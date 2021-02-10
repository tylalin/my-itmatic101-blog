# Linode VPS မှာကိုယ်ပိုင် Wireguard VPN server တစ်ခုတည်ဆောက်ပုံ

အခုလိုမျိုး Facebook ကို block လိုက် ဟိုဟာကို block လိုက် ဒီဟာကို block လုပ်လိုက်နဲ့ လုပ်နေတဲ့ မြန်မာနိုင်ငံရဲ့ အရေးပေါ်အခြေအနေမျိုးမှာ အသုံးတည့်တဲ့ Wireguard ကို Linode ရဲ့ VPS တစ်ခုမှာ ဘယ်လိုမျိုးကိုယ်တိုင် setup လုပ်ပြီးတော့ ကိုယ့်အသိုင်းအဝိုင်း နဲ့  ရင်းနှီးတဲ့ မိတ်ဆွေအလွယ် သုံးနိုင်အောင် ဘယ်လို setup လုပ်နိုင်သလဲဆိုတာကို မျှဝေလိုပါတယ်။ စာရေးသူ ကိုယ်တိုင်လည်း Singapore မှာ VPS တစ်လုံးကိုယ်တိုင် ထောင်ထားပြီးတော့ အမျိုးတွေနဲ့ အသိမိတ်ဆွေတွေကို ပြန်လည်မျှဝေ သုံးစေခြင်းဖြင့် free VPN ဆိုတဲ့ ရန်ကနေကင်းဝေးအောင် ကူညီနိုင်ပါတယ်။ Free VPN တွေရဲ့ nature အရ free ဖြစ်တဲ့အတွက် တစ်ခုခုကနေ revenue ရမှ ရပ်တည်နိုင်မယ့်  သဘောပါ။ Browsing history တွေ log လုပ်တာပဲဖြစ်ဖြစ်၊ အခြားသော ငွေရှာနိုင်မည့် နည်းလမ်းတွေကို တနည်းမဟုတ် တနည်းနဲ့ လုပ်ရစမြဲမို့ လုံခြုံရေး အပိုင်းမှာ အပြည့်အဝစိတ်ချရတာမျိုး မရှိတာတော့ အမှန်ပါ။ အခုလိုမျိုး မြန်မာနိုင်ငံမှာ စစ်တပ်က အာဏာသိမ်းပြီးတော့ ဗရုတ်သုတ်ခ တွေတစ်ခုပြီးတစ်ခု လျှောက်လုပ်နေတော့ မြန်မာပြည်သူတွေမှာလည်း ရရာ free VPN တွေကို အသုံးပြုရပါတော့တယ်။ နောက်တစ်ခုက free VPN တွေဟာ သုံးတဲ့ လူတွေများလာတာနဲ့ အမျှ သတ်မှတ်ထားတဲ့ bandwidth တွင်းမှာ traffic တွေဟာ အပြိုင်အဆိုင် contend လုပ်တဲ့အတွက် အားလုံးအတွက် နှေးလာပါတော့တယ်။ ကိုယ်ပိုင် VPN server ရှိခြင်းဖြင့် ရနိုင်တဲ့ အကျိုးကျေးဇူးကတော့ ကိုယ်နိုင်သလောက် လူဦးရေအတွက်ကိုသာ VPN connection လာချိတ်တဲ့အတွက် free VPN ထက်မြန်မယ်၊ လုံခြုံစိတ်ချရပါ့မယ်။ နောက်ပြီးတော့ သိပြီးကြတဲ့အတိုင်း Wireguard ဟာ lightweight ဖြစ်တဲ့အတွက် အခြားသော VPN server တွေနဲ့ မတူတာက resource intensive မဖြစ်ပါဘူး။ 

ဟုတ်ပြီ... အကုန်အကျဘယ်လောက်ရှိသလဲဆိုတော့ Linode ကို အကောင့် အသစ်စစဖွင့်ချင်း $100 ဖိုးစာကို ရက် ၆၀အတွက် free ရပါလိမ့်မယ်။ စာရေးသူရဲ့ ကြိုက်နှစ်သက်ဆုံး ဖြစ်တဲ့ Jupiter Broadcast ရဲ့ Linux Action News ကနေပြီးတော့ပေးထားတဲ့ ဒီ link လေး [https://www.linode.com/lp/podcasts/?ifso=lan](https://www.linode.com/lp/podcasts/?ifso=lan) အသုံးပြုတော့ အကောင့်အသစ်ဖွင့်ပြီးတော့ claim လိုက်ရုံပါပဲ။ တစ်ခုတော့ ရှိတယ် သုံးလို့ရတဲ့ credit card/debit card တော့လိုပါလိမ့်မယ်။ ဒီ link ကို အသုံးပြုချင်းအားဖြင့်လည်း Linux Action News podcast ကို အထောက်အကူ ပြုရာဖြစ်ပါတယ်။ $100 ဖိုးဆိုတာ Linode မှာအများကြီး သုံးရပါတယ်။ AWS မှာလိုမျိုး pricing structure မရှုပ်ထွေးတဲ့ အတွက် ရိုးရှင်းပါတယ်။ အခြေခံအကျဆုံး $5 VPS တစ်ခုကို Singapore မှာ setup လုပ်တဲ့ပုံစံကို ပြပါ့မယ်။ ပြီးတော့ အဲ့ဒီ VPS ပေါ်မှာ Wireguard ကို install လုပ်ပုံနဲ့ setup လုပ်ပုံကို ပြပါ့မယ်။ $5 တန် VPS ကို အသုံးပြုတဲ့အတွက် VPN user ၁၀ ယောက်ကနေ အယောက် ၃၀ လောက် ထိအတွက်သာကောင်းပါလိမ့်မယ်။ ဒီထက်များမယ်ဆိုရင်တော့... အခြားသော VPS သို့မဟုတ် dedicated VPS လိုမျိုးတွေကို အသုံးပြုရပါလိမ့်မယ်။ စာရေးသူ စမ်းကြည့်သလောက်တော့ Singapore မှာ VPS ကို ထားတာ အခြားသော Asia zone မှာရှိတဲ့ အခြားသော region တွေထက် ကောင်းသော VPN performance ကိုရပါတယ်။ မြန်မာနိုင်ငံနဲ့ အနီးဆုံးဖြစ်တဲ့အပြင် marine fibre backbone ကို ကြည့်လိုက်ရင်ဖြင့် တိုက်ရိုက်ဆက်သွယ်ထားတဲ့ fibre backbone မှာ bandwidth အများဆုံးနိုင်ငံလည်း ဖြစ်ပါတယ်။ ဒီအတွက် Singapore ကို strategically အရ ရွေးချယ်ခဲ့တာလည်းဖြစ်ပါတယ်။ ကဲ... internet ရတုန်းလေး စလိုက်ရအောင်ဗျာ။ 

### Linode ပေါ်မှာ VPS တစ်ခု ဖန်တီးပုံ

Cloud မှာ VPS တစ်ခုကို ဖန်တီးတဲ့အခါ မှာတစ်ခုနဲ့ တစ်ခု ခပ်ဆင်ဆင်တူကြပါတယ်။ ဒီတစ်ခုမှာတော့ basic VPS တစ်ခုကို ဘယ်လိုမျိုး တည်ဆောက်သလဲဆိုတာ အောက်မှာ gif ပုံထဲမှာ ကြည့်လိုက်ပါ။ အချိန်နည်းနည်း သက်သာအောင်လို့ ပုံတစ်ခုချင်းစီမသွားတော့ပါဘူး။ 

![](../.gitbook/assets/wg-srv-linode.gif)

အထက်မှာပြထားတဲ့ အတိုင်း Linode ပေါ်မှာ VPS တစ်ခုကို ဖန်တီးဖို့ရာ အတွက်က မခက်ပါဘူး။ ကိုယ်သုံးမယ် Linux distribution ကိုရွေးမယ်၊ Region ကိုရွေးမယ် VPS ရဲ့ အရွယ်အစား၊ နာမည် နဲ့ login လုပ်ဖို့ လိုအပ်တဲ့ root ရဲ့ password နဲ့ key authentication အတွက် ကိုယ့်ရဲ့ ssh key တွေကိုထည့်ပေးလိုက် ပြီးတော့ create လုပ်လိုက်ရုံပါပဲ။ ပြီးရင် ကိုယ်ရဲ့ VPS ကို provisioning၊ booting နဲ့ running ဆိုပြီးတော့ တစ်ခုချင်းစီပြပါလိမ့်မယ်။ သူချပေးလိုက် public IP address ကို မှတ်ထားလိုက်ပြီးတော့ အခုဆိုရင် server ထဲကို root account နဲ့ အောက်ကအတိုင်း ssh login ဝင်လို့ရပါပြီ။ 

![](../.gitbook/assets/wg-srv-key-auth.gif)

စာရေးသူ ရဲ့ ssh key ကို ဒီ VPS ကို create လုပ်တုန်းက tick လုပ်ပြီးထည့်ထားတဲ့အတွက် root ရဲ့  password ကို login လုပ်တဲ့အခါမှာ မမေးပါဘူး။ Cloud မှာ အခုလိုမျိုး VPS တစ်ခုလုပ်တဲ့အခါမှာ ကိုယ့် VPS လုံခြုံရေးအတွက် ssh configuration မှာ လိုအပ်တဲ့ ပြင်စရာလေးတွေ အချို့ရှိနေပါတယ်။ ပထမတစ်ခုက အထက်မှာလိုမျိုး root account ကို production မှာ remote login မပေးထားသင့်ပါဘူး။ ကိုယ့်ရဲ့ ကိုယ်ပိုင် account ကို VPS ထဲ ဝင်ပြီးတာနဲ့ ချက်ချင်း create လုပ်သင့်ပါတယ်။ ပြီးရင်အဲ့ဒီ account ကို sudo ဆိုတဲ့ group ထဲမှာထည့်ပေးလိုက်ရုံဖြင့် ကိုယ့် account က sudoer ဖြစ်သွားပါတယ်။ 

![](../.gitbook/assets/create-user.gif)

ကိုယ့် account နဲ့ VPS ထဲကို ssh ဝင်လို့ ရမရ အရင်စမ်း ကြည့်ပါ။ ဝင်လို့ရပြီဆိုတာနဲ့ ကိုယ် ssh ပတ်သတ်တဲ့ remote login လုံခြုံရေးအတွက် စတင်လုပ်စရာရှိတာတွေကို လုပ်လို့ ရနိုင်ပါပြီ။ အောက်ကအတိုင်း တဆင့်ပြီးတော့ တဆင့်လုပ်သွားလိုက်ပါ။ 

```bash
root@wg-srv:~# nano /etc/ssh/sshd_config

       $OpenBSD: sshd_config,v 1.103 2018/04/09 20:41:22 tj Exp $

# This is the sshd server system-wide configuration file.  See
# sshd_config(5) for more information.

# This sshd was compiled with PATH=/usr/bin:/bin:/usr/sbin:/sbin

# The strategy used for options in the default sshd_config shipped with
# OpenSSH is to specify options with their default value where
# possible, but leave them commented.  Uncommented options override the
# default value.

Include /etc/ssh/sshd_config.d/*.conf

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key

# Ciphers and keying
#RekeyLimit default none

# Logging
#SyslogFacility AUTH
#LogLevel INFO

# Authentication:

#LoginGraceTime 2m
PermitRootLogin no
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10

#PubkeyAuthentication yes

# Expect .ssh/authorized_keys2 to be disregarded by default in future.
#AuthorizedKeysFile     .ssh/authorized_keys .ssh/authorized_keys2

#AuthorizedPrincipalsFile none

#AuthorizedKeysCommand none
#AuthorizedKeysCommandUser nobody

# For this to work you will also need host keys in /etc/ssh/ssh_known_hosts
#HostbasedAuthentication no
# Change to yes if you don't trust ~/.ssh/known_hosts for
# HostbasedAuthentication
#IgnoreUserKnownHosts no
# Don't read the user's ~/.rhosts and ~/.shosts files
#IgnoreRhosts yes

# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication no
#PermitEmptyPasswords no

# Change to yes to enable challenge-response passwords (beware issues with
# some PAM modules and threads)
ChallengeResponseAuthentication no

# Kerberos options
#KerberosAuthentication no
#KerberosOrLocalPasswd yes
#KerberosTicketCleanup yes
#KerberosGetAFSToken no

# GSSAPI options
#GSSAPIAuthentication no
#GSSAPICleanupCredentials yes
#GSSAPIStrictAcceptorCheck yes
#GSSAPIKeyExchange no

# Set this to 'yes' to enable PAM authentication, account processing,
# and session processing. If this is enabled, PAM authentication will
# be allowed through the ChallengeResponseAuthentication and
# PasswordAuthentication.  Depending on your PAM configuration,
# PAM authentication via ChallengeResponseAuthentication may bypass
# the setting of "PermitRootLogin without-password".
# If you just want the PAM account and session checks to run without
# PAM authentication, then enable this but set PasswordAuthentication
# and ChallengeResponseAuthentication to 'no'.
UsePAM yes

#AllowAgentForwarding yes
#AllowTcpForwarding yes
#GatewayPorts no
X11Forwarding yes
#X11DisplayOffset 10
#X11UseLocalhost yes
#PermitTTY yes
PrintMotd no
#PrintLastLog yes
#TCPKeepAlive yes
#PermitUserEnvironment no
#Compression delayed
#ClientAliveInterval 0
#ClientAliveCountMax 3
#UseDNS no
#PidFile /var/run/sshd.pid
#MaxStartups 10:30:100
#PermitTunnel no
#ChrootDirectory none
#VersionAddendum none

# no default banner path
#Banner none

# Allow client to pass locale environment variables
AcceptEnv LANG LC_*

# override default of no subsystems
Subsystem       sftp    /usr/lib/openssh/sftp-server

# Example of overriding settings on a per-user basis
#Match User anoncvs
#       X11Forwarding no
#       AllowTcpForwarding no
#       PermitTTY no
#       ForceCommand cvs server

root@wg-srv:~# su - tyla
tyla@wg-srv:~$ mkdir .ssh
tyla@wg-srv:~$ logout
root@wg-srv:~# cp .ssh/authorized_keys /home/tyla/.ssh/authorized_keys
root@wg-srv:~# cd /home/tyla/.ssh
root@wg-srv:/home/tyla/.ssh# chown tyla:tyla authorized_keys 
root@wg-srv:/home/tyla/.ssh# ll
total 12
drwxrwxr-x 2 tyla tyla 4096 Feb  7 21:40 ./
drwxr-xr-x 4 tyla tyla 4096 Feb  7 21:40 ../
-rw------- 1 tyla tyla  389 Feb  7 21:40 authorized_keys

root@wg-srv:/home/tyla/.ssh# systemctl restart sshd
root@wg-srv:/home/tyla/.ssh# systemctl status sshd
● ssh.service - OpenBSD Secure Shell server
     Loaded: loaded (/lib/systemd/system/ssh.service; enabled; vendor preset: enabled)
     Active: active (running) since Sun 2021-02-07 21:53:32 UTC; 7s ago
       Docs: man:sshd(8)
             man:sshd_config(5)
    Process: 2001 ExecStartPre=/usr/sbin/sshd -t (code=exited, status=0/SUCCESS)
   Main PID: 2013 (sshd)
      Tasks: 1 (limit: 1074)
     Memory: 1.4M
     CGroup: /system.slice/ssh.service
             └─2013 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups

Feb 07 21:53:31 wg-srv systemd[1]: Starting OpenBSD Secure Shell server...
Feb 07 21:53:32 wg-srv sshd[2013]: Server listening on 0.0.0.0 port 22.
Feb 07 21:53:32 wg-srv sshd[2013]: Server listening on :: port 22.
Feb 07 21:53:32 wg-srv systemd[1]: Started OpenBSD Secure Shell server.
Feb 07 21:53:37 wg-srv sshd[2014]: Unable to negotiate with 167.99.41.124 port 45520: no matching key exchange method found. Their offer: diffie-hellman-group14-sha1,diffie-hellman-group-exchange-sha1,diff>
lines 1-17/17 (END)
```

အထက်က အဆင့်မှာတော့ /etc/ssh/sshd\_config ဆိုတဲ့ ssh daemon configuration file ကို nano နဲ့ဖြစ်ဖြစ်၊ vim နဲ့ ဖြစ်ဖြစ် edit လုပ်ရပါလိမ့်မယ်။ line number 36 မှာ PermitRootLogin yes ဆိုတဲ့ နေရာမှာ no လို့ပြောင်းပေးပါ။ ဒီတစ်ခုကတော့ root account နဲ့ ssh remote login ပေးမလုပ်ဘူးလို့ sshd ကို ပြောလိုက်တာပါ။ ပြီးရင် line number 60 မှာ PasswordAuthentication yes ကို no လို့ထပ်ပြောင်း ပေးရပါ့မယ်။ ဒါကတော့ password နဲ့ ssh remote login ပေးမလုပ်တော့ဘူးလို့ သတ်မှတ်ပေးလိုက်ပါ။ ဒီအတွက် ကိုယ့်ရဲ့ ssh key ကို root user account ကနေပြီးတော့ ကိုယ့် user အသစ်ရဲ့ /home/tyla/.ssh အောက်မှာ cp နဲ့ copy ကူးယူပြီးတော့ chown နဲ့ ကိုယ်ပိုင် ဖြစ်အောင်ပြောင်းပေးရပါ့မယ်။ ဒီအဆင့်က အရေးကြီးပါတယ်။ ဒီလိုလုပ်ပြီးတဲ့ အခါမှ systemctl restart sshd နဲ့ ssh daemon ကို restart ချပေးလိုက်ပါ။ အခုဆိုရင်တော့... ကိုယ့် account နဲ့ ssh authentication လုပ်ဖို့ အဆင့်သင့်ဖြစ်ပါပြီ။ SSH login လုပ်လို့ ရမရ အရင်ဆုံး စမ်းကြည့်ပါ။ အားလုံး အဆင်ပြေရင်တော့ Wireguard ကို စတင်ပြီးတော့ install လုပ်နိုင်၊ configure လုပ်နိုင်ပါပြီ။ 

### Wireguard ကို VPS ပေါ်မှာ VPN Server အနေနဲ့ configure လုပ်ပုံ

Wireguard ကိုအောက်က အတိုင်း install လုပ်လိုက်ပါ။ 

```text
$ sudo apt-get install wireguard -y
```

SSH login နဲ့ ပတ်သတ်ပြီးတော့ အားလုံး အဆင်သင့်ဖြစ်ရင် Wireguard server ပုံစံကို ကိုယ့် VPS ပေါ်မှာ အောက်မှာပြထားတဲ့အတိုင်း configure လုပ်ပြီးတော့ ပြင်ဆင်လိုက်ပါ။ ဒီ link မှာလည်း  [https://my.itmatic101.com/networking/wireguard-intro](https://my.itmatic101.com/networking/wireguard-intro) Wireguard ကို configure လုပ်တဲ့ပုံကို အနည်းငယ်ရှင်းပြီးသားမို့ ဒီမှာတော့ အတိုချုပ်ပြီးတော့ ပဲရှင်းပါတော့မယ်။ 

```text
tyla@wg-srv:~$ sudo -i
[sudo] password for tyla:  [Enter your sudoer password]
# Generating public and private keys under /etc/wireguard directory
root@wg-srv:~# cd /etc/wireguard/
root@wg-srv:~# wg genkey | tee privatekey | wg pubkey > publickey
# Creating wg0.conf file for WireGuard configuration
root@wg-srv:~# vi wg0.conf
# this section is for local wg0 interface
[Interface]
# local wg0 interface IP address
Address = 10.1.10.1
# local wg server node's private key
PrivateKey = cC6caA87hRNhOYYLFRawzWCOxMHEzzxJCJKibDasPng=
# default wg listen port
ListenPort = 51820
# wg0 up post action on iptabes to activate redirecting all traffic 
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o ens3 -j MASQUERADE
# wg0 down post action on iptabes to deactivate redirecting all traffic 
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o ens3 -j MASQUERADE
# this section is for remote peer wg0 interface 
[Peer]
# remote peer's wg public key
PublicKey = LEQj4f1sNfrF7c+7tjTFBQ8GJjL8gog+ozj4QFgYcn8=
# remote peer's wg0 interface ip address
AllowedIPs = 10.1.10.2/32
# activate the wireguard wg0 interface 
root@wg-srv:~# wg-quick up wg0
```

### Wireguard ကို client ဘက်မှာ configure လုပ်ပုံ

Wireguard ရဲ့ server ဘက်မှာ ပြင်ဆင်ပြီးရင် ကိုယ်သုံးမယ့် Wireguard client ဘက်မှာလည်း အောက်ကအတိုင်းဆက်လက် configure လုပ်လိုက်ပါ။ Client တစ်ခု ထပ်ပေါင်းထည့်ဖို့လိုတိုင်း အောက်ကအတိုင်း လုပ်ပြီးတော့ server ဘက်အခြမ်းမှာ နောက်ထပ်တိုးထည့်တဲ့ \[Peer\] တစ်ခုအနေနဲ့ သွားထည့်ပေးလိုက်ရုံပါပဲ။  

```text
tyla@wg-cl-node:~$ sudo -i
[sudo] password for tyla:  [Enter your sudoer password]
# Generating public and private keys under /etc/wireguard directory
root@wg-cl-node:~# cd /etc/wireguard/
root@wg-cl-node:~# wg genkey | tee privatekey | wg pubkey > publickey
# Creating wg0.conf file for WireGuard configuration
root@wg-cl-node:~# vi wg0.conf
# this section is for local wg0 interface
[Interface]
# local wg0 interface ip address
Address = 10.1.10.2
# local wg client node's private key
PrivateKey = aCKXChbpzlvJtdOpnYLmc/fEGH+5W7Tx/ZveSqczYVA=
# this section is for wireguard server node's wg0 interface 
[Peer]
# wireguard server node's public key
PublicKey = X8pnECl9ha2CX0JI7GsI1ygjRF4Mu1e+Lyira3EE4j0=
# wireguard server node's public ip address with port number 51820
Endpoint = 156.215.24.12:51820
# all traffic redirect thru wireguard server node 
AllowedIPs = 0.0.0.0/0
# every 25 seconds to check the wg connection status for persistence 
PersistentKeepalive = 25
# activate the wireguard wg0 interface 
root@wg-cl-node:~# wg-quick up wg0
```

အခုဆိုရင်... Wireguard ရဲ့ server ဘက်မှာရော client ဘက်ခြမ်းအတွက်ပါ အဆင်သင့်ဖြစ်ပါပြီ။ Wireguard ဟာ public/private keys တွေနဲ့ authenticate လုပ်တာမို့ ဘာမှထပ်ပြီးတော့ အခြားသော VPN service တွေမှာလို ထပ်ပြီးတော့  configure လုပ်စရာမရှိပါ။ သူ့ရဲ့ configuration ကဒါပါပဲ။ ကိုယ်လုပ်တာအကုန်မှန်တယ်ဆိုရင်တော့ wg ဆိုတဲ့ command ကို prompt မှာရိုက်ထည့်လိုက်ရင် တဘက်တချက်စီမှာ ကိုယ့်ရဲ့ peer နဲ့ဆိုင်တဲ့ အချက်အလက်တွေကို တွေ့ရမှာပဲဖြစ်ပါတယ်။ နောက်ပြီး wg server နဲ့ client node ကြားမှာ 10.1.10.0 ip ကို ping ကြည့်လို့ရတယ်ဆိုရင် wireguard ရဲ့ connection က စတင် အလုပ်လုပ်ပါပြီ။ WireGuard client node ဘက်မှာ AllowedIPs ကို ကိုယ် route ချင်တဲ့ ip address သို့မဟုတ် subnet ကိုလည်း အောက်မှာလို comma နဲ့ ထက်ပြီးတော့ ပေါင်းထည့်လို့ရပါတယ်။

```text
AllowedIPs = 10.1.10.1/32, 192.168.0.0/24 
```

အထက်ကအတိုင်း ထည့်လိုက်ရင်တော့ wg server ရဲ့ IP address နဲ့၊ peer မှာရှိတဲ့ 192.168.0.0/24 ဆိုတဲ့ subnet နဲ့ကိုတာ WireGuard ရဲ့ tunnel ထဲမှာ route လုပ်မယ်လို့ပြောတာဖြစ်ပါတယ်။

နောက်တစ်ခုက… ကိုယ်က WireGuard server node ကို reboot လုပ်တိုင်း wireguard ကို system startup မှာ service တစ်ခုအနေနဲ့ autostart လုပ်ချင်တယ်ဆိုရင်တော့ အောက်ကအတိုင်း systemd ရဲ့ systemctl ကို အသုံးပြုလို့ရပါတယ်။ Wireguard daemon ကို မသုံးလို့ ရပ်ထားချင်ရင် systemctl stop wg-quick@wg0.service နဲ့ restart လုပ်ချင်ရင် systemctl restart wg-quick@wg0.service ဆိုတာတွေကို အသုံးပြုပြီးတော့ daemon ကို systemd ရဲ့ systemctl နဲ့ ထိန်းလို့ရပါတယ်။ တစ်ခုတော့ရှိတယ်.... အပေါ်မှာ သုံးပြထားတဲ့ command တွေထဲမှာ wg-quick up wg0 ဆိုတာအတွက် wg-quick down wg0 ဆိုတဲ့ command ကိုအရင်ဆုံး အသုံးပြုပြီးတော့မှ systemctl command ကိုသုံးပါ။ 

```text
root@wg-srv-node:~# systemctl enable wg-quick@wg0.service
```

ကိုယ်က mobile phone မှာ Wireguard app ကို အသုံးပြုတဲအခါမှာ client side ဘက်က configuration တွေကိုကူးယူပြီးတော့ ထည့်ရတာ တော်တော်လေးလက်ဝင်ပါတယ်။ အထူးသဖြင့် public/private keys တွေကိုတစ်ခုချင်းစီရိုက်ထည့်ရတာ မလွယ်ပါဘူး။ အဲ့ဒီအတွက် ကိုယ်ရဲ့ Wireguard client configuration ကို QR Code အနေနဲ့ ပြောင်းပြီးတော့ mobile phone camera နဲ့ scan ဖတ်ပြီးတော့ configure လုပ်ရတာ ပိုပြီးတော့ အဆင်ပြေပါတယ်။ အောက်ကအတိုင်း လိုက်ပြီးတော့ install လုပ်၊ QR code ကို issue လုပ်လို့ ရပါတယ်။ 

```text
root@wg-cl-node:~# apt install qrencode
root@wg-cl-node:~# qrencode  -t ansiutf8 < tyla.conf
```

### Ubuntu မှာ UFW firewall ကို အသုံးပြုပြီးတော့ Wireguard အတွက် port ဖွင့်ပေးပုံ

ကိုယ့်ရဲ့ VPS ဟာ public internet မှာ public IP address နဲ့ expose ဖြစ်မှာမို့ Ubuntu ရဲ့ ufw Firewall ကို အသုံးပြုပြီးတော့ port တွေကို limit လုပ်ရပါလိမ့်မယ်။ ဘယ်လို လုပ်လို့ရသလဲဆိုတာကို အောက်မှာ တချက်ကြည့်လိုက်ရအောင်။

UFW ဆိုတာကတော့ Ubuntu ရဲ့ default firewall တစ်ခုပါ။ Uncomplicated Firewall ကို အတိုကောက်ခေါ်ဆိုထားတာလည်းဖြစ်ပါတယ်။ UFW ဟာ iptables ရဲ့ abstraction layer တစ်ခုအနေနဲ့ အပေါ်ကနေ အုပ်ထားပါတယ်။ ကိုယ်က ufw ကို enable မလုပ်ထားရင် သူ့ status က inactive ပါ။ Inactive ဆိုတဲ့နေရာမှာ ufw feature ကို အသုံးမပြုထားဘူးဆိုတဲ့ အဓိပ္ပာယ်ပါ၊ firewall ကို disable လုပ်ထားတာမဟုတ်ပါဘူး။ Underlay မှာတော့ iptables ကို security အရအသုံးပြုထားပါတယ်။ Wireguard အတွက် Ubuntu မှာ ufw သုံးပြီးတော့ ဘယ်လိုမျိုး port ကို ဖွင့်ပေးတဲ့ ပုံကိုကြည့်လိုက်အောင်။ 

```text
root@wg-srv-node:~# sudo ufw default deny incoming
Default incoming policy changed to 'deny'
(be sure to update your rules accordingly)

root@wg-srv-node:~# sudo ufw default allow outgoing
Default outgoing policy changed to 'allow'
(be sure to update your rules accordingly)

root@wg-srv-node:~# ufw allow 22/tcp
root@wg-srv-node:~# ufw allow 51820/udp
root@wg-srv-node:~# ufw enable
root@wg-srv-node:~# ufw status verbose
Status: active
Logging: on (low)
Default: deny (incoming), allow (outgoing), disabled (routed)
New profiles: skip

To                         Action      From
--                         ------      ----          
51820/udp                  ALLOW IN    Anywhere                  
22                         ALLOW IN    Anywhere                  
51820/udp (v6)             ALLOW IN    Anywhere (v6)             
22 (v6)                    ALLOW IN    Anywhere (v6)             

```

အခုဆိုရင်တော့... Wireguard နဲ့ ssh အတွက် ufw ကိုပြင်ဆင်တာပြီးသွားတာဖြစ်တဲ့အတွက် Wireguard connection ကို စတင်စမ်းသပ်လို့ရပါပြီ။ 

