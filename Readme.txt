#configuring Winrm service on Windows
#run ConfigureRemotingForAnsible.ps1 script on powershell(windows)as follow:

powershell.exe  -ExecutionPolicy Bypass -File ConfigureRemotingForAnsible.ps1 -CertValidityDays 3650 -Verbose
#then configure basic auth on windows as follows

winrm set winrm/config/service/auth @{Basic="true"}
winrm set winrm/config/service @{AllowUnencrypted="true"}


#below is a  reference for the controlling machine(Linux machine or Cloud forms)
#
http://nokitel.im/index.php/2016/11/09/how-to-manage-windows-server-2016-with-ansible/
..

in /etc/ansible/hosts

[windows]
<ip of windows machine>


[windows:vars]
ansible_user=administrator # A local user account on Windows environments 
ansible_password=<password> # The password for the Windows user
ansible_connection=winrm
ansible_winrm_server_cert_validation=ignore

