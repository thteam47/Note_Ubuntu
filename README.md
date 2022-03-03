# Note_Ubuntu
1. Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable) [duplicate]
- For above wait for the process to complete. If this does not happen run in terminal:\
  sudo killall apt apt-get
- If none of the above works, remove the lock files. Run in terminal: \
  sudo rm /var/lib/apt/lists/lock \
  sudo rm /var/cache/apt/archives/lock \
  sudo rm /var/lib/dpkg/lock* \
- then reconfigure the packages. Run in terminal:\
  sudo dpkg --configure -a
- and\
  sudo apt update
- That should do the job.
