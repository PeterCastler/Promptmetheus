# **Log (lack of) Progress**
If there isn't a `pain.md` file, create one.
For every failed attempt you must update the `pain.md` file with a short entry of what you tried and what (error) it yielded.
These entries should be dead simple. They don't even have to sound like full sentences. Do NOT write about future plans in this file, only what you have done and what that produced, and the current task if you have already queued the next attempt.
You may only declare success after a conclusive test of the implementation! If the test yields success, add another short entry of what succeeded. Below the entry about the success, explain why the solution worked.
This will allow us to see what turned out to be the real problem which we missed in the chain of previous attempts.
This will be one of the most valuable files in the project.
Seriously, these entries must be so simple, that they don't even have to look like a human-readable text file (but do use line breaks).
For example:
```painmd
[hh:mm:ss/d/m/y] - tried: x. --> error: y.
attempting z.
```
And when `z` fails, update `pain.md` like this:
```painmd
[hh:mm:ss/d/m/y] - tried: x. --> error: y.
[hh:mm:ss/d/m/y] - tried: z. --> error: a.
attempting b.
```
If `b` passes the test, update `pain.md` like this:
```painmd
[hh:mm:ss/d/m/y] - tried: x. --> error: y.
[hh:mm:ss/d/m/y] - tried: z. --> error: a.
[hh:mm:ss/d/m/y] - tried: b. --> SUCCESS: The solution was (...)
```
etc
