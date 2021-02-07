# WireGuard အကြောင်းသိကောင်းစရာ

အရှေ့ post မှာတော့ ssh tunneling အကြောင်းကို အကျယ်တဝင့်ရှင်းပြသွားပြီးသားမို့ tunneling လုပ်နိုင်တဲ့ protocol တွေ ရိုးရှင်းသလောက် ဘယ်လောက်တောင် အလုပ်ဖြစ်သလဲဆိုတာ စာဖတ်သူတို့ သိသင့်သလောက် သိထားပြီးကြပါပြီ။ post အရမ်းရှည်သွားမှာကိုလည်း မလိုလားလို့ ssh tunneling တစ်ခုတည်းကိုသာ သီးသန့်ရှင်းလိုက်ပြီးတော့ WireGuard အကြောင်းကို အကြမ်းဖျင်း အနေနဲ့သာ အစပျိုးခဲ့ပါတယ်။ အထူးသဖြင့် Jupiter Broadcasting ရဲ့ shows တွေအကြောင်းကိုလည်း တော်တော်များများ မိတ်ဆက်ပေးခဲ့ပါတယ်။ စာရေးသူအတွက်တော့ အလုပ်သွားတဲ့ အချိန်နဲ့ အလုပ်မှာ အလုပ်နည်းနည်းပါးတဲ့ အချိန်တွေမှာတော့ podcast လေးတွေက တော်တော်လေးကို အဆင်ပြေပါတယ်။ shows မှာလာပြီးပါဝင်တဲ့ guest တွေက technical background မျိုးစုံပါတဲ့အတွက် ပြောတဲ့ topic တွေက sysadmin ကစလို့ DevOps နဲ့ storage specialist တွေအပါအဝင် core programmer၊ cloud engineer အပြင် open source က entrepreneur တွေပါ ပါဝင်တတ်တာမို့ အလွန်ကို စုံစုံလင်လင်ရှိလှပါတယ်။ စာရေးသူ WireGuard ကို စတင်တွေရှိခဲ့တာလည်း သူတို့ အမြဲပြောတတ်တဲ့ Lightweight Overlay Network တစ်ခုဆိုလို့ စိတ်ဝင်စားရာမှ လေ့လာမိတဲ့ open source က tools လေးတစ်ခုဖြစ်ပါတယ်။ ပေါ့ပါးသလောက် setup လုပ်ရတာလည်း အရမ်းကိုလွယ်ကူလှပါတယ်။ OpenVPN လိုမျိုး အဆင့်ပေါင်းများစွာ setup လုပ်စရာသိပ်မလိုပါဘူး။ စာရေးသူရဲ့ အတွေ့အကြုံအရ ဆိုရင် OpenVPN ထက် ၂ ဆ ၃ ဆ ပိုလည်းမြန်ပြီး VPN connection ရဲ့ bandwidth လည်း OpenVPN ထက် ၂ ဆ ကျော်ကျော်လောက် ပိုရပါတယ်။ စာရေးသူ iPerf3 ကိုအသုံးပြုတော့ benchmark လုပ်တာဖြစ်ပါတယ်။

### WireGuard မိတ်ဆက်

WireGuard ကို စာဖတ်သူ တချို့လည်းသိနေနှင့်ပြီးသား ဖြစ်နိုင်သလို၊ မသိသေးသူတွေလည်း အများကြီးရှိနိုင်ပါတယ်။ Open source ရဲ့ free VPN solution ဆိုလိုက်ရင်တော့ OpenVPN နဲ့ IPsec လိုမျိုး implementation တွေကိုလူသိများပါတယ်။ စာရေးသူ ကိုယ်တိုင်လည်း လက်ရှိအချိန်ထိ OpenVPN နဲ့ WireGuard ကိုတွဲပြီးတော့ အသုံးများပါတယ်။ ကိုယ်လိုချင်တဲ့ routed နဲ့ bridged setup မှာတော့ WireGuard \(wg\) ကိုအသုံးများပါတယ်။ စာရေးသူ နေ့စဥ်တိုင်းလို အသုံးပြုဖြစ်ပါတယ်။ WireGuard \(wg\) ရဲ့ ထူးခြားချက်က Linux kernel ရဲ့ module တစ်ခုအနေနဲ့ ရှိနေတာမို့ Linux OS နဲ့ တသားတည်း ဖြစ်နေတယ်လို့ ဆိုနိုင်ပါတယ်။ အဲ့ဒါကြောင့်လည်း performance ပိုင်းမှာ Linux ပေါ်မှာ run မယ်ဆိုရင် အခြားသော VPN solution တွေထက် အများကြီးသာပါတယ်။ VPN Server/Client ပုံစံမျိုးထက်၊ point-to-point လိုမျိုး setup မှာ WireGuard \(wg\) အသာစီးရပါတယ်။ အောက်မှာ configuration လုပ်တဲ့အခါ WireGuard ကဘယ်လောက်တောင် elegant ဖြစ်သလဲဆိုတာ တွေ့ပါလိမ့်မယ်။ site နှစ်ခုကို tunnel အနေနဲ့ တည်ဆောက်ဖို့ကို OpenVPN လို၊ IPsec လိုဘာမှ အများကြီးလုပ်စရာ မလိုပဲနဲ့ WireGuard ကို နှစ်ဘက်စလုံးမှာ install လုပ်ပြီးတော့ static configuration file တစ်ခုကို public key နဲ့ private key တို့နဲ့အတူ setup လုပ်ပေးလိုက်ရုံပါပဲ။ restriction တွေကိုလည်း လိုအပ်သလို ပြင်ဆင်ပြီးတော့ ထည့်သွင်းအသုံးပြုရုံပါပဲ။ အစပိုင်းမှာတော့ Linux အတွက်ပဲ ထုတ်ထားတာကနေအခုဆိုရင် platform နီးပါးတိုင်းမှာ တင်ပြီးတော့ အသုံးပြုလို့ရပါတယ်။ ဒီ post မှာတော့ စာရေးသူ အနေနဲ့ Linux platform မှာဘယ်လို အသုံးပြုသလဲဆိုတာကို ရှင်းပြပေးသွားပါ့မယ်။

### WireGuard ကို install လုပ်ပုံ

**Ubuntu ပေါ်မှာ install လုပ်နည်း**

```text
$ sudo add-apt-repository ppa:wireguard/wireguard
$ sudo apt-get update
$ sudo apt-get install wireguard -y
```

အထက်ကအတိုင်း ဆိုင်ရာ distro မှာ WireGuard ကို install လုပ်ပြီးရင်တော့ နောက်တဆင့်မှာ public key၊ private key နဲ့ wg0.conf configuration file တွေကို ဆက်ပြီးတော့ setup လုပ်ရပါ့မယ်။ ကိုယ်အသုံးပြုမယ့် node တွေအကုန်လုံးမှာ WireGuard ကို install လုပ်ရမှာဖြစ်ပါတယ်။ ဒီ post မှာတော့ စာရေးသူ Ubuntu 18.04 ကို အသုံးပြုပြီးတော့ WireGuard ကို setup လုပ်ပုံကို ရှင်းပြသွားမှာဖြစ်ပါတယ်။

### WireGuard ကို configure လုပ်ပုံ

WireGuard ကို ဘယ် Linux box မှာမဆို run လို့ရတဲ့အတွက် Linux VM သို့မဟုတ် Linux bare metal server တစ်ခုပေါ်မှာ configure လုပ်ပြီးတော့ setup လုပ်ရတာပို အဆင်ပြေပါတယ်။ အချို့သော Firewall/Router vendor အချို့မှာတော့ WireGuard ကို built-in အသုံးပြုလို့ ရအောင် အဆင်သင့် integrate လုပ်ထားတဲ့အတွက် Linux box နောက်တစ်ခုမလိုပဲနဲ့ Firewall/Router ပေါ်မှာလည်း setup လုပ်လို့ရပါတယ်။ ဒီ post မှာတော့ Linux box ကို Firewall/Router ရဲ့ အနောက်မှာ ထားပြီးတော့ setup လုပ်တဲ့ပုံစံကို ရှင်းပြသွားပါ့မယ်။ အောက်ကပုံ ကတော့ topology diagram အကြမ်းဖျင်းဖြစ်ပါတယ်။

![WireGuard Topology Diagram](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/01/WireGuard-Topology-Diagram-1024x214.png?resize=637%2C133&ssl=1)

ပုံထဲမှာတော့ ကိုယ့်အိမ်မှာ self-hosted လုပ်ထားတဲ့ Linux Server ကို WireGuard Local Node လို့ခေါ်ထားပြီးတော့ ကိုယ်အပြင်ကနေ ချိတ်ဆက်ပြီးတော့ အသုံးပြုချင်တဲ့ Laptop/PC ကို remote PC သို့မဟုတ် WireGuard Remote Node လို့ ခေါ်ထားပါတယ်။ အရှင်းဆုံးပြောမယ်ဆိုရင် WireGuard Server Node နဲ့ Client Node ဆိုပြီးမြင်မယ်ဆိုရင်လည်းရပါတယ်။ WireGuard မှာတော့ server ရယ်၊ client ရယ်လို့ မရှိပါဘူး။ ကိုယ်ကြိုက်သလို point-to-point overlay networking ပုံစံမျိုး setup လုပ်ချင်လည်းရပါတယ်။ များသောအားဖြင့် WireGuard ကိုအသုံးပြုတဲ့ ပုံစံတိုင်းမှာ တစ်ခုထက်ပိုတဲ့ remote client node တွေရှိနိုင်ပါတယ်။ WireGuard ရဲ့ architecture မှာတော့ hub-and-spoke model မျိုးကိုသာအသုံးပြုနိုင်မှာဖြစ်ပါတယ်။ Mesh overlay networking ပုံစံဖြစ်လာဖို့တော့ WireGuard project ရဲ့ Todo ထဲမှာ နောက်ပိုင်းထည့်သွားဖို့တော့ ရည်ညွန်းထားတာကိုတွေ့ရပါတယ်။ အဲ့ဒါကို အကောင်အထည် ဖော်လာဖြစ်ရင်တော့ WireGuard ကို MPLS network ပုံစံမျိုးကို home setup တွေမှာ အလွယ်တကူ အသုံးပြုလာနိုင်တော့မှာပါ။ နောက်ပြီး အရှေ့မှာပြောခဲ့သလိုပဲ WireGuard ဟာ Linux kernel ထဲမှာ ထဲထဲဝင်ဝင် integrate လုပ်ထားတဲ့အပြင် Linus Torvalds ကိုယ်တိုင် ကြိုက်နှစ်သက်လို့ Linux kernel ထဲမှာ module တစ်ခုအနေနဲ့ merge လုပ်ဖို့ ဖြစ်လာတဲ့အထိပါပဲ။ Codebase အားဖြင့် လိုင်းပေါင်း ၄၀၀၀ လောက်သာရှိပြီးတော့ ရိုးရှင်းလှတဲ့ implementation ကြောင့် အခုလို lightweight ဖြစ်ရတာလို့ စာရေးသူထင်ပါတယ်။ အကယ်လို့များကိုယ်က WireGuard ထက်ပိုပြီးတော့ ရှေ့ပြေးတဲ့ overlay networking tool ကို open source မှာ အသုံးပြုချင်တယ်ဆိုရင်တော့ နောက်ပိုင်းမှ ထွက်လာတဲ့ Nebula ဆိုတဲ့ Slack က open source လုပ်ပေးထားတဲ့ project တစ်ခုရှိပါတယ်။ Nebula ဟာအခုအချိန်ထိ စမ်းသပ်ဆဲကာလ ဖြစ်တာမို့ အချောသက်တော့ မပြီးသေးပါဘူး။ ကိုယ်ကစမ်းပြီးတော့ အသုံးပြုချင်တယ်ဆိုရင်တော့ စတင်စမ်းသပ်လို့ရပါပြီ။ စာရေးသူကိုယ်တိုင်လည်း Nebula ကိုလေ့လာဆဲ၊ စမ်းသပ်ဆဲမို့ လက်တွေမှာ အခုချပြစရာ တစ်ခုမှမရှိသေးပါဘူး။ ကိုယ်တိုင်နားလည်ပြီးရင်တော့ Nebula အတွက် post သီးသန့်တစ်ခုကို အသေးစိတ်ချပြချင်ပါတယ်။ Nebula ရဲ့ introduction ကိုတော့ ဒီ [link](https://slack.engineering/introducing-nebula-the-open-source-global-overlay-network-from-slack-884110a5579) မှာဖတ်ရှုနိုင်ပါတယ်။

WireGuard ကို setup လုပ်တဲ့ဘက်ကို ပြန်ပြီးတော့လှည့်လိုက်ရအောင်… ကိုယ့်ရဲ့ Linux box လည်း ready၊ ကိုယ့်ရဲ့ home router မှာလည်း ပုံမှာပြထားတဲ့ အတိုင်း port 51820 ကို ကိုယ့်ရဲ့ Linux box ဆီ port forward လုပ်ပြီးရင် WireGuard ကိုစတင် configure လုပ်ဖို့ပဲကျန်ပါတော့တယ်။ အောက်မှာတော့ ဘယ်လို setup လုပ်သလဲဆိုတာဆက်သွားပါ့မယ်။

**WireGuard ကို server node ပေါ်မှာ configure လုပ်ပုံ**

```text
tyla@wg-srv-node:~$ sudo -i
[sudo] password for tyla:  [Enter your sudoer password]
# Generating public and private keys under /etc/wireguard directory
root@wg-srv-node:~# cd /etc/wireguard/
root@wg-srv-node:~# wg genkey | tee privatekey | wg pubkey > publickey
# Creating wg0.conf file for WireGuard configuration
root@wg-srv-node:~# vi wg0.conf
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
root@wg-srv-node:~# wg-quick up wg0
```

**WireGuard ကို client node ပေါ်မှာ configure လုပ်ပုံ**

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

သူ့ရဲ့ configuration ကဒါပါပဲ။ ကိုယ်လုပ်တာအကုန်မှန်တယ်ဆိုရင်တော့ wg ဆိုတဲ့ command ကို prompt မှာရိုက်ထည့်လိုက်ရင် တဘက်တချက်စီမှာ ကိုယ့်ရဲ့ peer နဲ့ဆိုင်တဲ့ အချက်အလက်တွေကို တွေ့ရမှာပဲဖြစ်ပါတယ်။ နောက်ပြီး wg server နဲ့ client node ကြားမှာ 10.1.10.0 ip ကို ping ကြည့်လို့ရတယ်ဆိုရင် wireguard ရဲ့ connection က စတင် အလုပ်လုပ်ပါပြီ။ WireGuard client node ဘက်မှာ AllowedIPs ကို ကိုယ် route ချင်တဲ့ ip address သို့မဟုတ် subnet ကိုလည်း အောက်မှာလို comma နဲ့ ထက်ပြီးတော့ ပေါင်းထည့်လို့ရပါတယ်။

```text
AllowedIPs = 10.1.10.1/32, 192.168.0.0/24 
```

အထက်ကအတိုင်း ထည့်လိုက်ရင်တော့ wg server ရဲ့ IP address နဲ့၊ peer မှာရှိတဲ့ 192.168.0.0/24 ဆိုတဲ့ subnet နဲ့ကိုတာ WireGuard ရဲ့ tunnel ထဲမှာ route လုပ်မယ်လို့ပြောတာဖြစ်ပါတယ်။

နောက်တစ်ခုက… ကိုယ်က WireGuard server node ကို reboot လုပ်တိုင်း wireguard ကို system startup မှာ service တစ်ခုအနေနဲ့ autostart လုပ်ချင်တယ်ဆိုရင်တော့ အောက်ကအတိုင်း systemd ရဲ့ systemctl ကို အသုံးပြုလို့ရပါတယ်။

```text
root@wg-srv-node:~# systemctl enable wg-quick@wg0.service
```

ဒီလောက်ဆိုရင်တော့ WireGuard ကို setup လုပ်ပုံအတွက် လုံလောက်ပြီလို့ စာရေးသူထင်ပါတယ်။ WireGuard မှာ ဒီထက်ပိုပြီးတော့ လုပ်လို့ရတဲ့ဟာ အများကြီးကျန်ပါသေးတယ်။ အကုန်လိုက်ရှင်းရင် အရမ်းရှည်သွားမှာပါ။ အဲဒီတော့… ဒီ post ကို ဒီလောက်နဲ့ပဲ ရပ်လိုက်ပါတော့မယ်။

