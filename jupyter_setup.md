# This is how i setup jupyter notebook using pace, WSL and windows setup

## Method 1:

1.To run a session, you can start a basic interactive session using the following command:
`qsub -I -l nodes=1:ppn=1,mem=8gb,walltime=10:00:00 -q iw-shared-6`
 
2.When you start your Jupyter Notebook session, you'll want to add the following option to the command: --ip=$HOSTNAME. This tells Jupyter Notebook that you will be connecting from a remote address on that compute node:
`jupyter notebook --no-browser --port=8001 --ip=$HOSTNAME`
 
3.To connect to the session from your laptop, then, we need to set up an ssh tunnel. This can be done by entering the following command in a new terminal window on your laptop:
`ssh -L <PORT>:<COMPUTENODE>:<PORT>-N <USERNAME>@login-s.pace.gatech.edu`

In the above command, <PORT> is the port you specified for your Jupyter Notebook and <COMPUTENODE> is the computer on which the Notebook is actually running (the one you connected to for your interactive job - it usually starts with "iw-").

This full description and some relevant screenshots can be found at https://github.gatech.edu/pages/PACE/documentation/interactiveJobs/jupyterInt/.
