## Cheatsheets

Cheatsheets for CLI commands I use.


### SGE (Sun Grid Engine)

Note: The brackets are not literal, **but** the curly brackets are.

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
  - `qstat -u [user_name]`: Display information on all queues for the specified user
  - `qstat -q [queue_name]`: Display information on the specified queue
  - The options above can be combined, e.g.:
    - `qstat -f -u [user_name] -q [queue_name]`
