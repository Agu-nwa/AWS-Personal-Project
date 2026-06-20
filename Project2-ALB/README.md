# 💻 Project 2: Highly Available Nginx Application using AWS ALB

---

# 💾 EBS (Elastic Block Store) Setup, Format, Mount & Persistence

This section documents the full lifecycle of attaching, formatting, mounting, and persisting an AWS EBS volume on an EC2 Ubuntu instance.

---

## 🔌 1. Identify the attached EBS volume

### Command
```bash
lsblk

Result
nvme0n1 → root disk (OS)
nvme1n1 → new EBS volume (6G)


🧱 2. Format the EBS volume (ext4 filesystem)
Command
sudo mkfs -t ext4 /dev/nvme1n1

Result
Filesystem created successfully
UUID generated: ec1a8b0f-0576-4f01-9d39-4de66d16e213


📁 3. Create mount directory
Command
sudo mkdir /aws-data

Result
Directory /aws-data created successfully


4. Mount EBS volume to directory
Command
sudo mount /dev/nvme1n1 /aws-data

Result
Volume mounted successfully at /aws-data


5. Verify mounted filesystem
Command
df -h

Result
/dev/nvme1n1 → /aws-data (5.9G available, mounted)


6. Test write operation
Command
sudo touch /aws-data/test.txt
ls /aws-data

Result
lost+found
test.txt


7. Get UUID for persistence configuration
Command
sudo blkid

Result
/dev/nvme1n1 UUID="ec1a8b0f-0576-4f01-9d39-4de66d16e213"


8. Configure persistent mount (fstab)
Command
sudo nano /etc/fstab

Added line
UUID=ec1a8b0f-0576-4f01-9d39-4de66d16e213 /aws-data ext4 defaults,nofail 0 2


9. Apply and validate configuration
Command
sudo mount -a
df -h | grep aws-data

Result
/dev/nvme1n1 still mounted at /aws-data
Persistence confirmed


Outcome
EBS volume successfully attached
Filesystem formatted (ext4)
Mounted to EC2 instance
Persistent mount configured via fstab
Data survives reboot
Verified using real system commands
