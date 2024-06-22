#### Bash Scripts (`bashScripts.js`)

- **Backup a Directory**: This script creates a compressed archive of a specified directory and stores it with a timestamp.

```bash {.line-numbers}
#!/bin/bash

# Variables
BACKUP_DIR="/path/to/backup"
DEST_DIR="/path/to/destination"
TIMESTAMP=$(date +"%Y-%m-%d_%H-%M-%S")
ARCHIVE_NAME="backup_$TIMESTAMP.tar.gz"

# Create the backup
tar -czvf "$DEST_DIR/$ARCHIVE_NAME" "$BACKUP_DIR"

# Optional: Remove backups older than 7 days
find "$DEST_DIR" -type f -name "backup_*.tar.gz" -mtime +7 -exec rm {} \;

```

- **System Update and Upgrade**: This script updates and upgrades the system packages.

```bash {.line-numbers}
#!/bin/bash

# Update package list and upgrade packages
sudo apt update && sudo apt upgrade -y

# Optional: Clean up
sudo apt autoremove -y
sudo apt clean

```

- **Check Disk Usage and Send Email Alert**: This script checks disk usage and sends an email alert if usage exceeds a certain threshold.

```bash {.line-numbers}
#!/bin/bash

# Variables
THRESHOLD=80
EMAIL="your-email@example.com"
HOSTNAME=$(hostname)
SUBJECT="Disk Space Alert on $HOSTNAME"

# Check disk usage
USAGE=$(df -h / | grep / | awk '{ print $5 }' | sed 's/%//g')

if [ $USAGE -gt $THRESHOLD ]; then
  MAIL_BODY="Disk space on $HOSTNAME is critically low. Usage: $USAGE%."
  echo $MAIL_BODY | mail -s "$SUBJECT" $EMAIL
fi

```
