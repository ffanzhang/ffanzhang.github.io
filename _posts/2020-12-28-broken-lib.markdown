---
layout: post
title: "Lessons Learned Dealing with Unstable C/C++ Libraries with Cross-Platform Builds"
date: 2020-12-28 10:47:00 -0800
---

One of the unfortunate/forturnate thing is, sometimes we have no choice but to use an unstable library.
What's unfortunate about it is dealing with the pressure getting stuff to work while bugs just keep flooding in every day.
And what's forturnate about using such a library is that it really challenges us to get creative.
What is also fortunate about it is that this library is open source and we are
able to make improvements.

During the process of making this library work, I learned some lessons and re-discovered several techniques (probably known by some already).

### Hard coded timeouts raise red flags
In realistic network conditions, things usually arrive later than expected
than designed. Double checking and reason about whether those timeouts are
reasonable give the most bang for the buck. Actual field data gives valuable
feedback on whether some of those timeouts need adjustment.

### If there is a bug, think outside of the box: the build/hardware/os-config/environment could also be the cause
In a lot of scenarios, we automatically assume the bug is probably caused by the code and spending 99% looking cluelessly
using all the fancy tools going through code. However, keep in mind that there
is a lot of factors outside of code. There could be cases where an os setting will solve the problem.

### Fallback to a more common platform
If we are exhausted from debugging on a special platform, consider trying to reproduce
the bug on a common platform. If reproducible, we have a wider selection of tools to analyze and fix the bug. 
If not reproducible, the likelihood of an actual bug on the source code is very small, or this bug is platform specific.
This also relates to the last section. Not all bugs are caused by code.

### Log everything
This is self explanatory, add log entries everywhere that could lead up to the bug.

### Dealing with catastrophic crashes
If we were to perform some searches online, the standard approach is to
install some monitoring services such as supervisord, or to configure some
systemd service file. If you are in a scenario where configuring system files
is a big yikes, the following approach is probably a feasible self contained solution.

The high level idea is, spawn/fork a child process off of a parent process. If the
child process dies, respawn a new one. Before settling down to this forking
solution, I've attempted to spawn child threads, which made me realize and
learn that a crash in a thread will also crash the whole program. However, if a
forked process dies, the main program will just move on and create another one.

The long term goal is to find the causes of all of those crashes and fix them one by one, but if we end up with an
unstable library, this seems like a feasible short term solution. If we were to
find most of the crashes, this also seems like an ultimate failsafe guard. 

```
int main(int argc, char** argv)
{
    for (;;) {
        int pid = fork();
        if (pid == 0) {
            // this makes sure that the child process is killed when the parent process is killed
            prctl(PR_SET_PDEATHSIG, SIGKILL);
            prctl(PR_SET_NAME, "child_process_name");
            // do some blocking work
            do_meaningful_work(argc, argv);
            exit(0);
        } else {
            // wait till child process to die.
            while (wait(NULL) > 0);
        }
    }
    return 0;
}
```
