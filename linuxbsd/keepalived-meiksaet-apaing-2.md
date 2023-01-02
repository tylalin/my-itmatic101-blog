---
cover: ../.gitbook/assets/2022-06-11_18-16.png
coverY: 0
---

# Keepalived မိတ်ဆက် – အပိုင်း (၂)

ပထမပိုင်းမှာ keepalived ကိုအသုံးပြုပြီးတော့ VRRP ကိုဘယ်လို setup လုပ်လို့ရသလဲဆိုတာကို Apache web server နှစ်လုံးနဲ့ lab လုပ်ပြခဲ့ပြီးပါပြီ။ တကယ်ဆိုရင် အဲ့ဒီအပိုင်းမှာ setup လုပ်တဲ့ပုံစံက လွယ်အောင်၊ ပြီးတော့ ကိုယ့် PC က CPU နဲ့ RAM မလောက်ခဲ့ရင်တောင် အနည်းဆုံး Virtualbox မှာ VM နှစ်လုံးနဲ့ စမ်းသပ်နိုင်အောင် အရင်ဆုံး ရှင်းပြလိုက်တာဖြစ်ပါတယ်။ လုံးဝ fully high availability (HA) ပုံစံမျိုးတော့ အလုပ်လုပ်မှာမဟုတ်ပါဘူး။ Web server နှစ်လုံးထဲက တစ်လုံး down သွားရင်နောက် တစ်လုံးကဝင်ပြီးတော့ failover လုပ်ရုံသာရှိပါတယ်။ ဆိုပါတော့… ပထမ web server က down တော့မသွားဘူး သို့သော် overload ဖြစ်နေတယ်ဆိုရင် end user experience အတွက်လုံးဝကို အလုပ်မဖြစ်ပါဘူး။ Fully HA ဖြစ်ဖို့ဆိုရင် load balancer လိုပါလိမ့်မယ်။ ဒီအတွက်စာရေးသူတို့ haproxy ကို web server ရဲ့အရှေ့မှာ reverse proxy အနေနဲ့ အသုံးပြုပါ့မယ်။ ပြီးတော့ keepalived ကို web server ပေါ်မှာ မတင်ပဲနဲ့ haproxy နှစ်လုံးနဲ့ keepalived ကိုတွဲပြီးတော့ setup လုပ်မှာဖြစ်ပါတယ်။ ဒီ့အတွက် web server အတွက် Ubuntu 20.04 LTS VM နှစ်လုံး၊ haproxy နဲ့ keepalived တွဲပြီးတော့ အသုံးပြုဖို့အတွက် VM နှစ်လုံးလိုပါလိမ့်မယ်။ အောက်မှာပြထားတဲ့ ပုံအတိုင်း ha1 နဲ့ ha2 က Haproxy နှစ်လုံးဖြစ်ပြီး၊ web1 နဲ့ web2 ကတော့ Apache web server နှစ်လုံးဖြစ်ပါတယ်။ သတိပြုရမှာက ဒီ setup မှာ keepalived ကို ha1 နဲ့ ha2 ပေါ်မှာ setup လုပ်မှာဖြစ်ပါတယ်။

<figure><img src="../.gitbook/assets/keepalived_4nodes_1-1.png" alt=""><figcaption></figcaption></figure>

Apache web server နှစ်လုံးကို အရှေ့တပိုင်းမှာလို install လုပ်ပြီးတော့၊ configure လုပ်ထားလိုက်ပါ။ သို့သော်… keepalived ကိုတော့ ဒီတခေါက် web server ပေါ်မှာတိုက်ရိုက် install မလုပ်ပါဘူး။ Haproxy အတွက် Ubuntu 20.04 LTS VM နှစ်လုံး အဆင်သင့်ဖြစ်ပြီ ဆိုရင်အောက်ကအတိုင်း Haproxy နဲ့ Keepalived ကို install လုပ်၊ configure စတင်လုပ်ပါတော့မယ်။ ပထမဆုံး ha1 မှာ install နဲ့ configure လုပ်ပုံကို အရင်ဆုံးသွားလိုက် ရအောင်။

```
$ sudo apt update && sudo apt install -y haproxy keepalived
$ sudo systemctl enable haproxy keepalived
$ sudo systemctl start haproxy keepalived
$ sudo vim /etc/haproxy/haproxy.cfg

global
	log /dev/log	local0
	log /dev/log	local1 notice
	chroot /var/lib/haproxy
	stats socket /run/haproxy/admin.sock mode 660 level admin expose-fd listeners
	stats timeout 30s
	user haproxy
	group haproxy
	daemon

	# Default SSL material locations
	ca-base /etc/ssl/certs
	crt-base /etc/ssl/private

	# See: https://ssl-config.mozilla.org/#server=haproxy&server-version=2.0.3&config=intermediate
        ssl-default-bind-ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384
        ssl-default-bind-ciphersuites TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA256
        ssl-default-bind-options ssl-min-ver TLSv1.2 no-tls-tickets

defaults
	log	global
	mode	http
	option	httplog
	option	dontlognull
        timeout connect 5000
        timeout client  50000
        timeout server  50000
	errorfile 400 /etc/haproxy/errors/400.http
	errorfile 403 /etc/haproxy/errors/403.http
	errorfile 408 /etc/haproxy/errors/408.http
	errorfile 500 /etc/haproxy/errors/500.http
	errorfile 502 /etc/haproxy/errors/502.http
	errorfile 503 /etc/haproxy/errors/503.http
	errorfile 504 /etc/haproxy/errors/504.http

frontend myweb
	bind *:80
	option tcplog
	mode tcp
	default_backend web-servers
    
backend web-servers
    mode tcp
    balance roundrobin
    option tcp-check
    server web1 192.168.56.11:80 check fall 3 rise 2
    server web2 192.168.56.12:80 check fall 3 rise 2

$ vim /etc/keepalived/keepalived.conf

# define the script used to check if haproxy is still working
vrrp_script chk_haproxy {
    script “killall -0 haproxy”
    interval 2
    weight 2
}

# configuation for the virtual interface
vrrp_instance vi_1 {
    interface eth1
    state master
    priority 101
    advert_int 2
    virtual_router_id 101
    unicast_src_ip 192.168.56.21
    unicast_peer {
        192.168.56.22
    }

    authentication {
        auth_type PASS
        auth_pass mylittlesecret 
    }

    # the virtual ip address shared between the two loadbalancers
    virtual_ipaddress {
		192.168.56.69
    }

    # use the script above to check if we should fail over
    track_script {
        chk_haproxy
    }
}

$ sudo  systemctl restart haproxy keepalived
```

ပြီးသွားရင် ha2 ပေါ်မှာလည်း အောက်ကအတိုင်းဆက်ပြီး install လုပ်၊ configure လုပ်ဖို့လိုပါလိမ့်မယ်။

```
$ sudo apt update && sudo apt install -y haproxy keepalived
$ sudo systemctl enable haproxy keepalived
$ sudo systemctl start haproxy keepalived
$ vim /etc/haproxy/haproxy.cfg

global
	log /dev/log	local0
	log /dev/log	local1 notice
	chroot /var/lib/haproxy
	stats socket /run/haproxy/admin.sock mode 660 level admin expose-fd listeners
	stats timeout 30s
	user haproxy
	group haproxy
	daemon

	# Default SSL material locations
	ca-base /etc/ssl/certs
	crt-base /etc/ssl/private

	# See: https://ssl-config.mozilla.org/#server=haproxy&server-version=2.0.3&config=intermediate
        ssl-default-bind-ciphers ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-ECDSA-CHACHA20-POLY1305:ECDHE-RSA-CHACHA20-POLY1305:DHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384
        ssl-default-bind-ciphersuites TLS_AES_128_GCM_SHA256:TLS_AES_256_GCM_SHA384:TLS_CHACHA20_POLY1305_SHA256
        ssl-default-bind-options ssl-min-ver TLSv1.2 no-tls-tickets

defaults
	log	global
	mode	http
	option	httplog
	option	dontlognull
        timeout connect 5000
        timeout client  50000
        timeout server  50000
	errorfile 400 /etc/haproxy/errors/400.http
	errorfile 403 /etc/haproxy/errors/403.http
	errorfile 408 /etc/haproxy/errors/408.http
	errorfile 500 /etc/haproxy/errors/500.http
	errorfile 502 /etc/haproxy/errors/502.http
	errorfile 503 /etc/haproxy/errors/503.http
	errorfile 504 /etc/haproxy/errors/504.http

frontend myweb
	bind *:80
	option tcplog
	mode tcp
	default_backend web-servers
    
backend web-servers
    mode tcp
    balance roundrobin
    option tcp-check
    server web1 192.168.56.11:80 check fall 3 rise 2
    server web2 192.168.56.12:80 check fall 3 rise 2

$ vim /etc/keepalived/keepalived.conf

# define the script used to check if haproxy is still working
vrrp_script chk_haproxy {
    script “killall -0 haproxy”
    interval 2
    weight 2
}

# configuation for the virtual interface
vrrp_instance vi_1 {
    interface eth1
    state backup
    priority 100
    advert_int 2
    virtual_router_id 101
    unicast_src_ip 192.168.56.22
    unicast_peer {
        192.168.56.21
    }

    authentication {
        auth_type PASS
        auth_pass mylittlesecret 
    }

    # the virtual ip address shared between the two loadbalancers
    virtual_ipaddress {
		192.168.56.69
    }

    # use the script above to check if we should fail over
    track_script {
        chk_haproxy
    }
}

$ sudo  systemctl restart haproxy keepalived
```

သတိပြုကြည့်လိုက်ရင် haproxy မှာသုံးတဲ့ configuration file ဖြစ်တဲ့ /etc/haproxy/haproxy.cfg ဟာ ha1 နဲ့ ha2 မှာအတူတူပါပဲ။ Configuration ရဲ့ ပထမပိုင်းကတော့ haproxy ကို install လုပ်လိုက်တာနဲ့ ပါလာတဲ့ default တွေပါ။ စာရေးသူတို့ ထပ်ဖြည့်ပြီးတော့ ပေါင်းထည့်ရမယ့် configuration ကတော့ အောက်ကအတိုင်းဖြစ်ပါတယ်။

```
frontend myweb # haproxy ရဲ့ frontend အတွက်လိုအပ်တဲ့ parameters တွေပါ။ 
	bind *:80 # binding portကို frontend မှာ 80 ကိုသုံးထားပါတယ်။
	option tcplog
	mode tcp # http ဖြစ်တဲ့အတွက် tcp ကိုအသုံးပြုရပါ့မယ်။ 
	default_backend web-servers # backend section ကိုဒီမှာသတ်မှတ်ပေးရပါတယ်။ 
    
backend web-servers # haproxy ရဲ့ backend အတွက်လိုအပ်တဲ့ parametersတွေဖြစ်ပါတယ်။ 
    mode tcp
    balance roundrobin # load balancing မှာ roundrobin ကိုအသုံးပြုထားပါတယ်။ 
    option tcp-check
    server web1 192.168.56.11:80 check fall 3 rise 2
    server web2 192.168.56.12:80 check fall 3 rise 2
```

ဒီနေရာမှာ haproxy နဲ့ပတ်သတ်ပြီးတော့ အနည်းငယ် ဖြည့်စွတ်ရှင်းလင်းလိုပါတယ်။ frontend အပိုင်းမှာ ထပ်ပြီးတော့ ရှင်းပြစရာ လိုမယ်မထင်ပါ။ backend အပိုင်းမှာတော့ နှစ်ခုလောက်အပိုရှင်းပြရမယ်ထင်ပါတယ်။ Balance နေရာမှာ roundrobin ဆိုတဲ့ algorithm ကိုအသုံးပြုထားပါတယ်။ Roundrobin ဖြစ်တဲ့အတွက် haproxy ဟာ backend web server နှစ်လုံးမှာ web1 တလှည့်၊ web2 တလှည့် အလှည့်ကျ load ကိုမျှဝေထားတာဖြစ်ပါတယ်။ web1 မှာ load မနိုင်မနင်း ဖြစ်နေတာ၊ web2 မှာ idle ဖြစ်နေတာတွေ အားလုံးကို လုံးဝထည့်သွင်း စဉ်းစားခြင်းမရှိပါဘူး။ အလှည့်ကျပဲတောက်လျှောက် request ကို web1 တခါ၊ web2 တခါ သွားနေမှာဖြစ်ပါတယ်။ နောက်တခုက server web1 192.168.56.11:80 check fall 3 rise 2 နဲ့ server web2 192.168.56.12:80 check fall 3 rise 2 ဆိုတဲ့နှစ်ကြောင်းပါ။ Backend မှာ ပါဝင်မည့် web server နှစ်လုံးအတွက် health check mechanism ပါ။ Check ဆိုတာက အဆက်မပြတ် ၂စက္ကန့် ကိုတခါ health check လုပ်မယ်၊ fall 3 ဆိုတာကတော့ ၃ ခါ health check လုပ်ပြီးတော့ မအောင်မြင်ဘူးဆိုရင် အဲ့ဒီ node ကို dead လို့သတ်မှတ်လိုက်ပြီး load balancing cluster ထဲကနေဖယ်ထုတ်လိုက်ပါတယ်။ rise 2 ဆိုတာကတော့ health check အနည်းဆုံး နှစ်ခါအောင်မြင်မှ အဲ့ဒီ node ကို alive လို့ သတ်မှတ်ပြီး load balancing cluster ထဲမှာပြန်လည် ပေါင်းထည့်ပေးပါတယ်။ အဲ့ဒီလိုနည်းနဲ့ delay ကိုနည်းနိုင်သလောက်နည်းအောင်လုပ်ပါတယ်။ ဒီလောက်ဆိုရင် haproxy ပတ်သတ်တဲ့ အပိုင်းကရှင်းသွားပါပြီ။

Keepalived မှာတော့ configuration နည်းနည်းတော့ကွာခြားသွားပါတယ်။ အောက်မှာကွာခြားသွားတဲအပိုင်းလေး တွေကို ရှင်းလင်းပါ့မယ်။

```
# define the script used to check if haproxy is still working
vrrp_script chk_haproxy { # keepalived node တွေအတွက် health check script ပါ။
    script “killall -0 haproxy” # haproxy ကို dependency အနေနဲ့ထားတာပါ။
    interval 2 # ၂စက္ကန့် တခါ စစ်ခိုင်းတာပါ။
    weight 2 # ဒီ weightဆိုတာကတော့ priority မှာပေါင်းထည့်ပေးတဲ့ valueပါ။
}

# configuation for the virtual interface
vrrp_instance vi_1 {
    interface eth1
    state master
    priority 101
    advert_int 2
    virtual_router_id 101
    unicast_src_ip 192.168.56.21
    unicast_peer {
        192.168.56.22
    }

    authentication {
        auth_type PASS
        auth_pass mylittlesecret 
    }

    # the virtual ip address shared between the two loadbalancers
    virtual_ipaddress {
		192.168.56.69
    }

    # use the script above to check if we should fail over
    track_script { # keepalived အတွက်ဘယ်လိုမျိုး track လုပ်မလဲလို့ သတ်မှတ်ပေးတာပါ။
        chk_haproxy
    }
}
```

အနည်းငယ်ဖြည့်ပြီးတော့ ရှင်းချင်တာကတော့ script “killall -0 haproxy” ဆိုတဲ့အပိုင်းပါ။ Haproxy daemon ကို သတ်တဲ့ command မဟုတ်ပါဘူး။ killall -0 ဆိုတဲ့အတွက် return value ကို စစ်တဲ့သဘောပါ။ အခြားသော daemon တွေရဲ့ status ကိုစစ်ချင်ရင်လည်း သုံးတဲ့ command ပါ။ ဒီတော့ အဲ့ဒီ script ကနေ return value က zero ဖြစ်နေသရွေ့ healthy ဖြစ်နေတယ်လို့ သတ်မှတ်လို့ ရပါတယ်။ ဒါမှမဟုတ်ဘူး non-zero value ကိုပြန်ရရင်တော့ keepalived ကို failover လုပ်ခိုင်းထားပဲဖြစ်ပါတယ်။ ha1 နဲ့ ha2 မှာ node က down သွားလား ဆိုတာထက် haproxy ရဲ့ health status ကပိုပြီးတော့ အရေးကြီးပါတယ်။ ဒီ့အတွက် haproxy မှာတစ်ခုခုမှားတာနဲ့ keepalived ရဲ့ vrrp ကိုအလုပ် လုပ်ခိုင်းထားတာပါ။ ဒါမှလည်း fully HA ဖြစ်မှာပါ။ ဒီထက်ပိုပြီးတော့ ရှုပ်ထွေးတဲ့ haproxy နဲ့ keepalived တို့ကို setup လုပ်လို့ရနိုင်ပါသေးတယ်။ ကိုယ့် environment မှာဘာလိုချင်တာလဲပေါ်မှာပဲမူတည်ပါတယ်။

ဒီတခါ keepalived ကို 4 nodes နဲ့ manually setup မလုပ်ချင်ဘူးဆိုရင်တော့ အောက်က vagrantfile နဲ့ automate လုပ်လို့ရပါတယ်။

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
      subconfig.vm.provision "shell", inline: <<-Web
        sudo -i   
        apt update && sudo apt install -y apache2
        echo web#{x} > /var/www/html/index.html
        systemctl enable apache2
        systemctl start apache2
      Web
    end
  end

  (1..NODE_COUNT).each do |y|     
    config.vm.define "ha#{y}" do |subconfig|       
      subconfig.vm.box = BOX_IMAGE       
      subconfig.vm.hostname = "ha#{y}"       
      subconfig.vm.network :private_network, ip: "192.168.56.#{y + 20}"     
      subconfig.vm.provision "shell", inline: <<-Ha
        sudo -i   
        apt update && sudo apt install -y haproxy keepalived
        systemctl enable haproxy keepalived
        systemctl start haproxy keepalived
      Ha
      if (subconfig.vm.hostname=="ha1") then
        subconfig.vm.provision "file", source: "./keepalived_master.conf", destination: "~/keepalived.conf"
        subconfig.vm.provision "shell", inline: <<-S1     
          sudo cp /home/vagrant/keepalived.conf /etc/keepalived/keepalived.conf
        S1
      else
        subconfig.vm.provision "file", source: "./keepalived_backup.conf", destination: "~/keepalived.conf"
        subconfig.vm.provision "shell", inline: <<-S2
          sudo cp /home/vagrant/keepalived.conf /etc/keepalived/keepalived.conf
        S2
      end
      subconfig.vm.provision "file", source: "./haproxy.cfg", destination: "~/haproxy.cfg"
      subconfig.vm.provision "shell", inline: <<-S3
        sudo rm -f /etc/haproxy/haproxy.cfg
        sudo cp /home/vagrant/haproxy.cfg /etc/haproxy/haproxy.cfg
        systemctl restart haproxy keepalived
      S3
    end
  end 
  # copy ssh public key to the VM and update then reboot
  config.vm.provision "file", source: "./me.pub", destination: "~/.ssh/me.pub"  
  config.vm.provision "shell", inline: <<-SHELL     
    cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
 SHELL
end
```

Vagrant နဲ့ run ဖို့အတွက် လိုအပ် file တွေကိုလည်း အောက်က GitHub repo မှာတင်ပေးထားပါတယ်။

[https://github.com/tylalin/ITmatic101/tree/master/infra\_as\_code/vagrant\_files/keepalived\_4nodes](https://github.com/tylalin/ITmatic101/tree/master/infra\_as\_code/vagrant\_files/keepalived\_4nodes)

Vagrant ကို setup လုပ်ပုံနဲ့ run ပုံကို အသေးစိတ်ဖတ်ချင်ရင်တော့ အောက်က Link မှာဖတ်ပါ။

{% embed url="https://itmatic101.com/2020/12/28/rough-edges-iac-part2/" %}

အဲ့ဒီ post ကိုပဲ GitBook မှာသွားရောက်ဖတ်ရှုချင်တယ်ဆိုရင်တော့ အောက်က Link မှာသွားဖတ်လို့ရပါတယ်။

{% embed url="https://my.itmatic101.com/automation/rough-edges-iac-part2" %}

ဒီလောက်ဆိုရင် keepalived အတွက်အခြေခံကိုရပြီလို့ထင်ပါတယ်။ နောက်ပိုင်း keepalived နဲ့ ပတ်သတ်တဲ့ project အသစ်တွေရှိရင် စာရေးသူ ထပ်ပြီးတော့ မျှဝေချင်ပါသေးတယ်။ ဒီ post ကိုတော့ အခုလောက်နဲ့ပဲ အဆုံးသတ်လိုက်ပါတော့မယ်။
