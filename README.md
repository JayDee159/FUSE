# FUSE-Based Custom File System  
A simple user-space file system implemented using **FUSE3** in C.

This project demonstrates how to create a custom filesystem using the FUSE framework.  
It supports basic operations:

- getattr
- readdir
- open
- read
- write
- create
- mkdir
- unlink
- rmdir

All operations redirect to a backend storage directory on the host system.

---


---

## 🚀 Features

✔ Uses FUSE3  
✔ Supports basic filesystem operations  
✔ Transparent backend storage at `/home/vboxuser/storage`  
✔ Automatically sets permissions to `0777`  
✔ Fully mountable and usable as a Linux filesystem  
✔ Simple and easy to extend  

---

## 🛠 Requirements

Install FUSE3:

```bash
sudo apt update
sudo apt install fuse3 libfuse3-dev build-essential

🔧 Build Instructions

Compile:

gcc myfs.c -o myfs `pkg-config fuse3 --cflags --libs`

▶️ Run the File System

Create mount point:

mkdir /mnt/myfs


Mount:

./myfs /mnt/myfs


Try some operations:

echo "Hello!" > /mnt/myfs/a.txt
cat /mnt/myfs/a.txt
ls -l /mnt/myfs
mkdir /mnt/myfs/newdir

⏹ Unmount
fusermount3 -u /mnt/myfs

🔍 How It Works

Requests such as:

ls /mnt/myfs
echo hi > /mnt/myfs/file
cat /mnt/myfs/file


are mapped internally to:

/home/vboxuser/storage/


Each FUSE callback corresponds to real operations:

FUSE Function	Linux Function
getattr	lstat
readdir	opendir
open	open
read	pread
write	pwrite
mkdir	mkdir
unlink	unlink
🧰 Future Improvements

Persistent metadata

Virtual memory filesystem (RAM FS)

Operation logs

Access control & permissions

Caching

👨‍💻 Authors

Projit Maity (24BRS1218)

Jyotiraditya Das (24BRS1260)
