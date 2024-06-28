---
aliases:
  - fg
  - bg
---
#bash #shell 

[Baeldung guide](https://www.baeldung.com/linux/jobs-job-control-bash),[doc](https://www.gnu.org/software/bash/manual/html_node/Job-Control-Basics.html)
Read JOB CONTROL section in bash [[man]]

- see current jobs of the shell:  `jobs`
- stop the current job: `Ctrl`+`Z`
- after the job was stopped, rerun the job in the background: `bg %2`
- kill some jobs: `kill %1 %2 %3`
- foreground the last suspended process: `fg`.
- foreground a job: `fg %n` where `n` is the job number.

**Note:** if job runs in the background and we close the owner shell, the job might terminate anyway if ti tries to output to the shell as the shell doesn't exist anymore. To make sure the job keeps running in the background after the shell is closed we could *disown* the job from the shell: `disown %2`

asynchronous execution: `myCommand &`