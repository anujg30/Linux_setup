#General Information

`pace-whoami`: returns username, UserID, groups that you are a part of, and queues you have access to.

`pace-check-queue <queue name>`: gives info on resources available for queue, node names, status of queue

#Modules

`module avail <optional module name>`: lists modules (software) available on pace, can provide a module name to search for specific software

`module load <module name>`: loads module into environment

`module purge`: gets rid of any modules loaded

#Job Submission

`qsub <script.pbs>`: submits PBS script (script that determines resources needed and contiains job to be run) to scheduler.

#Job Control

`showq`: shows all jobs and status of jobs in queue.

`qstat <jobid>`: status of job in queue

`qstat | grep someuser3`: lists your jobs and status

`qstat -u <someuser3> -n`: lists your jobs and state

`checkjob <jobid>`: get a detailed status on your jobid.

`showstart <jobid>`: can run shortly after job is submitted. Estimates time until job will be run (time job will be in queue).

`qdel <jobid>` or `canceljob <jobid>`: deletes job in queue

`qselect -u gtusername3|xargs qdel` : deletes all jobs you have in queue. Replace gtusername3 with your gt username

#Check Storage

`pace-quota`: gives you a summary of how much storage you have used and how much you have left

#Troubleshooting

`pace-why-inqueue <jobid>`: diagnoses why a job is stuck in the queue (not running)
