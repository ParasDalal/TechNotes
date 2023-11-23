- Install WSL
  - Start Windows Powershell in admin mode
  - wsl --install
- Find available Linux versions
  - wsl --list --online
- Install Ubuntu
  - wsl --install -d  Ubuntu-20.04
- Once the OS is installed, it will ask for new user/password
- Generate SSH key
  - ssh-keygen -t ed25519 -C "your_email@example.com"
- Install OpenSSH client
  - Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
- Transfer key to server (This needs to be done via Linux terminal on Windows)
  - ssh-copy-id -i ~/.ssh/example_key.pub example_user@192.0.2.123        
  - ssh-copy-id -i /mnt/d/softprojects/sshkeys/vultr.pub root@45.32.5.159