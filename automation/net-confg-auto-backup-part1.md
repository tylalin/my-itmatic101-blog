---
cover: https://i.imgur.com/C8YTDtE.png
coverY: 0
---

# FTP/TFTP server ပေါ်မှာ network config တွေကို auto backup လုပ်ပုံ – အပိုင်း (၁)

ဒီတခါလည်း အလုပ်နဲ့ပတ်သတ်ပြီးတော့ စဖြစ်တဲ့ project တစ်ခုအကြောင်းကို တင်ပြချင်လို့ ဒီ post ကိုရေးဖြစ်တာပါ။ အရင် post တွေမှာရေးသလိုပဲ စာရေးသူ အလုပ်နဲ့ပတ်သတ်ပြီးတော့ ဆိုင်ရာဆိုင်ရာ workflow တော်တော်များများကို စိတ်တိုင်းမကျပါဘူး။ task တော်တော်များများကို manual လိုက်လုပ်နေရလို့ အချို့ အပိုင်းတွေမှာ စာရေးသူ တော်တော်လေးကို စိတ်ညစ်ရပါတယ်။ manual လုပ်ပြီးဆိုကတည်းက productivity လည်းကျသွားပြီးတော့ ကိုယ်လုပ်ရမယ့် အရေးကြီးတဲ့ project တွေပေါ်မှာ အာရုံမစိုက်နိုင်တော့ပါဘူး။ အဲ့လိုနဲ့ integration နဲ့ optimization အတွက် လိုအပ်တဲ့ လုပ်ငန်းဆောင်တာ တွေကို မလုပ်နိုင်တဲ့အတွက် customer base များလာတာနဲ့အမျှ အလုပ်ပို ရှုပ်လာရပြီးတော့ အလုပ်လည်း အချိန်တိုအတွင်းမပြီးနိုင်တော့ပါဘူး။ အချို့ SMB (small and medium-sized business) တွေမှာ အဲ့လိုမျိုး manual process ကိုပဲအသုံးပြုပြီးတော့ အလုပ်ဖြစ်အောင်လို့ ဆက်သွားကြပါတယ်။ အချို့ဆိုရင် automatic workflow အတွက် research နဲ့ staging လုပ်တာကို လုံးဝအားမပေးပါဘူး။ အလုပ်ချိန်အတွင်းမှာ အချိန်ကုန်တယ်လို့ ယူဆတဲ့အတွက် မှားယွင်းတဲ့ work culture တွေကို adopt လုပ်ပါတယ်။ စာရေးသူအမြင်တော့ အဲ့ဒီလို business မျိုးဟာ creativity နဲ့ innovation ကို အားမပေးတဲ့အတွက် SMB အနေနဲ့ပဲ အချိန်တော်တော်ကြာကြာ ဆက်သွားရပါတယ်။ ဘယ်လိုပဲဖြစ်ဖြစ် စာရေးသူ တကိုယ်ရေအမြင်ကတော့ လက်ရှိ work culture ကောင်းသည်ဖြစ်စေ၊ မကောင်းသည်ဖြစ်စေ၊ ကိုယ်က management နဲ့ အဆင်ပြေသည်ဖြစ်စေ၊ အဆင်မပြေသည်ဖြစ်စေ ကိုယ်လုပ်တဲ့ အလုပ်ကို အလေးပေး တန်ဖိုးထားနိုင်ခြင်းဟာ ကိုယ်ဘယ်သွားသွား ကိုယ့်နောက်ပါလာမယ့်၊ ကိုယ်သယ်သွားလို့ရမယ့် အဖိုးတန် အရည်အချင်းတစ်ခုဖြစ်တယ်လို့ မြင်ပါတယ်။ ဆိုလိုချင်တာကတော့ ကိုယ်လုပ်လို့ရသလောက်တော့ ဆက်လုပ်နေရပါ့မယ်။ ကိုယ်လုပ်တဲ့ အလုပ်ပေါ်မှာ စေတနာထားတတ်ရပါမယ်။ အဲ့ဒီအတွက်လည်း ကိုယ့်မှာ အကျိုးမယုတ်ပါဘူး။ စိတ်ထားတာမှန်ရင် နောင်သံတရာ ထိအောင်ပါနိုင်ပါတယ်။ ကဲ… တွေးမိတဲ့ work culture အကြောင်းလေးပြောရင်းနဲ့ တရားခွေလည်း ဖြစ်သွားတော့မယ်။ FTP/TFTP အကြောင်းလေး ဆက်သွား လိုက်ရအောင်…

စစချင်းတုန်းက အလုပ်မှာ manage လုပ်ရတဲ့ network ထဲက router နဲ့ switch တွေရဲ့ config ကို backup လုပ်ချင်ရင် တခုချင်းစီ ssh login လုပ်ပြီးတော့ copy ရပါတယ်။ network မှာ device များလာတာနဲ့ အမျှ manual process ဖြစ်တဲ့ copy သွားသွားလုပ်ရတာ သိပ်ပြီးတော့ အလုပ်မဖြစ်တော့ပါဘူး။ အချိန်ကုန်တယ်၊ လူလည်းပင်ပန်းပါတယ်။ အဲ့ဒီတော့ script တွေကို အသုံးပြုပြီးတော့ automate လုပ်ဖို့ စာရေးသူ စဉ်းစားပါတော့တယ်။ ပထမတော့ TCL/Expect ကိုအသုံးပြုပြီးတော့ scripted automation လုပ်မယ်ဆိုပြီးတော့ အတွေးလေး ရပါတယ်။ ပြဿနာက အလုပ်မှာ က multi-vendors router နဲ့ switch တွေအသုံးပြုတဲ့အတွက် TCL/Expect နဲ့ ဆို Cisco မဟုတ်တဲ့ device တွေမှာ အခက်အခဲ အချို့ရှိနေတာကို သွားပြီးတွေ့ရပါတယ်။ အဲ့ဒီတော့ vendor-agnostic ဖြစ်မယ့် neutral backup process ကို တစ်ခုချင်းစီလိုက်ပြီးတော့ research လုပ်ရပါတော့တယ်။ အချိန်တော့ နည်းနည်းကုန်ပါတယ်၊ သို့သော် အလုပ်ဖြစ်မယ်ဆိုရင် အစပိုင်းတော့နည်းနည်း အလုပ်ရှုပ်မယ်ဆိုတာလည်း ကြိုပြီးတော့ တွက်ထားပြီးသားပါ။ ဒီ post တွင် ပထမတပိုင်း CentOS 7 ပေါ်မှာ လုပ်အပ်တဲ့ FTP နဲ့ TFTP ကိုဘယ်လို install လုပ်သလဲ၊ configure လုပ်သလဲဆိုတာကို အရင်ဆုံးသွားလိုက်ပါ့မယ်။ နောက်ပြီးတော့မှ အဲ့ဒီ FTP နဲ့ TFTP ကိုအသုံးပြုပြီးတော့ multi-vendors device တွေရဲ့ config တွေကို ဘယ်လို backup လုပ်သလဲဆိုတာကို ဆက်ရှင်းပါ့မယ်။ ဒီ process ကိုပဲ ပုံစံအမျိုးမျိုးနဲ့ ဖန်တီးယူလို့ရပါတယ်။ စာရေးသူ အသုံးပြုထားတဲ့ workflow က ကိုယ်လက်လှမ်းမှီသလောက် ရှာကျန်ပြီးတော့ လုပ်ထားတဲ့အတွက် အခြားလူတွေရဲ့ workflow နဲ့ နည်းနည်းတော့ ကွာပါလိမ့်မယ်။ နားလည်ရလွယ်မယ်လို့ တော့ စာရေးသူထင်ပါတယ်။ အရင်ဆုံး CentOS 7 ကို install လုပ်ပါ။ ကိုယ့်ရဲ့ CentOS 7 box ဟာ internet access ရှိနေရပါ့မယ်။ ပြီးရင်တော့ sudo yum update -y လုပ်ဖို့လည်း မမေ့ပါနဲ့။ အားလုံးသိကြပြီးတဲ့အတိုင်း CentOS 7 box ကိုဘယ်လို setup လုပ်သလဲ ဆိုတာကို အသေးစိတ် မသွားတော့ပါဘူး။ Install လုပ်ပြီးသား၊ update လုပ်ပြီးသား CentOS 7 ပေါ်မှာ FTP နဲ့ TFTP ကို ဘယ်လို setup လုပ်သလဲဆိုတာကို ဆက်ပြီးတော့သွားပါ့မယ်။

**FTP server ကို setup လုပ်ပုံ**

```
tyla@rpm-dev02:~$ sudo -i

[sudo] password for tyla: 

# install vsftp and ftp
root@rpm-dev02:~# yum install vsftpd ftp -y

# configure vsftpd.conf file
root@rpm-dev02:~# vi /etc/vsftpd/vsftpd.conf
```

vsftpd.conf file မှာ အောက်က အတိုင်း လိုသလို ပြင်လိုက်ပါ။

```
# disable anonymous login
anonymous_enable=NO

# remove # signs in front of following 2 lines 
ascii_upload_enable=YES
ascii_download_enable=YES

# add the following line at the end
use_localtime=YES
```

နောက်ပြီးရင်တော့ vsftpd ကို အောက်ကအတိုင်း enable နဲ့ start လုပ်လိုက်ပါ။

```
# enable vsftpd daemon to start upon system reboot
root@rpm-dev02:~# systemctl enable vsftpd

# start vsftpd daemon
root@rpm-dev02:~# systemctl start vsftpd

# grant ftp service thru firewall
root@rpm-dev02:~# firewall-cmd --permanent --add-port=21/tcp
root@rpm-dev02:~# firewall-cmd --permanent --add-service=ftp

# reload the firewall to apply the change
root@rpm-dev02:~# firewall-cmd --reload

# update SELinux boolean values for ftp service
root@rpm-dev02:~# setsebool -P ftp_home_dir on

# create a new user for ftp service
root@rpm-dev02:~# useradd gnu-ftp01

# set login password "Passw0rd!23" for newly created user gnu-ftp01
root@rpm-dev02:~# passwd gnu-ftp01
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully

# verify the ftp server login
root@rpm-dev02:~# ftp 192.168.105.10
Connected to 192.168.105.10.
Name (192.168.105.10:root): gnu-ftp01
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>

# verify the ftp server login from remote client
root@x1c:~# ftp 192.168.105.10
Connected to 192.168.105.10.
Name (192.168.105.10:root): gnu-ftp01
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp>
```

အခုဆိုရင်တော့ vsftpd ကို setup လုပ်ပြီးသွားပါပြီ။ ဒီထက်ပိုပြီးသေချာချင်ရင်တော့ file တွေကို ftp ကနေတဆင့် upload နဲ့ download လုပ်စမ်းကြည့်လို့ရပါတယ်။ ကိုယ် upload လုပ်လိုက်တဲ့ file တွေ folder တွေကိုတော့ လက်ရှိ login ဝင်ထားတဲ့ user ရဲ့ home directory မှာ တွေ့နိုင်မှာဖြစ်ပါတယ်။ ဒါကတော့ ftp service ကို CentOS 7 ပေါ်မှာ setup လုပ်တဲ့ပုံပါ။

FTP server ကတော့ အသုံးပြုလို့ရနေပါပြီ။ multi-vendors device တွေနဲ့ တွဲပြီးတော့ အသုံးပြုရမှာမို့ TFTP server လည်း setup လိုလာပြန်လို့ စာရေးသူ TFTP service ကို setup လုပ်တဲ့ပုံကို ဆက်ပြီးတော့ ရှင်းပါ့မယ်။ HPE ရဲ့ procurve switch မှာ ftp နဲ့တွဲပြီးတော့ အသုံးပြုတာ သိပ်အဆင်မပြေလို့ TFTP ကိုထက်ပြီးတော့ setup လုပ်ရပြန်ပါတယ်။ အောက်မှာတော့ tftp service ကို setup လုပ်တဲ့ ပုံစံဖြစ်ပါတယ်။

**TFTP server ကို setup လုပ်ပုံ**

```
# install tftp-server and xinetd
root@rpm-dev02:~# yum install tftp tftp-server* xinetd*

# edit /etc/xinetd.d/tftp to enable tftp via xinetd
root@rpm-dev02:~# vi /etc/xinetd.d/tftp
```

```
# default: off
# description: The tftp server serves files using the trivial file transfer \
#	protocol.  The tftp protocol is often used to boot diskless \
#	workstations, download configuration files to network-aware printers, \
#	and to start the installation process for some operating systems.
service tftp
{
	socket_type		= dgram
	protocol		= udp
	wait			= yes
	user			= root
	server			= /usr/sbin/in.tftpd
	server_args		= -c -s /tftpboot  # add -c argument for client upload
	disable         = no  # set to no to enable tftp service
	per_source		= 11
	cps             = 100 2
	flags			= IPv4
}
```

အထက်မှာပြထားတဲ့ အတိုင်း line number 13 နဲ့ 14 ကို ပြင်ဆင်ဖို့လိုပါတယ်။ ပြီးရင်တော့ save လုပ်ပြီးတော့ file ကိုပိတ်လိုက်ပါ။ နောက်တဆင့် အနေနဲ့ tftp အတွက် directory တစ်ခုကို ဖန်တီးဖို့လိုပါလိမ့်မယ်။

```
# create a tftproot folder and set required permissions
root@rpm-dev02:~# mkdir /tftproot
root@rpm-dev02:~# chmod -R 777 /tftproot

# enable tftp in systemd by configuring /usr/lib/systemd/system/tftp.service as below
root@rpm-dev02:~# vi /usr/lib/systemd/system/tftp.service
```

```
[Unit]
Description=Tftp Server
Requires=tftp.socket
Documentation=man:in.tftpd

[Service]
ExecStart=/usr/sbin/in.tftpd -c -s /tftproot
StandardInput=socket

[Install]
Also=tftp.socket
WantedBy=multi-user.target
```

```
# enable and start xinetd
root@rpm-dev02:~# systemctl enable xinetd
root@rpm-dev02:~# systemctl start xinetd

# enable and start tftp
root@rpm-dev02:~# systemctl enable tftp
root@rpm-dev02:~# systemctl start tftp
```

```
# check tftp permission in SELinux
root@rpm-dev02:~# getsebool -a | grep tftp
tftp_anon_write --> off
tftp_home_dir --> off

# if write is off as above, set 1 to enable it as following
root@rpm-dev02:~# setsebool -P tftp_anon_write 1
root@rpm-dev02:~# setsebool -P tftp_home_dir 1

# configure firewalld for tftp
root@rpm-dev02:~# firewall-cmd --permanent --add-port=69/udp
success
root@rpm-dev02:~# firewall-cmd --zone=public --add-service=tftp --permanent
success 
root@rpm-dev02:~# firewall-cmd --reload
success 

# enable and start firewalld
root@rpm-dev02:~# systemctl enable firewalld
root@rpm-dev02:~# systemctl start firewalld
```

အခုဆိုရင်တော့ TFTP server လည်း စတင်အသုံးပြုလို့ရပါပြီ။ နောက်တပိုင်းမှာတော့ multi-vendors network device တွေဘက်မှာ configuration file ကို FTP/TFTP ဆီကို လှမ်းပြီးတော့ ဘယ်လို သိမ်းလို့ရအောင် လုပ်သလဲဆိုတာကို ဆက်လက်ဖော်ပြသွားပါ့မယ်။ အထက်မှာပြောသလိုပဲ TCL/Expect လိုမျိုး script တွေကို အသုံးမပြုပဲနဲ့ neutral အတိုင်း FTP/TFTP server ပေါ်မှာ သိမ်းလို့ရတဲ့ vendor တစ်ခုချင်းစီရဲ့ built-in feature တွေပဲ အသုံးပြုသွားမှာဖြစ်ပါတယ်။ နောက်ဆုံးမှာတော့ FTP/TFTP server ပေါ်မှာ bash script တစ်ခုကို အသုံးပြုပြီးတော့ config file တွေကို housekeeping လုပ်သလဲဆိုတာကို ဆက်ပြီးတော့ ဖော်ပြပေးသွားပါ့မယ်။ ဒီအပိုင်းကိုတော့ ဒီမှာပဲရပ်လိုက်ပါတော့မယ်။
