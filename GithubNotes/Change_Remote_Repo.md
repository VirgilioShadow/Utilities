# Git Commands for Changing Remote Repository URL

This document provides a series of git commands to change the remote repository URL and verify the changes.

## Step 1: Check Current Remote URL

To check the current remote URL, run the following command:

```sh
git remote -v
```

This command will display the current remote URLs for fetching and pushing.

## Step 2: Change the Remote URL

To set the remote URL to the correct repository, use the following command:

```sh
git remote set-url origin https://github.com/yourusername/data-aggregator.git
```

Replace yourusername and data-aggregator with the appropriate username and repository name.

## Step 3: Verify the Change

After changing the remote URL, verify the change by running:

```sh
git remote -v
```

This should now show the correct remote repository URL.

## Step 4: Push to the Correct Repository

Now you can push your changes to the correct repository:

```sh
git push origin main
```
