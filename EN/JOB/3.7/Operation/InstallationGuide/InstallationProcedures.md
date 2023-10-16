# Installation steps

## NFS storage setup

See [Appendix NFS Solution](../Appendix/NFSSolution.md) If there is already a corresponding storage solution, ignore this step.

## Working directory initialization

### Create public directory

Create a public directory on the JOB server.
```bash
${BK_HOME}/logs/job is responsible for writing program running logs to the job platform, which can be cleaned up
${BK_HOME}/job The main directory of the job platform is ${JOB_HOME}

${BK_HOME}/run_data/job/data1 master: storage and mount nfs location of job logs and files (data is important and cannot be lost)
${BK_HOME}/run_data /job/data2 Backup machine: storage and mount nfs location of job logs and files
(If there is no NFS backup machine, there is no need to create this directory)
```

### Mount nfs

```bash
mount storage machine IP1:/data/bkee/job/data ${BK_HOME}/run_data/job/data1
mount storage machine IP2:/data/bkee/job/data ${BK_HOME}/run_data/job/data2
mount storage machine IP1:/data/bkee/job/log ${BK_HOME}/run_data/job/log1
mount storage machine IP2:/data/bkee/job/log ${BK_HOME}/run_data/job/log2
```

## Unzip job_ee-x.x.x.tgz

Go to the `${JOB_HOME}` directory and unzip the installation package.

## JDK/JRE installation

Please use JDK1.8 version to install

## Certificate installation

See [Appendix Certificates Installation](../Appendix/CertificatesInstallation.md) Generally, this step has been initialized by the BlueKing installation automation script.

## MQ Deployment

### RabbitMQ

The deployment method is a cluster, and the construction method is provided by the platform (omitted). The key point here is to set the mirroring mode of the message queue of the job platform for RabbitMQ to ensure high availability. After all cluster nodes are built and started, the steps are as follows:

Enter the RabbitMQ sbin directory of the RabbitMQ master node and execute the following command:

```bash
./rabbitmqctl set_policy bk_job_mirror "^bk.job" '{"ha-mode":"all","ha-sync-mode":"automatic"}'
```

## Modify the configuration file

## Start the Job server

### Modify memory parameters


By setting the Linux system environment variable JOB_JAVA_OPTS as follows:

Set the boot memory to 8g, in GB. If the machine configuration does not work, set the unit as 512m in MB, and configure the two values to be the same to ensure that size inversion errors and one-time memory application performance are avoided, and then start again.

```bash
export JOB_JAVA_OPTS="–Xms8g –Xmx8g”
```

The memory configuration, the number of concurrent tasks, the number of IPs contained in each task, and the amount of print logs for each IP are combined to obtain the following recommended values. Of course, various combinations are flexible, and there may be unexpected situations

The calculation details are as follows:

Each log line can be up to 256 bytes, output 2000 lines instantly, 2000*256=51200 =512KB memory.
100 IPs are 100*512KB=50MB memory.
10 concurrent tasks are 50MB*10 = 500MB of memory. In addition to system switching and other module overheads in the job, 1.5G is required. A total of 2G memory.

Of course, generally very few jobs will output 2000 lines of logs in an instant, unless it is an operation such as cat printing a certain file. This kind of behavior is not recommended and will increase the load on the machine. Therefore, under normal circumstances, the memory demand of the operating system is much lower than that described in the table. The recommended initial memory is 4GB, and the maximum recommended memory for 64G machines is 32G. Generally, the maximum is half of the real memory of the machine, and it is not recommended to increase it later.

Finally, the following table is obtained:

| Number of tasks | Number of IPs | Number of log lines | Memory |
|--|--|--|--|
| 10 | 100 | 2000 | 2G |
| 100 | 100 | 2000 | 8G |
| 200 | 100 | 2000 | 16G |
| 500 | 100 | 2000 | 32G |

### Modify port

The default port is 8080, and the API port is 8443. Please modify it if it is occupied by other processes, but you should also change the corresponding Nginx and ESB interface configuration, otherwise it will be inaccessible. The modification method is in job.conf
```bash
# Job's process web port, not Nginx port
job.listen.port=8080
# Job's process API port, not Nginx port
job.listen_ssl.port=8443
```

### Run the server