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
