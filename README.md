### CentOS7 Custom Mirror

#### Server
```
mkdir /var/repo
cd /var/repo
yum install httpd
yum install createrepo
yum install yum-plugin-donwloadonly
yum install --downloadonly --downloaddir=/var/repo nmap
createrepo /var/repo/
ln -s /var/repo /var/www/html/repo 
```

#### Client
```
vi /etc/yum.repos.d/icesi.repo
--
[repo_server-repo]
name=My RPM System Package Repo
baseurl=http://[repo_server-ip]/repo
enabled=1
gpgcheck=0
--
yum repolist
yum —disablerepo="*" —enablerepo="icesi" list available
yum update
yum install nmap
```

### References
* https://g4greetz.wordpress.com/2016/10/12/how-to-run-a-yum-update-from-a-specific-repository/
* https://www.ostechnix.com/download-rpm-package-dependencies-centos/
* https://www.digitalocean.com/community/tutorials/how-to-set-up-and-use-yum-repositories-on-a-centos-6-vps


