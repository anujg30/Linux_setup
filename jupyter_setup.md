# This is how i setup jupyter notebook using pace, WSL and windows setup

## Method 1:

1. To run a session, you can start a basic interactive session using the following command (refer to pace_guide.md):
`qsub -I -l nodes=1:ppn=1,mem=8gb,walltime=10:00:00 -q iw-shared-6`
 
2. When you start your Jupyter Notebook session, you'll want to add the following option to the command: --ip=$HOSTNAME. This tells Jupyter Notebook that you will be connecting from a remote address on that compute node:
`jupyter notebook --no-browser --port=8001 --ip=$HOSTNAME`
 
3. To connect to the session from your laptop, then, we need to set up an ssh tunnel. This can be done by entering the following command in a new terminal window on your laptop:
`ssh -L <PORT>:<COMPUTENODE>:<PORT>-N <USERNAME>@login-s.pace.gatech.edu`

In the above command, <PORT> is the port you specified for your Jupyter Notebook and <COMPUTENODE> is the computer on which the Notebook is actually running (the one you connected to for your interactive job - it usually starts with "iw-").

This full description and some relevant screenshots can be found at https://github.gatech.edu/pages/PACE/documentation/interactiveJobs/jupyterInt/.

## Method 2: (not recommended but works!!!)

An easy path forward to run an interactive Jupyter Notebook session is probably to just run a fell desktop VNC session. To do this, you'll need to make sure you have an appropriate VNC client (like Turbo VNC Viewer) installed on your laptop, and then proceed as follows:
 
1.	SSH into the login headnode from which you'll be submitting your interactive job.
`ssh <USERNAME>@login-s.pace.gatech.edu`

2.	Load the qsubvnc module, set your VNC password, and start a Turbo VNC server session:
`module load qsubvnc/1.1
vncpasswd
qsubturbovncserver -t 10:00:00 -n 1 -p 8 -m 8gb -q iw-shared-6 -d ~/tmp -l qsubvnclog`

3.	Verify that your job is running by using qstat. Once running, run the following command to look for the file that indicates which compute node and display are allocated for your job:
`ls ~/.vnc | grep <JOBID>`

Where <JOBID> is the job you are currently running. The file name will be of the form <JOBID>.<SCHEDULER><COMPUTE-NODE>:<DISPLAY>. So for example, my interactive session generated the following file name:
`20942.dedicated7-sched.pace.gatech.edu.rich133-h35-22.pace.gatech.edu:3`

According to this, the allocated compute node is `rich133-h35-22.pace.gatech.edu` and the display is 3.

4.	At this point we will want to set up a tunnel for our VNC viewer to access our interactive job. The port we want to be forwarding is simply 5900 + display (so for the above example, it would be port 5903). Exit your ssh session, and on your Windows machine, you can run the following command:
`ssh -L <PORT>:<COMPUTE-NODE>:<PORT> -N <USERNAME>@login-s.pace.gatech.edu`

At this point, the terminal will appear to hang, but this is expected - it's just handling our port forwarding.

5.	Open your VNC client, and for the address, simply enter
`localhost:<DISPLAY>`
Note that display doesn't include the 5900. At this point you'll be prompted to enter your VNC password, and you'll have remote desktop access.

6.	Open a terminal, load anaconda, and then start your Jupyter Notebook
`module load anaconda3/latest
jupyter notebook`


