#### PowerShellScripts

- **PowerShell Script to Backup a Directory**: This script creates a compressed archive of a specified directory and stores it with a timestamp.

```powershell {.line-numbers}
# Variables
$backupDir = "C:\path\to\backup"
$destDir = "C:\path\to\destination"
$timestamp = Get-Date -Format "yyyy-MM-dd_HH-mm-ss"
$archiveName = "backup_$timestamp.zip"
$archivePath = Join-Path $destDir $archiveName

# Create the backup
Compress-Archive -Path $backupDir -DestinationPath $archivePath

# Optional: Remove backups older than 7 days
$daysToKeep = 7
$cutoffDate = (Get-Date).AddDays(-$daysToKeep)
Get-ChildItem -Path $destDir -Filter "backup_*.zip" | Where-Object { $_.CreationTime -lt $cutoffDate } | Remove-Item

```

- **PowerShell Script to Update System and Applications**: This script uses choco (Chocolatey) to update the system and applications.

```powershell {.line-numbers}
# Update Chocolatey
choco upgrade chocolatey

# Update all installed packages
choco upgrade all -y

```

- **PowerShell Script to Monitor Disk Usage and Send Email Alert**: This script checks disk usage and sends an email alert if usage exceeds a certain threshold.

```powershell {.line-numbers}
# Variables
$threshold = 80
$email = "your-email@example.com"
$hostname = $env:COMPUTERNAME
$subject = "Disk Space Alert on $hostname"

# Check disk usage
$drive = Get-PSDrive -Name C
$usage = [math]::Round((($drive.Used / $drive.Size) * 100), 2)

if ($usage -gt $threshold) {
  $mailBody = "Disk space on $hostname is critically low. Usage: $usage%."
  $smtpServer = "smtp.example.com"
  $smtpFrom = "alert@example.com"
  $smtpTo = $email
  $message = New-Object System.Net.Mail.MailMessage $smtpFrom, $smtpTo, $subject, $mailBody
  $smtp = New-Object Net.Mail.SmtpClient($smtpServer)
  $smtp.Send($message)
}


```
