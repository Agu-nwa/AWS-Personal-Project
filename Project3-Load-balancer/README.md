## 🔌 Step 1: Verify EC2 Block Storage

### Command
```bash
lsblk

Output section
```markdown
### Output
```text
NAME         MAJ:MIN RM  SIZE RO TYPE MOUNTPOINTS
loop0          7:0    0 28.2M  1 loop /snap/amazon-ssm-agent/13009
loop1          7:1    0 49.3M  1 loop /snap/snapd/26865
loop2          7:2    0   74M  1 loop /snap/core22/2411
nvme0n1      259:0    0    8G  0 disk 
├─nvme0n1p1  259:1    0  6.9G  0 part /
├─nvme0n1p13 259:2    0 1023M  0 part /boot
├─nvme0n1p14 259:3    0    4M  0 part 
└─nvme0n1p15 259:4    0  106M  0 part /boot/efi
nvme1n1      259:5    0    6G  0 disk /aws-data


## ⚙️ Step 2: Verify Nginx Service Status

### Command
```bash
sudo systemctl status nginx

● nginx.service - A high performance web server and a reverse proxy server
     Loaded: loaded (/usr/lib/systemd/system/nginx.service; enabled; preset: enabled)
     Active: active (running) since Sat 2026-06-20 11:09:36 UTC; 3h 24min ago
 Invocation: b25b8cb3d7c14148b9f45f327301024b
       Docs: man:nginx(8)
   Main PID: 7839 (nginx)
      Tasks: 3 (limit: 627)
     Memory: 3.2M (peak: 7.3M)
        CPU: 271ms
     CGroup: /system.slice/nginx.service
             ├─7839 "nginx: master process /usr/sbin/nginx -g daemon on; master_process on;"
             ├─7842 "nginx: worker process"
             └─7843 "nginx: worker process"

Jun 20 11:09:36 ip-172-31-30-140 systemd[1]: Started nginx.service - A high performance web server and a reverse proxy server.
