# Wireguard ရဲ့ automated workflow

အရှေ့က post တစ်ခုမှာ Wireguard ကိုဘယ်လိုမျိုး setup လုပ်ပြီးတော့ကိုယ်အိမ်ကို အချိန်မရွေး အပြင်ကနေ  VPN ချိတ်လို့ရအောင်လို့ တခါရှင်းပြပြီးပါပြီ၊ နောက်မြန်မာနိုင်ငံမှာ နိုင်ငံရေးအခြေအနေ မကောင်းလို့စစ်အာဏာသိမ်း အစိုးရက Facebook နဲ့ အခြားသောလူသုံးများတဲ့ social media platform တွေနဲ့ Google service တွေကိုပိတ်လိုက်တဲ့ အခါမှာလည်း Linode မှာကိုယ်ပိုင်အကောင်ဖွင့်ပြီးတော့ VPS တစ်လုံးပေါ်မှာ ကိုယ်ပိုင် Wireguard VPN server တစ်ခုကို ထောင်ပြီးတော့ ကိုယ်နဲ့ ရင်းနှီးတဲ့ မိတ်ဆွေတွေ သူငယ်ချင်းတွေကို ပေးသုံးလို့ရနိုင်အောင်လို့ setup လုပ်ပုံကိုလည်း တဖန်ထပ်ရှင်းခဲ့ပါတယ်။ ကိုယ်ပိုင်အိမ်မှာရှိတဲ့ Wireguard VPN server အတွက် private key နဲ့ public key တွေကို ထိန်းသိမ်းရတာလွယ်သလောက်၊ တကယ်တမ်း Linode မှာကိုယ်တိုင် setup လုပ်တဲ့အချိန်မှာတော့ လူတွေအများကြီးအတွက် client side configuration တွေကို QR code ထုတ်တဲ့အခါ တော်တော်လေးကို လက်ဝင်လာပါတော့တယ်။ အခြားသူတွေကတော့ Wireguard configuration တွေအတွက် အများကြီးထုတ်လို့ရအောင်လို့ website တွေနဲ့ GitHub ပေါ်မှာလည်း script အချို့ကိုရှာတွေ့ပါတယ်။ ကိုယ့်အတွက်လက်တွေ့ သုံးတဲ့အခါမှာတော့ website ပေါ်မှာထုတ်တဲ့ configuration တွေကို public cloud မှာတင်ထားတဲ့ VPS မှာ configure လုပ်ဖို့အတွက် စိတ်မသန့်သလိုရှိတာနဲ့ မသုံးဖြစ်ခဲ့ပါဘူး။ နောက်ပြီးတော့ GitHub မှာတင်ထားတဲ့ customised script တွေကြတော့လည်း ကိုယ်သုံးမယ့် ပုံစံနဲ့ကွက်တိ အဆင်မပြေတာကြောင့် ကိုယ်သုံးချင်တဲ့ပုံစံအတိုင်း ကိုယ်ပိုင် script တစ်ခုရေးမယ်လို့ စဉ်းစားမိလာပါတော့တယ်။ နောက်ပြီးတော့ automated workflow အတွက်ဘယ်လိုရေးမလဲ၊ Python သုံးမလား၊ Bash မှာပဲရေးမလားဆိုတာကို ထပ်တခါစဉ်းစားကြည့်တော့ Bash ကကိုယ့်အတွက်ပိုပြီးတော့ အဆင်ပြေသလိုရှိိနေတာနဲ့ bash ကိုပဲအသုံးပြုလိုက်ပါတော့တယ်။  

## ကြိုတင်ပြင်ဆင်ထားရမယ့် အချက်များ 

ပထမဆုံးအနေနဲ့ Linode မှာ ကိုယ် setup လုပ်ထားတဲ့ Wireguard server တစ်ခုအဆင်သင့်ရှိနေရပါ့မယ်။ ပြီးတော့ အဲ့ဒီ server အတွက် wireguard ရဲ့ public နဲ့ private key pair တစ်ခုကို အရင်ဆုံး issue ထုတ်ထားရပါ့မယ်။ အသေးစိတ်လုပ်ပုံကိုတော့ ထပ်မရှင်းတော့ပါဘူး။ အရှေ့က post နှစ်ခုကို မဖတ်ရသေးရင်တော့ အောက်မှာတချက်အရင်သွားဖတ်လို့ရပါတယ်။ 

**Wireguard အကြောင်းသိကောင်းစရာ**

{% embed url="https://my.itmatic101.com/networking/wireguard-intro" %}

**Linode VPS မှာကိုယ်ပိုင် Wireguard VPN server တစ်ခုတည်ဆောက်ပုံ**

{% embed url="https://my.itmatic101.com/networking/linode-vps-wireguard-vpn" %}

အပေါ်က link နှစ်ခုမှာ Wireguard server အတွက် private နဲ့ public key pair ကိုပြင်ဆင်တဲ့ပုံနဲ့ လိုအပ်တဲ့ firewall setting နဲ့ ip forwarding ကို enable လုပ်ပြီးသွားရင် ကျန်တဲ့ client side အတွက် Wireguard configuration နဲ့ ဖုန်းမှာသုံးဖို့အတွက် QR code တွေအများကြီးထုတ်ဖို့ရာအတွက် workflow ကို automate လုပ်လို့ရပါပြီ။ နောက်ပြီးတော့ qrencode ဆိုတဲ့ command ကိုအသုံးပြုဖို့အတွက် သူ့ကိုလည်းအရင်ဆုံး ကြိုပြီးတော့ ကိုယ့်ရဲ့ PC သို့မဟုတ် laptop မှာကြိုပြီးတော့ install လုပ်ရပါလိမ့်မယ်။ ကိုယ်သုံးတဲ့ OS က Linux ဖြစ်ဖို့တော့လိုပါလိမ့်မယ်။ စာရေးသူအတွက်တော့ Ubuntu 20.04 LTS ကို GNOME Desktop နဲ့သုံးပါတယ်။ ဒီနေရာမှာ နှစ်မျိုးလုပ်လို့ရပါတယ်။ အခုသုံးမယ့် bash script ကို ကိုယ့်ရဲ့စက်မှာ wireguard နဲ့ qrencode အရင်သွင်းထားပြီးတော့ လိုအပ်တဲ့ client side QR code တွေကို ကိုယ့်စက်ပေါ်မှာ locally တစ်ခုပြီးတော့ တစ်ခုထုတ်လို့ရပါတယ်။ User တွေအများကြီးအတွက် ထုတ်တဲ့အခါမှာ အများကြီးလွယ်ကူသွားတာကိုတွေ့ရပါလိမ့်မယ်။ မျက်စိထဲမြင်အောင်လို့ Wireguard server ပေါ်မှာ /etc/wireguard/wg0.conf ကို configure လုပ်ပုံကို နောက်တခါထပ်ပြီးတော့ ပြပေးထားပါတယ်။ ဒီတစ်ခုမှာ သတိထားရမှာက wg0 ရဲ့ interface မှာ assign လုပ်မယ့် IP address ရဲ့ scope နဲ့ client ဘက်မှာသုံးမယ့် IP address ဟာ subnet တစ်ခုတည်းမှာရှိနေဖို့ လိုပါတယ်။ နောက်ပြီးတော့... PostUp နဲ့ PostDown လိုင်းနှစ်ခုမှာ ကိုယ့်ရဲ့ Linux distro ပေါ်မှာမူတည်ပြီးတော့ NIC နာမည် အနည်းငယ်ကွာခြားနိုင်ပါတယ်။ ဥပမာ ဒီတစ်ခုမှာတော့ စာရေးသူ eth0 နဲ့ သုံးပြီးတော့ပြထားပါတယ်။ အချို့သော VPS တွေမှာတော့ ens3 ဆိုပြီးတော့ဖြစ်နေတတ်ပါတယ်။ ဘယ်လို verify လုပ်နိုင်သလဲဆိုရင် terminal ထဲမှာ "ip address" ရိုက်ထည့်လိုက်ရင် NIC ရဲ့ နာမည်ကို သူ့ရဲ့ ip address နဲ့အတူတွေ့မြင်နိုင်မှာဖြစ်ပါတယ်။ ဒီ wireguard server မှာတော့ public cloud တစ်ခုမှာ VPS တစ်ခုကို ပြင်ဆင်ပြီးတော့ wg0 interface ကလာသမျှ traffic ကို VPS ရဲ့ public ip address နဲ့ထွက်စေချင်တာဖြစ်တဲ့ sysctl မှာ ip forwarding ကို enable လုပ်ရပါ့မယ်၊ MASQUERADE ဆိုတာကတော့ NAT overload လုပ်မယ်လို့ iptable အတွက် configure လုပ်ရတာပါ။ PrivateKey ဆိုတာကတော့ အထက်မှာတုန်းက wireguard server အတွက် public/private key pair ကို generate လုပ်တုန်းကထွက်လာတဲ့ private key ကိုဒီမှာလာထည့်ရတာပါ။ Public key ကို အနောက်မှာ client side အတွက် configuration တွေကိုထုတ်တဲ့အခါမှာ bash script ထဲမှာ အသေထည့်သုံးရုံပါပဲ။ 

{% code title="wg0.conf" %}
```bash
[Interface]
Address = 192.168.240.1/32
PostUp = iptables -A FORWARD -i %i -j ACCEPT; iptables -A FORWARD -o %i -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
PostDown = iptables -D FORWARD -i %i -j ACCEPT; iptables -D FORWARD -o %i -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE
ListenPort = 51820
PrivateKey = cN4ITN3S0mS9I0Zkd6/44iqumCjszudM034XMVWllFE=
```
{% endcode %}

အောက်မှာ bash နဲ့လုပ်ထားတဲ့ automated workflow တစ်ခုကို အရင်ဆုံးကြည့်လိုက်ရအောင်ဗျာ။ 

{% code title="wg-config-gen.sh" %}
```bash
#!/bin/bash

p='wg-srv-peers.conf'
[ -f $p ] && rm -f $p

i='PNGs'
[ -d $i ] && rm -rf $i
mkdir $i

while IFS=, read -r ui ip
do
    echo "$ui and $ip"
    [ -d "$ui" ] && rm -rf $ui
    mkdir $ui && cd $ui
    wg genkey | tee $ui.key | wg pubkey | tee $ui.key.pub > /dev/null
    key=`cat $ui.key`
    pubkey=`cat $ui.key.pub`

echo "[Interface]
PrivateKey = $key
Address = $ip
DNS = 8.8.8.8, 8.8.4.4 
[Peer]
PublicKey = Ccd+Z/JBwktqy3i2wIfb+rwX9h0w4BO/fghOd7AcxFE=
AllowedIPs = 0.0.0.0/0
Endpoint = 11.22.33.44:51820
PersistentKeepalive = 25" >> $ui.conf

    qrencode -o $ui.png -t png < $ui.conf
    cp $ui.png ../$i/
    cd - > /dev/null

echo "[Peer]
# $ui wg
PublicKey = $pubkey
AllowedIPs = $ip/32
" >> $p

done < users-list.csv
```
{% endcode %}

အထက်မှာပြထားတဲ့ bash ထဲမှာအဆင့်ဆင့်လုပ်ထားတဲ့ command တွေကိုတစ်ခုချင်းစီသွားလိုက်ကြည့်လိုက်ရအောင်။ p ဆိုတဲ့ variable တစ်ခုကိုတည်ဆောက်ပြီးတော့ 'wg-srv-peers.conf' ဆိုတဲ့ string တစ်ခုကို assign လုပ်ထားလိုက်ပါတယ်။ အဲ့ဒါက filename ပါ။ \[ -f $p \] && rm -f $p ဆိုတာကတော့ လက်ရှိ directory မှာ အဲ့ဒီ $p ဆိုတဲ့ filename နဲ့ -f ဆိုတာ file ရှိသလားလို့ စစ်ကြည့်ခိုင်းတဲ့ conditional statement တစ််ခုပါ။ ပြီးတော့ အနောက်မှာ && rm -f $p ဆိုတာက အဲ့ဒီ file ရှိခဲ့ရင် အရင်ဆုံးဖျက်ဆီး ပစ်လိုက်လို့ပြောတာပါ။ ဘာဖြစ်လို့လဲဆိုရင် ဒီ bash file ကိုတစ်ခါ run တိုင်း file ကိုအသစ်ပြန်လည်တည်ဆောက်ပြီးတော့ wireguard server ရဲ့ peers အသစ်တွေနဲ့ပဲ ဖန်တီးချင်လို့ပါ။ အဲ့လိုမှာမဟုတ်ရင်... bash ရဲ့ runtime မှာ filename နဲ့လက်ရှိ directory ထဲမှာရှိပြီးသားမို့ overwrite လုပ်မလားဆိုပြီးတော့ မေးလို့ workflow ကသိပ်ပြီးတော့ အဆင်ပြေမနေပါဘူး။ ထိုနည်းတူပဲ i ဆိုတဲ့ variable ကိုတည်ဆောက်ပြီးတော့ PNGs ဆိုတဲ့ string ကို assign လုပ်လိုက်ပါတယ်။ ဒါကတော့ folder ရဲ့နာမည်ပါ။ syntax ကတော့ အပေါ်ကပုံစံအတိုင်းပါပဲ။ -f အစား -d ဆိုတာကတော့ directory ကိုဆိုလိုခြင်းဖြစ်ပါတယ်။ 

နောက်တစ်ခုက while loop ကိုအရင်ဆုံးတချက်ကြည့်လိုက်ရအောင်။ အောက်မှာမြင်ရတဲ့အတိုင်း while loop ရဲ့ အစနဲ့ အဆုံးကို အရင်ဆုံးသွားလိုက်ပါ့မယ်။ while IFS=, read -r ui ip ဆိုတာ while loop နဲ့လှည့်ပြီးတော့ done &lt; users-list.csv ဆိုတဲ့အတိုင်း users-list.csv file ထဲမှာရှိတဲ့ content တွေကိုဖတ်လိုက်မယ်ပြီးရင် variable ui နဲ့ ip အနေနဲ့ ရတဲ့ value တွေကို သိမ်းဆည်းထားမယ်လို့ပြောတာပါ။ IFS ဆိုတာကတော့ Input Field Separator ဆိုတဲ့ delimiter ကို ' , ' ပါလို့ bash ကိုပြောတာပါ။ csv file မှာက column တွေကို comma တွေနဲ့ ခွဲထားတာဖြစ်တဲ့အတွက် ဘာလို delimiter ကိုကြည့်ပြီးတော့ ဖတ်ရမလဲဆိုတာကို ပြောတာပါ။ read -r ဆိုတာကတော့ read တဲ့အခါမှာလည်း backslash \(\\) ကိုပါ string အနေနဲ့ဖတ်ဖို့ပြောတာပါ။ အဲ့လိုမှမဟုတ်ရင်တော့ escape character အနေနဲ့ bash ကဖတ်ပါလိမ့်မယ်။ 

```bash
while IFS=, read -r ui ip
do
    ...
done < users-list.csv
```



အောက်မှာတော့ wg-config-gen.sh ကို run ပြီးသွားရင်တွေ့ နိုင်တဲ့ folder structure တည်ဆောက်ပုံပဲဖြစ်ပါတယ်။ 

```bash
wg_automated_workflow
├── john
│   ├── john.conf
│   ├── john.key
│   ├── john.key.pub
│   └── john.png
├── PNGs
│   ├── john.png
│   ├── smith.png
│   └── tyla.png
├── smith
│   ├── smith.conf
│   ├── smith.key
│   ├── smith.key.pub
│   └── smith.png
├── tyla
│   ├── tyla.conf
│   ├── tyla.key
│   ├── tyla.key.pub
│   └── tyla.png
├── users-list.csv
├── wg-config-gen.sh
├── wg-srv-peers.conf
└── wg-srv-side-config-example.txt
```

