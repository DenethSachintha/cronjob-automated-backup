# Backup Script Project

## Project Overview

This project provides an automated backup solution using a Bash script (`backup.sh`). The script archives and compresses files from a source directory and moves the backup file to a specified destination directory. Additionally, a cron job can be set up to automate backups at scheduled intervals (Daily at  midnight).

## **What Does `backup.sh` Do?**

- Takes two arguments: the source directory (to back up) and the destination directory (to store the backup).
- Creates a compressed `.tar.gz` archive of the source directory.
- Moves the backup file to the destination directory.
- Can be scheduled to run automatically using a cron job.

---

## **Installation Guide**

### **Step 1: Clone the Repository**

Run the following command to clone the repository:

```bash
 git clone https://github.com/DenethSachintha/cronjob-automated-backup.git
 cd cronjob-automated-backup
```

### **Step 2: Make the Script Executable**

By default, scripts are not executable. To allow execution, run:

```bash
chmod +x backup.sh
```

### **Step 3: Verify Execution Permissions**

You can check if `backup.sh` is executable using:

```bash
ls -l backup.sh
```

Expected output:

```
-rwxr--r-- 1 user user 1221 Mar 14 11:58 backup.sh
```

`rwx` means the owner has **read, write, and execute** permissions.

---

## **Testing `backup.sh` Manually**

### **Step 1: Create a Test File**

```bash
touch source_directory/any.txt
```

This creates a dummy file (`any.txt`) inside the `source_directory` to test the backup process.

### **Step 2: Run the Backup Script**

Execute the script by specifying the source and destination directories:

```bash
./backup.sh source_directory destination_directory
```

Expected output:

```
targetDirectory: source_directory
destinationDirectory: destination_directory
Backup created: backup-YYYY-MM-DD_HH-MM-SS.tar.gz
Backup moved to: destination_directory/backup-YYYY-MM-DD_HH-MM-SS.tar.gz
```

---

## **Automating Backups Using a Cron Job**

### **Step 1: Open Crontab for Editing**

```bash
crontab -e
```

### **Step 2: Add a Scheduled Backup Job**

To schedule a backup to run **daily at midnight**, add the following line:

```
0 0 * * * /usr/local/bin/backup.sh /home/project/source /home/project/dest
```

**Explanation:**

| Field        | Value | Meaning               |
| ------------ | ----- | --------------------- |
| Minute       | `0`   | 0th minute            |
| Hour         | `0`   | 0th hour (midnight)   |
| Day of Month | `*`   | Every day             |
| Month        | `*`   | Every month           |
| Day of Week  | `*`   | Every day of the week |

This ensures that `backup.sh` runs at **midnight every day**.

---

## **Useful Commands**

### **Create a Directory**
```bash
mkdir directory_name
```
Creates a new directory with the specified name.

### **Start the Cron Service**
```bash
sudo service cron start
```
Starts the cron job scheduler, ensuring that scheduled tasks run as expected.

### **Stop the Cron Service**
```bash
sudo service cron stop
```
Stops the cron job scheduler, preventing scheduled tasks from executing.

### **Check the Status of the Cron Service**
```bash
sudo service cron status
```
Displays whether the cron service is running or stopped.

---

## **Conclusion**

With this setup, you can automate your backups using `backup.sh` and ensure that your data is archived regularly. You can modify the cron job timing as per your needs and integrate this script into larger automation workflows.

