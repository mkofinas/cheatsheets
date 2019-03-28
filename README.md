## Cheatsheets

Cheatsheets for CLI commands I use.

__NOTE__: The brackets are not literal, **but** the curly brackets are.

### Remote Connection (ssh)

- `ssh [user]@[host] ls -lNHha --color DIR`: Remote ls
- `ssh [user]@[host] "cat [file]" | diff - [local_file]`: Remote diff
- `ssh -Y -l [user] [host] -p [PORT]`: Port Forwarding (X11)
- `scp -pr [user]@[host]:[REMOTE_PATH] [LOCAL_PATH]`: Download file(s) from server
- `scp -pr [LOCAL_PATH] [user]@[host]:[REMOTE_PATH]`: Upload file(s) to server
- `Shift`+`Middle Click` or `Shift`+`Insert`: Paste from clipboard to server

__NOTE__: `[user]@[host]` can be simplified by using aliased in `$HOME/.ssh/config` file

### SGE (Sun Grid Engine)


- Submit Jobs:
  - `qsub [script]`: Submit a job that will execute the specified script
  - `qsub [script] [arguments]`: Submit a job that will execute the specified script with the specified arguments
  - `qsub [script] [arguments]`: Submit a job that will execute the specified script with the specified arguments
  - `qsub -N [job_name] [script]`: Submit a job that will execute the specified script with the specified job name
  - `qsub -hold_jid [dependency_job] [script]`: Submit a job that will execute the specified script but depends on the execution of another job
- Delete jobs:
  - `qdel [job_id]`: Delete the job with the specified job_id
  - `qdel {[job_id_i]..[job_id_j]}`: Delete jobs in the specified range (including both ends)
- View job statuses:
  - `qstat -f`: Display "full" information on all queues for all users
  - `qstat -j [job_list]`: Display information for the specified jobs (comma separated)
  - `qstat -u [user_name]`: Display information on all queues for the specified user
  - `qstat -q [queue_name]`: Display information on the specified queue
  - The options above can be combined, e.g.:
    - `qstat -f -u [user_name] -q [queue_name]`

### SLURM

- `srun -u --pty --gres=gpu:1 bash -i`: Allocate 1 GPU (`--gres=gpu:1`) and run bash interactively (`bash -i`)
- `srun -u --pty --gres=gpu:1 -t 2-0 bash -i`: Allocate 1 GPU and run bash interactively for 2 days (`-t 2-0`)
- `srun -u --pty --gres=gpu:1 -t 2:30:00 bash -i`: Allocate 1 GPU and run bash interactively for 2 and a half hours (`-t 2:30:00`)
- `srun -u --pty --gres=gpu:1 -C [constraint] bash -i`: Allocate 1 GPU and run bash interactively when the constraint (e.g. TitanX) is met
- `srun -u --pty --gres=gpu:1 [script]`: Allocate 1 GPU (`--gres=gpu:1`) and run the specified script

### Tmux

- `Prefix`+`Ctrl-s`: Save tmux session that persists through reboots (requires [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect))
- `Prefix`+`Ctrl-r`: Restore tmux session, even after reboot (requires [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect))
- `Prefix`+`?`: Help
- `Prefix`+`/`: Search
