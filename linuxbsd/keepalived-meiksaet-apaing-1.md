# Keepalived မိတ်ဆက် – အပိုင်း (၁)

နည်းပညာနဲ့ ပတ်သတ်လာရင် Linux မှာလုပ်လို့ မရနိုင်တာ မရှိသလောက်ပါပဲ။ အခြားသော operating system တွေနဲ့ ကွာခြားချက်ကတော့ ကိုယ့်အိမ်မှာ စမ်းသပ်ချင်လို့လုပ်တဲ့ setup မှာရနိုင်တာနဲ့ production မှာစနစ်တကျ တည်ဆောက်ပြီးမှာရလာတဲ့ setupအတွက် ရနိုင်တာအများကြီး မကွာခြားပါဘူး။ Windows လို operating system မှာ trial တွေရနိုင်သော်လည်း ရေရှည်စမ်းသပ်အသုံးပြုဖို့အတွက်ကြတော့ ဘာမှများများစားစားမရှိသလိုမျိုးခံစားရပါတယ်။ တဘက်မှာလည်း BSD တို့လို alternative operating system တွေရှိသော်လည်း Linux မှာလောက်ပြီးပြည့်စုံတယ်လို့ မခံစားရပြန်ပါဘူး။ Tool တွေစုံစုံလင်လင်နဲ့ ပြီးပြည်စုံတဲ့ platform တစ်ခုလိုမျိုး စာရေးသူ အမြဲခံစားရပါတယ်။ အဲ့ဒါကြောင့်လည်း အရှေ့မှာထပ်ခါထပ်ခါ ပြောခဲ့သလိုမျိုးပဲ Linux operating system ကို မြတ်မြတ်နိုးနိုး စတင်လေ့လာလိုက်ကတည်းက နည်းပညာအတွက် သင်ကြားမှုမှာ ပိုမိုသင်ယူရလွယ်ကူလာပြီး တိုးတက်နှုန်းလည်း ပိုမြန်လာနိုင်တာတော့ စာရေးသူ တယောက်တည်းရဲ့ အတွေ့အကြုံ တစ်ခုတည်း ဖြစ်မယ်မထင်ပါဘူး။ ဒီ့အတွက် Linux လိုမျိုး ပြီးပြည့်စုံတဲ့ operating system တစ်ခုလည်းဖြစ်၊ open-source မှာလည်း လမ်းပြရှေ့ဆောင်လည်း ဖြစ်တဲ့အတွက် လေ့လာဖြစ်အောင်လေ့လာဖို့ကို တိုက်တွန်းလိုပါတယ်။

ဒီ post မှာတော့ Cisco routing နဲ့ switching မှာလုပ်လို့ရတဲ့ feature တစ်ခုဖြစ်တဲ့ Virtual Router Redundancy Protocol (VRRP) ကို routing and switching gear မပါပဲနဲ့ Linux ပေါ်မှာ setup လုပ်တဲ့ပုံစံကို မိတ်ဆက်ပေးလိုပါတယ်။ ပုံမှန်အားဖြင့် High Availability (HA) system တစ်ခုကိုတည်ဆောက်တော့မယ်ဆိုရင် VRRP ကို router တွေ switch တွေပေါ်မှာ configure လုပ်ကြပါတယ်။ အရှင်းဆုံးပြောရရင် VRRP ဟာ router နှစ်ခုကြားမှာ Virtual IP (VIP) ကိုအသုံးပြုပြီးတော့၊ router နှစ်ခုမှာ တစ်ခုလုံးဝ down သွားရင်တောင် ဆက်ပြီးတော့ routing နဲ့ switching မှာအလုပ်လုပ် အောင်သုံးတဲ့ redundancy protocol တစ်ခုပါ။ Cisco CLI မှာလည်း configure လုပ်ရတာ အရမ်းကြီးခက်ခဲတဲ့ အရာတော့မဟုတ်ပါဘူး။ IT networking နဲ့ ပတ်သတ်တဲ့ job interview တွေမှာဆို VRRP topic ဟာ မမေးမဖြစ် မေးခွန်းတစ်ခုပါ။ HA system တစ်ခုအတွက်အသုံးများတဲ့ topic တစ်ခုဖြစ်တဲ့အတွက် မသိမဖြစ်သိထားရမည့် အရာလည်းဖြစ်ပါတယ်။ အောက်မှာပြထားတဲ့ အတိုင်း ကိုယ့် network မှာအခုလိုမျိုး VRRP ကိုအသုံးပြုပြီးတော့ HA setup လုပ်နိုင်ပါတယ်။ သတိပြုရမှာက ပုံမှာကိုယ့်ရဲ့ server တွေကို Gateway မှာ router တစ်ခုချင်းစီရဲ့ IP ကို configure မလုပ်ပဲနဲ့ Virtual IP (VIP) ကိုအသုံးပြုရမှာဖြစ်ပါတယ်။

![](https://itmatic101.com/wp-content/uploads/2022/06/VRRP1-1.png)

ဒါဆိုရင် VRRP ကို router တွေမှာဘယ်လိုမျိုး အသုံးပြုနိုင်သလဲဆိုတာမျက်လုံးထဲမှာမြင်မယ်ထင်ပါတယ်။ ဟုတ်ပြီ… ဒါဆိုစာရေးသူတို့ VRRP လိုမျိုး keepalived ကို Ubuntu Linux 20.04 LTS VMs နှစ်ခုပေါ်မှာ Apache web server ကိုအသုံးပြုပြီးတော့ Lab တစ်ခုတည်ဆောက်ကြည့်ရအောင်။ ပထမဆုံးအနေနဲ့ လိုအပ်တဲ့ Ubuntu 20.04 LTS VMs နှစ်ခုကို အရင် install လုပ်ပြီးတော့ ပြင်ဆင်ရပါ့မယ်၊ ပြီးရင်တော့ လိုအပ်တဲ့ Apache နဲ့ Keepalived ကိုအောက်မှာပြထားတဲ့ အတိုင်း VM နှစ်ခုလုံးပေါ်မှာ apt နဲ့ လုပ်ပြီး service နှစ်ခုလုံးကို enable လုပ်မယ်၊ start လုပ်လိုက်ပါ့မယ်။ စာရေးသူ ပထမ VM ကို web1 လို့ ခေါ်ပြီး၊ ဒုတိယ တစ်ခုကိုတော့ web2 ဆိုပြီးတော့ နာမည်ပေးထားပါ့မယ်။

```
$ sudo apt update && sudo apt install -y apache2 keepalived
$ sudo systemctl enable apache2 keepalived
$ sudo systemctl start apache2 keepalived
```

အဲ့ဒါပြီးရင် install လုပ်ထားတဲ့ Apache နဲ့ Keepalived ကိုခပ်သွက်သွက်လေး အောက်ကအတိုင်း configure လုပ်လိုက်ရအောင်။ ပထမဆုံး web1 မှာ အခုလိုမျိုး configure လုပ်ရပါ့မယ်။ တခုသတိထားရမှာက keepalived.conf ကို အသစ် create လုပ်ရမှာဖြစ်ပါတယ်။ Keepalived ကို install လုပ်ပြီးရင်တောင် အဲ့ဒီ configuration file က /etc/keepalived/ မှာရှိမနေပါဘူး။

```
$ sudo echo web1 > /var/www/html/index.html
$ vim /etc/keepalived/keepalived.conf

# configuation for the virtual interface
vrrp_instance vi_1 {
    interface eth1
    state MASTER
    priority 101
    advert_int 1
    virtual_router_id 77
    unicast_src_ip 192.168.56.11
    unicast_peer {
        192.168.56.12
    }

    authentication {
        auth_type PASS
        auth_pass secret 
    }

    # the virtual ip address shared between the two servers
    virtual_ipaddress {
		192.168.56.69
    }
}

$ sudo systemctl restart keepalived
```

ပြီးရင် web2 ပေါ်မှာအောက်ကအတိုင်း ဆက်ပြီးတော့ configure လုပ်ပါ။

```
$ sudo echo web2 > /var/www/html/index.html
$ vim /etc/keepalived/keepalived.conf

# configuation for the virtual interface
vrrp_instance vi_1 {
    interface eth1
    state BACKUP
    priority 100
    advert_int 1
    virtual_router_id 77
    unicast_src_ip 192.168.56.12
    unicast_peer {
        192.168.56.11
    }

    authentication {
        auth_type PASS
        auth_pass secret 
    }

    # the virtual ip address shared between the two servers
    virtual_ipaddress {
		192.168.56.69
    }
}  

$ sudo systemctl restart keepalived 
```

ဒီမှာ စာရေးသူတို့ ဘာတွေ configure လုပ်ထားသလဲဆိုတာ နည်းနည်းရှင်းပြဖို့လိုပါတယ်။ Apache web ပေါ်မှာတော့ လွယ်ပါတယ်၊ /var/www/html/index.html အတွက်တော့ web1 မှာဆိုရင် web1 မှန်းသိအောင် echo နဲ့ insert လုပ်သွားတာပါ။ Keepalived အတွက် configuration မှာတော့ နည်းနည်းထပ်ရှင်းဖို့လိုပါလိမ့်မယ်။

```
vrrp_instance vi_1 { # ဒီတလိုင်းမှာတော့ vrrp ရဲ့ instance ID ကိုဖန်းတီးလိုက်တာပါ။ 
    interface eth1 # interface ဆိုတာကတော့ ကိုယ်serverရဲ့ network interface IDပါ။
    state MASTER # state မှာတော့ ဒီ server ကို active master node အနေနဲ့ထားတာပါ။ 
    priority 101 # priorityကတော့ nodeတွေရွေးရင်ဘယ် nodeကိုဦးစားပေးမလဲအတွက်ပါ။
    advert_int 1 # advertisement interval အတွက်ပါ။ hello packetနဲ့ ဆင်တူပါတယ်။ 
    virtual_router_id 77 # router ID ဖြစ်ပါတယ်။ node နှစ်ခုလုံးမှာID တူရပါ့မယ်။ 
    unicast_src_ip 192.168.56.11 # broadcast အစား unicastကို သုံးချင်လို့ပါ။ 
    unicast_peer {
        192.168.56.12 # unicast peer တွေအတွက်ထားတဲ့ placeholder ပါ။ 
    }
```

ဒီတပိုင်းမှာ unicast\_src\_ip နဲ့ unicast\_peer နှစ်ခုမထည့်လည်း ရပါတယ်။ သို့သော် security အတွက် broadcast အစား unicast ကို အသုံးပြုချင်လို့ ဖြစ်ပါတယ်။ နောက်တပိုင်းမှာတော့ authentication နဲ့ virtual\_ipaddress ကို သတ်မှတ်ပေးတာပါ။

```
authentication {
        auth_type PASS # authentication အမျိုးအစားထဲမှာမှ passwordကိုသုံးထားပါတယ်။
        auth_pass secret # ဒါကတော့ keepalivedအတွက် password ပါ။ 
    }

    # the virtual ip address shared between the two servers
    virtual_ipaddress {
		192.168.56.69 # ကိုယ်သုံးချင် Virtual IP (VIP) ပါ။
    }
} 
```

![](https://itmatic101.com/wp-content/uploads/2022/06/Keepalived1.png)

web1 မှာ sudo systemctl status keepalived ဆိုပြီးတော့ service status ကြည့်လိုက်ရင် အောင်ကအတိုင်းတွေ့ရမှာပါ။

```
vagrant@web1:~$ sudo systemctl status keepalived
● keepalived.service - Keepalive Daemon (LVS and VRRP)
     Loaded: loaded (/lib/systemd/system/keepalived.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-06-11 06:15:31 UTC; 6min ago
   Main PID: 15463 (keepalived)
      Tasks: 2 (limit: 1071)
     Memory: 1.8M
     CGroup: /system.slice/keepalived.service
             ├─15463 /usr/sbin/keepalived --dont-fork
             └─15475 /usr/sbin/keepalived --dont-fork

Jun 11 06:15:31 web1 Keepalived[15463]: WARNING - keepalived was build for newer Linux 5.4.166, running>
Jun 11 06:15:31 web1 Keepalived[15463]: Command line: '/usr/sbin/keepalived' '--dont-fork'
Jun 11 06:15:31 web1 Keepalived[15463]: Opening file '/etc/keepalived/keepalived.conf'.
Jun 11 06:15:31 web1 Keepalived[15463]: Starting VRRP child process, pid=15475
Jun 11 06:15:31 web1 Keepalived_vrrp[15475]: Registering Kernel netlink reflector
Jun 11 06:15:31 web1 Keepalived_vrrp[15475]: Registering Kernel netlink command channel
Jun 11 06:15:31 web1 Keepalived_vrrp[15475]: Opening file '/etc/keepalived/keepalived.conf'.
Jun 11 06:15:31 web1 Keepalived_vrrp[15475]: Registering gratuitous ARP shared channel
Jun 11 06:15:31 web1 Keepalived_vrrp[15475]: (vi_1) Entering BACKUP STATE (init)
Jun 11 06:15:35 web1 Keepalived_vrrp[15475]: (vi_1) Entering MASTER STATE
```

web2 မှာကြည့်ရင်တော့ အခုလိုမျိုးတွေ့ရမှာပါ။

```
vagrant@web2:~$ sudo systemctl status keepalived
● keepalived.service - Keepalive Daemon (LVS and VRRP)
     Loaded: loaded (/lib/systemd/system/keepalived.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-06-11 06:17:53 UTC; 5min ago
   Main PID: 15143 (keepalived)
      Tasks: 2 (limit: 1071)
     Memory: 1.8M
     CGroup: /system.slice/keepalived.service
             ├─15143 /usr/sbin/keepalived --dont-fork
             └─15153 /usr/sbin/keepalived --dont-fork

Jun 11 06:17:53 web2 Keepalived[15143]: Starting Keepalived v2.0.19 (10/19,2019)
Jun 11 06:17:53 web2 Keepalived[15143]: WARNING - keepalived was build for newer Linux 5.4.166, running >
Jun 11 06:17:53 web2 Keepalived[15143]: Command line: '/usr/sbin/keepalived' '--dont-fork'
Jun 11 06:17:53 web2 Keepalived[15143]: Opening file '/etc/keepalived/keepalived.conf'.
Jun 11 06:17:53 web2 Keepalived[15143]: Starting VRRP child process, pid=15153
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Registering Kernel netlink reflector
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Registering Kernel netlink command channel
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Opening file '/etc/keepalived/keepalived.conf'.
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Registering gratuitous ARP shared channel
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: (vi_1) Entering BACKUP STATE (init)
```

ကိုယ်ကစမ်းချင်တယ်ဆိုရင်တော့ web browser ပဲဖြစ်ဖြစ်၊ terminalထဲမှာပဲဖြစ်ဖြစ် အောက်ကအတိုင်းရိုက်ထည့်ပြီးတော့ ကြည့်လို့ရပါတယ်။

```
$ watch -n 30 curl 192.168.56.69 

Every 30.0s: curl 192.168.56.69                                                                                                                                                       e32: Sat Jun 11 16:35:29 2022

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
   0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0 100     5  100     5    0     0   5000      0 --:--:-- --:--:-- --:--:--  5000
web1
```

web1 VM ကို shutdown လုပ်လိုက်မယ်ဆိုရင်တော့ အောက်ကအတိုင်း ပြောင်းသွားပါလိမ့်မယ်။ web2 ကို failover လုပ်သွားတာဖြစ်ပါတယ်။ ပြီးရင် web1 ကို boot ပြန်တက်လိုက်ပါ။

```
$ watch -n 30 curl 192.168.56.69 

Every 30.0s: curl 192.168.56.69                                                                                                                                                       e32: Sat Jun 11 16:35:29 2022

  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
   0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0 100     5  100     5    0     0   5000      0 --:--:-- --:--:-- --:--:--  5000
web2
```

ရှင်းရှင်းလင်းလင်းတွေ့ချင်ရင်တော့ sudo systemctl status keepalived ကိုကြည့်လိုက်ရင် အခုလိုတွေ့ရမှာပါ။

```
vagrant@web1:~$ sudo systemctl status keepalived
● keepalived.service - Keepalive Daemon (LVS and VRRP)
Loaded: loaded (/lib/systemd/system/keepalived.service; enabled; vendor preset: enabled)
Active: active (running) since Sat 2022-06-11 06:26:53 UTC; 4min 16s ago
Main PID: 638 (keepalived)
Tasks: 2 (limit: 1071)
Memory: 4.6M
CGroup: /system.slice/keepalived.service
├─638 /usr/sbin/keepalived --dont-fork
└─723 /usr/sbin/keepalived --dont-fork

Jun 11 06:26:54 web1 Keepalived_vrrp[723]: Opening file '/etc/keepalived/keepalived.conf'.
Jun 11 06:26:54 web1 Keepalived_vrrp[723]: Registering gratuitous ARP shared channel
Jun 11 06:26:54 web1 Keepalived_vrrp[723]: (vi_1) Entering BACKUP STATE (init)
Jun 11 06:26:55 web1 Keepalived_vrrp[723]: (vi_1) received lower priority (100) advert from 192.168.56.>
Jun 11 06:26:56 web1 Keepalived_vrrp[723]: (vi_1) received lower priority (100) advert from 192.168.56.>
Jun 11 06:26:57 web1 Keepalived_vrrp[723]: (vi_1) received lower priority (100) advert from 192.168.56.>
Jun 11 06:26:57 web1 Keepalived_vrrp[723]: (vi_1) Entering MASTER STATE
Jun 11 06:27:01 web1 Keepalived_vrrp[723]: (vi_1) Entering BACKUP STATE
Jun 11 06:27:01 web1 Keepalived_vrrp[723]: (vi_1) sent 0 priority
Jun 11 06:27:01 web1 Keepalived_vrrp[723]: (vi_1) Entering MASTER STATE


vagrant@web2:~$ sudo systemctl status keepalived
● keepalived.service - Keepalive Daemon (LVS and VRRP)
     Loaded: loaded (/lib/systemd/system/keepalived.service; enabled; vendor preset: enabled)
     Active: active (running) since Sat 2022-06-11 06:17:53 UTC; 13min ago
   Main PID: 15143 (keepalived)
      Tasks: 2 (limit: 1071)
     Memory: 1.8M
     CGroup: /system.slice/keepalived.service
             ├─15143 /usr/sbin/keepalived --dont-fork
             └─15153 /usr/sbin/keepalived --dont-fork

Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Registering Kernel netlink reflector
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Registering Kernel netlink command channel
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Opening file '/etc/keepalived/keepalived.conf'.
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: Registering gratuitous ARP shared channel
Jun 11 06:17:53 web2 Keepalived_vrrp[15153]: (vi_1) Entering BACKUP STATE (init)
Jun 11 06:23:28 web2 Keepalived_vrrp[15153]: (vi_1) Backup received priority 0 advertisement
Jun 11 06:23:29 web2 Keepalived_vrrp[15153]: (vi_1) Entering MASTER STATE
Jun 11 06:26:58 web2 Keepalived_vrrp[15153]: (vi_1) Master received advert from 192.168.56.11 with highe>
Jun 11 06:26:58 web2 Keepalived_vrrp[15153]: (vi_1) Entering BACKUP STATE
Jun 11 06:27:01 web2 Keepalived_vrrp[15153]: (vi_1) Backup received priority 0 advertisement
```

web1 နဲ့ web2 Ubuntu 20.04 LTS server နှစ်လုံးကို အကုန်လုံး install လုပ်တာနဲ့ configure လုပ်တာ အချိန်ပေးရပါလိမ့်မယ်။ ဒီ့အတွက် စာရေးသူ Vagrant ကိုအသုံးပြုပြီးတော့ server နှစ်ခုကိုအောက်ကအတိုင်း stand up လုပ်ထားပါတယ်။

```
# -*- mode: ruby -*- 
# vi: set ft=ruby :

BOX_IMAGE = "bento/ubuntu-20.04"
NODE_COUNT = 2

Vagrant.configure("2") do |config|
  (1..NODE_COUNT).each do |x|    
    config.vm.define "web#{x}" do |subconfig|
      subconfig.vm.box = BOX_IMAGE
      subconfig.vm.hostname = "web#{x}"
      subconfig.vm.network :private_network, ip: "192.168.56.#{x + 10}"     
      # subconfig.vm.provision :shell, path: "web_bootstrap.sh"
      subconfig.vm.provision "shell", inline: <<-Web
        sudo -i   
        apt update && apt install -y apache2 keepalived
        echo web#{x} > /var/www/html/index.html
        systemctl enable apache2 keepalived
        systemctl start apache2 keepalived
      Web
      if (subconfig.vm.hostname=="web1") then
        subconfig.vm.provision "file", source: "./keepalived_master.conf", destination: "~/keepalived.conf"
        subconfig.vm.provision "shell", inline: <<-W1     
          sudo cp /home/vagrant/keepalived.conf /etc/keepalived/keepalived.conf
        W1
      else
        subconfig.vm.provision "file", source: "./keepalived_backup.conf", destination: "~/keepalived.conf"
        subconfig.vm.provision "shell", inline: <<-W2
          sudo cp /home/vagrant/keepalived.conf /etc/keepalived/keepalived.conf
        W2
      end
      subconfig.vm.provision "shell", inline: <<-W3
        sudo systemctl restart apache2 keepalived
      W3
    end
  end

  # copy ssh public key to the VM and update then reboot
  config.vm.provision "file", source: "./me.pub", destination: "~/.ssh/me.pub"  
  config.vm.provision "shell", inline: <<-SHELL     
    cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
 SHELL
end
```

Vagrant ကို run ဖို့အတွက် လိုအပ်တဲ့ file တွေအားလုံးကို GitHub ပေါ်မှာတင်ပေးထားပါတယ်။

[https://github.com/tylalin/ITmatic101/tree/master/infra\_as\_code/vagrant\_files/keepalived\_2nodes](https://github.com/tylalin/ITmatic101/tree/master/infra\_as\_code/vagrant\_files/keepalived\_2nodes)

ပထမတစ်ခေါက် vagrant up ကို run တဲ့အခါမှာတော့ bento ကနေပြီး Ubuntu 20.04 LTS image ကို download ဆွဲတဲ့အတွက် အနည်းငယ် ကြာပါလိမ့်မယ်။ Download ဆွဲပြီးသွားရင်တော့ နောက်အခေါက်တွေ run တဲ့အခါ ပထမတခေါက်လောက်မကြာတော့ပါဘူး။ Vagrant ကို setup လုပ်ပုံနဲ့ အသုံးပြုပုံကို အောက်က Link မှာသွားရောက်ဖတ်ရှုလို့ ရပါတယ်။

{% embed url="https://itmatic101.com/2020/12/28/rough-edges-iac-part2/" %}

အဲ့ဒီ post ကိုပဲ GitBook မှာသွားရောက်ဖတ်ရှုချင်တယ်ဆိုရင်တော့ အောက်က Link မှာသွားဖတ်လို့ရပါတယ်။

{% embed url="https://my.itmatic101.com/automation/rough-edges-iac-part2" %}

ဒီအပိုင်းမှာတော့ ဒီလောက်နဲ့ပဲရပ်လိုက်ပါ့မယ်။ ဒုတိယပိုင်းမှာ keepalived ကိုနောက်ပုံစံတမျိုးနဲ့ အသုံးပြုပြပြီး setup လုပ်တဲ့အခါမှာ Ubuntu 20.04 LTS VM လေးခု လိုအပ်ပါလိမ့်မယ်။
