# NFS scheme

## Plan selection

NFS is responsible for storing job files uploaded by users on the job platform (which cannot be lost) and job execution logs (which can be cleaned up regularly), so the solution prefers professional and reliable storage provided by **enterprise users** to ensure that data is not lost, and high available.

### Solution 1: Shared Storage

The enterprise provides two storage servers** sharing one storage**, and the storage hard disk adopts **RAID** to ensure redundancy.
Mount the NFS from these two storage servers on multiple operating platform servers, which can ensure that after one mounted NFS physical machine hangs or the NFS service is abnormal, the operating platform can automatically and quickly switch to another NFS mount Point, because the data all share the same storage,** so the data redundancy mechanism is guaranteed by the external storage, reducing the repeated consumption of repeated writing of files and logs on the operating platform. **

advantage:

The data is stored in the same block, and there is no data inconsistency. In fact, the two storage servers **are primary storage**. This approach is recommended.

### Solution 2: rsync synchronization

The enterprise provides two storage servers, but each has independent storage, and the storage hard disk adopts RAID to ensure redundancy. The NFS mounted by the two storage servers is mounted on multiple operating platform servers, and the data between the two storage servers is synchronized with each other through rsync.

shortcoming:

**Delay may cause data loss**, this solution is for if the main storage server hangs up (possibility 2 points), because of the delay relationship of **rsyns synchronization**, the files will not be synchronized to the backup storage server ( Influence degree 3 points).

## Implementation

### NFS source initialization

*Only need to set the NFS source on the two storage servers, and the settings are exactly the same. *

Create NFS source directory `/data/bkee/job/data` on **two storage machines**

And modify the directory permissions, otherwise the business machine can only read but not write to the file

`/data/bkee/job/data/localupload` **is the storage directory for files uploaded by user jobs**

`/data/bkee/job/data/logs` **is the storage directory for user job execution log files**

```bash
mkdir -p /data/bkee/job/data/localupload
mkdir -p /data/bkee/job/data/logs

chmod 777 /data/bkee/job/data/
chmod 777 /data/bkee/job/data/localupload/
chmod 777 /data/bkee/job/data/logs/
```

Add IP permissions to all operating platform servers to be mounted on NFS. Please refer to the NFS or SAN provided by the enterprise to determine the actual situation.

`vi /etc/exports`
Content: `/data/enterprise/job` **job server IP1**(rw) **job server IP2**(rw)

**Start service:**
```bash
     service rpcbind start
     service nfs start
```
If not installed, please `yum install rpcbind –y && yum install nfs-utils`
Do the same on another storage server.

If option 1 is adopted, rsync does not need to be set

### Solution 2: rsync file synchronization

This step is used for enterprises without professional storage** (shared storage)**, and we need to use rsync to synchronize the data in the two storage servers.

Set up rsync on two **storage servers** so that the files are in sync with each other, the 2 machines are slightly different. see path
```bash
vi /etc/rsyncd.conf

  gid = users
  # read only = true
  use chroot = true
  transfer logging = true
  log format = %h %o %f %l %b
  log file = /var/log/rsyncd.log
  hosts allow = 10.0.0.1
  slp refresh = 300

  [JOB_DATA_SYNC]
      path = /data/enterprise/job/data
      comment = JOB DATA NEED TO SYNC

  load rsync service
      rsync --daemon --config=/etc/rsyncd.conf
  Add a scheduled task
      crontab -e
  The content is as follows:

  # Backup JOB file
  */2 * * * * /usr/bin/rsync -avz --progress --bwlimit=2000 root\@10.0.0.1::**JOB_DATA_SYNC**
  /data/enterprise/job/data

  In this way, the directory /data/enterprise/job/data of the two servers is realized, and the staggered files are automatically backed up every 2 minutes.

  Add autostart
     echo "rsync --daemon --config=/etc/rsyncd.conf" \>\> /etc/rc.d/rc.local
```