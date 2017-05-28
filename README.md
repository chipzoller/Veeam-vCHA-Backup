# Veeam-vCHA-Backup
Pre- and post-backup scripts for Veeam designed to find and protect only the active node in a vCenter High Availability configuration.
######
######
This is a set of pre- and post-backup Powershell scripts that get called on a job that backs up the vCenter Server Appliance 6.5 (vCSA) when it is in a vCenter High Availability (vCHA) configuration. VMware supports VADP-based backups of only the active node in a vCHA configuration. The script uses the vCenter API to detect which node has the active role, then excludes from the job the node with the passive role. At the conclusion of the job, the script removes this exclusion essentially "resetting" the job until its next run when it reruns the process. By using these scripts, one can ensure only the correct node is backed up each time, which has the added benefit of reducing the amount of backup storage data required to protect a vCSA and reducing backup times.
