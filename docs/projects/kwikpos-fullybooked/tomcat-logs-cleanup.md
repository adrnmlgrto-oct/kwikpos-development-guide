# Tomcat Logs Cleanup

This guide explains how to set up an automated cleanup script for Tomcat logs and temporary files on POS machines to prevent storage issues.

<iframe src="https://drive.google.com/file/d/1BuWln4tSEKyafV2eQa3VAJjw_w98Yx7L/preview" width="640" height="480" allow="autoplay; fullscreen" frameborder="0"></iframe>

---

## Download Script Files

You can find the script files here:

<a href="https://drive.google.com/file/d/1pXtpsEwMumMsF1r8WNrNbUWHDGxba1Xk/view?usp=drive_link" target="_blank">View Script Files →</a>

!!! info "Important:"
    Make sure to follow the instructions listed in the `INSTRUCTIONS.txt` file included in the download.

---

## Setup Steps

Follow these steps to configure the automated cleanup script:

### 1. Configure the PowerShell Script

Edit the `script.ps1` file and configure the following settings:

- **Tomcat folder path**: Set the location of your Tomcat installation
- **Retention period**: Configure how many days of logs to keep
- **Other configuration variables**: Adjust as needed for your environment

### 2. Create a Shortcut

Create a shortcut for the `cleanup.bat` file:

1. Right-click on `cleanup.bat`
2. Select "Create shortcut"
3. The shortcut will be used in the next step

### 3. Open the Startup Folder

1. Press ++win+r++ to open the Run dialog
2. Type `shell:startup` and press ++enter++
3. The Windows Startup folder will open

### 4. Add to Startup

Move or copy the `cleanup.bat` shortcut to the Startup folder that opened in the previous step.

---

## Benefits

Setting up this automated cleanup provides the following advantages:

- **Automatic execution**: The script runs automatically every time the machine starts
- **Automated maintenance**: Removes Tomcat log and temporary files without manual intervention
- **Storage management**: Frees up disk space daily, preventing storage-related issues on POS machines
- **Improved performance**: Helps maintain system performance by preventing log buildup

---

## Configuration Options

### Testing Mode

!!! tip "Test Before Deploy:"
    Set `$WhatIf = $true` in the `script.ps1` file to test the script without actually deleting files. This allows you to preview what would be deleted.

```powershell
$WhatIf = $true  # Set to $false for actual deletion
```

### Retention Period

Adjust the retention period to control how long files are kept before deletion:

```powershell
$RetentionDays = 5  # Keep files newer than 5 days
```

!!! warning "Retention Period:"
    The default retention period is set to **5 days** (recommended) in order to maintain at least 5 days worth of logs to investigate in the event that an error occurs. Files older than this will be deleted. Adjust the `$RetentionDays` variable based on your requirements:

    - Lower values (e.g., 2-3 days) = More aggressive cleanup, less storage used, but fewer logs available for troubleshooting
    - Higher values (e.g., 7-14 days) = More logs retained for troubleshooting, but uses more storage space

---

## Troubleshooting

If the script doesn't run as expected:

1. **Check execution policy**: Ensure PowerShell scripts are allowed to run on the machine
2. **Verify paths**: Confirm that the Tomcat folder path in `script.ps1` is correct
3. **Test manually**: Run `cleanup.bat` manually to check for errors
4. **Review logs**: Check if any error messages appear when the script runs
5. **Shortcut location**: Verify the shortcut is in the correct Startup folder
