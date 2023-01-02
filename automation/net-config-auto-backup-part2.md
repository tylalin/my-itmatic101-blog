---
cover: ../.gitbook/assets/FileZilla-ftp-tftp.png
coverY: 0
---

# FTP/TFTP server ပေါ်မှာ network config တွေကို auto backup လုပ်ပုံ – အပိုင်း (၂)

အရှေ့တပိုင်းမှာတော့ လိုအပ်တဲ့ FTP/TFTP server အတွက်အားလုံးပြင်ဆင်ပြီးသွားပါပြီ။ ဒီ post မှာတော့ network device အမျိုးမျိုးမှာ ဘယ်လိုမျိုး auto config backup အတွက် trigger တွေကို ဖန်တီးနိုင်သလဲ ဆိုတာ ကိုဆက်ပြီးတော့ ရှင်းပြသွားပါ့မယ်။ ပထမပိုင်းမှာ စာရေးသူ ပြောတဲ့အတိုင်း အလုပ်မှာက multi-vendors networking device တွေကို အသုံးပြုထားတဲ့အတွက် တစ်ခုချင်းစီမှာဘယ်လိုမျိုး built-in features တွေကို အသုံးပြုသလဲဆိုတာကို ရှင်းပါ့မယ်။ အသုံးပြုထားတဲ့ networking device vendors နဲ့ သက်ဆိုင်ရာ OS တွေကတော့ Cisco IOS XE၊ Huawei VRP၊ HPE ProCurve၊ FortiGate နဲ့ MikroTik RouterOS တို့ပဲဖြစ်ပါတယ်။ Cisco ကိုတော့ အားလုံးသိထားတဲ့အတိုင်း လူတော်တော်များများ ကျွမ်းကျင်စွာ အသုံးပြုတတ်ပါတယ်။ အဓိက အားဖြင့်တော့ Cisco ရဲ့training နဲ့ certification တွေဟာ consumer-marketing အတွက်တော့ တော်တော်အားကြီးတဲ့ လွှမ်းမိုးမှု တစ်ခုလို့ဆိုရမှာပါ။ စာရေးသူ အတွက်တော့ Cisco ဟာ networking ဘက်မှာ အင်အားကြီးလွန်းပြီးတော့၊ ဈေးလည်းအလွန်ကြီးတဲ့ product တစ်ခုအနေနဲ့ မြင်ပါတယ်။ နောက်ပြီးတော့ Cisco ဟာ Microsoft လိုပဲ အလွန်ရှုပ် ထွေးတဲ့ licensing model ရှိတဲ့ အတွက်တခါတခါ အဲ့ဒီ licensing ကိုနားလည်ဖို့ကိုပဲ တော်တော်လေးအချိန်ယူရပါတယ်။ စာရေးသူအတွက်တော့ licensing ဆိုတာ vendor အတွက် အကျိုးအမြတ်ရှိပြီး consumer အတွက်တော့ မလိုအပ်ပဲ ကုန်တဲ့ အချိန်နဲ့ ပိုက်ဆံတွေလို့တာ မြင်ပါတယ်။ ရေဘူရအားဖြင့်တော့ HPE ProCurve နဲ့ Huawei VRP platform တွေမှာ hardware ကိုဝယ်လိုက်တာနဲ့ သူနဲ့ ပါလာတဲ့ feature တွေအကုန်လုံးကို ယူပြီးတော့ အသုံးပြုလို့ရပါတယ်။ ဘာ DNA essentials တို့၊ DNA advantage တို့လို license ကိုထက်ပြီးတော့ ထည့်စရာမလိုပါဘူး။ Cisco မှာတော့ လိုအပ်တဲ့ license မရှိရင် hardware က support လုပ်သော်လည်း အချို့ feature တွေကို အသုံးပြုလို့ မရပါဘူး။ Licensing နဲ့ subscription မှာပဲ တော်တော်လေးကို အကုန်အကျများနေပါပြီ။

အခုနောက်ပိုင်း networking industry ထဲမှာ Huawei ကိုတော်တော်လေး တွင်တွင်ကျယ်ကျယ် အသုံးပြုနေကြပါပြီ။ သူကတော့ အခြား vendor တွေနဲ့ယှဥ်လိုက်ရင် ဈေးလည်းသိပ်မကြီး သလို၊ feature တော်တော်များများကို ဘာ licensing မှမလိုပဲ အသုံးပြုလို့ရပါတယ်။ အချို့အပိုင်းတွေမှာ Cisco ထက်တောင် stable ဖြစ်နေလို့ အံ့အားသင့်ရပါတယ်။ CLI မှာအသုံးပြုတဲ့ command တွေအနေနဲ့တော့ Cisco နဲ့ တော်တော်လေးကွာခြားမှုရှိပြီးတော့၊ H3C နဲ့ HPE platform မှာအသုံးပြုတဲ့ command တွေနဲ့ ထပ်တူနီးပါး တူညီပါတယ်။ အချို့ကတော့ Huawei က OS ကို H3C နဲ့ HPE တို့စီကနေကူးချထားတာလို့လည်း ဆိုပါတယ်။ ဘယ်လိုပဲဖြစ်ဖြစ် stable ဖြစ်ပြီးတော့၊ ဈေးလည်းအများကြီးပေါလို့ Huawei နောက်ပိုင်းမှာ Enterprise နဲ့ နိုင်ငံတော်တော်များများရဲ့ government infrastructure တွေမှာအသုံးပြုလို့ နေပါပြီ။ HPE နဲ့ Dell ကတော့ အခုနောက်ပိုင်း networking ဘက်မှာ တော်တော်လေးကို invest လုပ်လာတာကိုလည်းတွေ့ရပါတယ်။ market ထဲမှာတော့ Cisco ကတော့ အခုချိန်ထိ ထိပ်ဆုံးမှာ ရှိနေတုန်းဆိုတာကိုတော့ ဘယ်သူမှငြင်းလို့မရပါဘူး။

Cisco၊ Huawei နဲ့ HPE တို့အပြင် အလုပ်မှာသုံးတဲ့ vendor နောက်တစ်ခုက MikroTik ပဲဖြစ်ပါတယ်။ အခြားသော networking OS တွေလိုပဲ MikroTik ရဲ့ RouterOS ကလည်း Linux ပေါ်မှာပဲ အခြေခံပြီးတော့ ရေးထားတာဖြစ်ပါတယ်။ သူကတော့ Latvia ဆိုတဲ့ Eastern European နိုင်ငံတစ်ခုကနေ ထုတ်တာဖြစ်ပြီးတော့ feature တော်တော်များများကို device သေးသေးလေးနဲ့ အကုန် support လုပ်လို့ developing countries တွေမှာ အသုံးများပါတယ်။ Ubiquiti လောက် အမြင်အားဖြင့် မခမ်းနားသော်လည်း၊ သူ့ဟာနဲ့သူတော့ အလုပ်ဖြစ်ပြီး ဈေးပေါတဲ့ platform တစ်ခုပါ။ အချို့သော ISP တွေမှာ MikroTik ကို core network အနေနဲ့ အသုံးပြုထားတာကိုလည်းတွေ့ရပါတယ်။ သေချာတာတစ်ခုကတော့ stable ဖြစ်တဲ့ network environment ကိုတော့ရမှာ မဟုတ်ပါဘူး။ MikroTik ကို edge သို့မဟုတ် CPE အနေလောက်နဲ့တာ အသုံးပြုသင့်ပြီးတော့၊ core network မှာတော့ sidekick အနေနဲ့ အရေးသိပ်ပြီးတော့ မကြီးတဲ့ feature အချို့ကိုပဲ ယူပြီးတော့ သုံးသင့်ပါတယ်။ Edge အနေနဲ့ အသုံးပြုမယ်ဆိုရင်တောင် MikroTik ကို enterprise လိုအရေးကြီးတဲ့ customer တွေအတွက် အသုံးမပြုရင်တော့ ပိုပြီးတော့ စိတ်ချရပါမယ်။ သို့သော် MikroTik ရဲ့ RouterBOARD နဲ့ RouterOS ကတော့ အလွန် အစွမ်းထက်လို့ Mighty MikroTik လို့ စာရေးသူ အလုပ်မှာ စနောက်ပြီးတော့ ပြောလေ့ရှိပါတယ်။

Firewall နဲ့ security appliance အနေနဲ့တော့ FortiGate ကို အသုံးပြုလို့ သူ့အတွက်လည်း script ကိုရှာကြံပြီးတော့ research လုပ်ရပြန်ပါတယ်။ CLI ကတော့ အထက်မှာပြောသွားတဲ့ product တွေနဲ့ ထပ်ပြီးတော့ လုံးဝကွဲထွက်သွားပြန်ပါတယ်။ Fortinet ရဲ့ OS ကလည်း ထုံးစံအတိုင်း Linux ကိုအခြေခံထားလို့ concept အရတော့ သဘောပေါက်ရလွယ်ပါတယ်။ နောက်ပိုင်း security ဘက်မှာ တော်တော်လေးကို Fortinet ထိုးဖောက်လာတာကိုတွေ့ရပါတယ်။ SD-WAN အတွက်လည်း FortiGate မှာ feature တွေပါပြီးတော့ Cisco နဲ့ Meraki တို့ရဲ့ SD-WAN solution တွေလောက်တော့ ဈေးမကြီးပါဘူး။ စာရေးသူ အသုံးပြုသလောက်တော့ ဘာပြဿနာ ထွေထွေထူးထူး မရှိလို့ မဆိုးဘူးလို့ ဆိုရမှာပါ။ စိတ်တိုင်းအကျဆုံးထဲမှာတော့ FortiGate မပါ ပါဘူး။ သို့သော် Enterprise အတွက်တော့ stable ဖြစ်တဲ့ platform တစ်ခုပါ။ Data Centre တွေထဲမှာ အခုနောက်ပိုင်း FortiGate ကိုတော်တော်လေး အသုံးပြုလာတာကိုလည်း စာရေးသူ တွေ့ရပါတယ်။

ကဲ… ပထမဆုံးအနေနဲ့ Cisco ရဲ့ IOS XE device တွေမှာ auto config backup အတွက်ဘယ်လို configure လုပ်သလဲဆိုတာနဲ့ syntax ကို အတိုချုပ်ပြီးတော့ ရှင်းသွားပါ့မယ်။

**Cisco IOS XE မှာ configure လုပ်ပုံ**

```
!
!
! # get into global configuration mode
conf t
! 
! 
! # configure ftp username and password 
ip ftp username gnu-ftp01
ip ftp password Passw0rd!23
!
!
! # if loopback interface is used as management network, configure the following
ip tftp source-interface Loopback0
ip ftp source-interface Loopback0
!
!
! # define archive path with its hostname and current timestamp 
! # write-memory is to trigger ftp backup whenever wr command input
! # time-period is to trigger ftp backup every week (1440 minutes = 1 day)
archive
 path ftp://192.168.105.10/$h-$t
 write-memory
 time-period 1440
!
!
```

အထက်က configuration ကတော့ Cisco IOS တွေမှာ အသုံးပြုလို့ရတဲ့ commands တွေပါ။ ပထမတပိုင်းကတော့ ftp username နဲ့ password ကိုအရင်းဆုံး configure လုပ်ပေးရပါ့မယ်။ ပြီးရင်တော့ ip tftp/ftp source-interface loopback0 ဆိုတာ လိုအပ်မှထည့်ဖို့လိုပါတယ်။ များသောအားဖြင့် တော့မလိုပါဘူး။ အလုပ်က network မှာတော့ VRF ကိုအသုံးပြုလို့ အဲ့ဒီ statement ကထည့်ဖို့လိုပါတယ်။ နောက်ဆုံးတပိုင်းမှာတော့ archive ဆိုတာ auto config backup ကို trigger လုပ်မယ့် အပိုင်းဖြစ်ပါတယ်။ အဲ့ဒီ archive အောက်မှာ path ftp://192.168.105.10/$h-$t ဆိုပြီးတော့ ftp server ကို ထောက်ပေးရပါ့မယ်။ $h ဆိုတာကတော့ device ရဲ့ hostname ကို filename မှာထည့်ချင်လို့ အသုံးပြုတဲ့ variable တစ်ခုဖြစ်ပါတယ်။ $t ဆိုတာကတော့ file ကို backup လုပ်တဲ့ timestamp အတွက်ဖြစ်ပါတယ်။ write-memory ဆိုတာကတော့ Cisco IOS XE ရဲ့ CLI မှာ write-memory သို့မဟုတ် copy running-config startup-config ကို ရိုက်ထည့်တိုင်းမှာ running-config ကို ftp server ပေါ်မှာသွားပြီးတော့ auto backup လုပ်မှာဖြစ်ပါတယ်။ time-period 1440 ဆိုတာကတော့ archive trigger ရဲ့interval ကို 1440 minutes ဆိုပြီးသတ်မှတ်ပေးတာ ဖြစ်ပါတယ်။ တရက်ကို တခါ အနည်းဆုံးတော့ တစ်ခါ backup လုပ်ချင်လို့ဖြစ်ပါတယ်။

**Huawei VRP မှာ configure လုပ်ပုံ**

```
# get into system-view which is equivalent of configure terminal in Cisco
system-view

# configure all ftp related settings for saving configuration
set save-configuration backup-to-server server 192.168.105.10 transport-type ftp user gnu-ftp01 password Passw0rd!23

# set interval for save-configuration
set save-configuration interval 1440 delay 2 cpu-limit 60
```

Huawei မှာတော့ နည်းနည်းပိုရှင်းပါတယ်။ ပထမဆုံး ftp နဲ့ ပတ်သတ်တဲ့ server IP address၊ ftp username နဲ့ ftp password ကို အရင်ဆုံး configure လုပ်ရပါ့မယ်။ ပြီးတော့မှ save-configuration အတွက် 1440 minutes ကို interval အနေနဲ့ သတ်မှတ်ပေးလိုက်ပါတယ်။ delay 2 နဲ့ cpu-limit 60 ဆိုတာကတော့ Huawei VRP မှာ တခါတခါ CPU ဟာ highly utilised ဖြစ်နေရင် ftp process ကို အနှောက်အယှက်ဖြစ်တတ်ပါတယ်။ အဲ့ဒါကြောင့် ၂ စက္ကန့် စောင့်ခိုင်းပြီးတော့ CPU utilisation ဟာ အများဆုံး ၆၀ ရာခိုင်နှုန်း အတွင်းမှာရှိမှ trigger လုပ်ပါလို့ သတ်မှတ်တာဖြစ်ပါတယ်။

**HPE ProCurve မှာ configure လုပ်ပုံ**

```
# get into system-view which is equivalent of configure terminal in Cisco
system-view

# create a job called save and its commands sequence
scheduler job save
command 1 save safely force

# create a job called tftp and its commands sequence
scheduler job tftp
command 1 tftp 192.168.105.10 put flash:/startup.cfg gnu-ce01.cfg source interface LoopBack 0

# create a schedule called save to trigger job save with its interval 
scheduler schedule save
job save
time repeating interval 1440
quit

# create a schedule called tftp to trigger job tftp with its interval  
scheduler schedule tftp
job tftp
time repeating interval 1445
quit
```

HPE ProCurve မှာကြတော့ နည်းနည်းလေး ကွာခြားသွားပြန်ပါတယ်။ ftp ကို scheduler နဲ့ တွဲပြီး အသုံးပြုဖို့အတွက် အခက်အခဲ အနည်းငယ်ရှိနေလို့ tftp ကိုပဲ အသုံးပြုထားပါတယ်။ ကျန်တဲ့ syntax ကတော့ နားလည်ရလွယ်မယ်လို့ ထင်တဲ့အတွက် အသေးစိတ်မရှင်းတော့ပါဘူး။

**MikroTik RouterOS မှာ configure လုပ်ပုံ**

```
# create a scheduler called AutoFTPBackupConfig
/system scheduler
add interval=1d name=AutoFTPBackupConfig on-event=AutoFTPBackupConfig policy=\
    ftp,reboot,read,write,policy,test,password,sniff,sensitive,romon \
    start-date=dec/25/2019 start-time=23:00:00

# create a script called AutoFTPBackupConfig to auto backup the device config	
/system script
add name=AutoFTPBackupConfig owner=dnxadm policy=\
    ftp,reboot,read,write,policy,test,password,sniff,sensitive,romon source="#\
    \_ftp server\r\
    \n# configure ftp server, username and password\r\
    \n :local ftphost \"192.168.105.10\"\r\
    \n :local ftpuser \"gnu-ftp01\"\r\
    \n :local ftppassword \"Passw0rd!23\"\r\
    \n\r\
    \n# get the current date and time\r\
    \n:local GDate [/system clock get date]\r\
    \n:local GDay [ :pick \$GDate 4 6 ]\r\
    \n:local GMonth [ :pick \$GDate 0 3 ]\r\
    \n:local GYear [ :pick \$GDate 7 11 ]\r\
    \n:local GTime [/system clock get time]\r\
    \n:local GResult \"\$GDay-\$GMonth-\$GYear-\$GTime\"\r\
    \n\r\
    \n\r\
    \n# format the file name for config export\r\
    \n:local ExportConf ([/system identity get name].\".rsc\")\r\
    \n:log info \$ExportConf\r\
    \n\r\
    \n# backup the existing configuration\r\
    \n/export compact file=\$ExportConf\r\
    \n:log info message=\"Config export finished.\"\r\
    \n\r\
    \n# upload the configuration to ftp server\r\
    \n:log info message=\"Uploading config export.\"\r\
    \n/tool fetch address=\"\$ftphost\" src-path=\$ExportConf user=\"\$ftpuser\
    \" mode=ftp password=\"\$ftppassword\" dst-path=\"\$GResult-\$ExportConf\"\
    \_upload=yes\r\
    \n\r\
    \n# delay 3 seconds to trigger the upload\r\
    \n:delay 3s;\r\
    \n\r\
    \n# feedback the user if it is completed successfully\r\
    \n:log info message=\"Configuration backup finished.\";"
```

ဒါကတော့ MikroTik မှာ scheduler တစ်ခု နဲ့ script တစ်ခု ဖန်တီးတဲ့ ပုံစံဖြစ်ပါတယ်။ CLI မှာ အသုံးပြုလို့ရတဲ့ commands sequence တွေကို ဖော်ပြပေးထားတာပါ။ Winbox ကို အသုံးပြုပြီးတော့ GUI သုံးမယ်ဆိုရင် တော့ အောက်က script ကို ထည့်သွင်းအသုံးပြုလို့ရပါတယ်။ Syntax နဲ့ command အသေးစိတ်ကိုတော့ MikroTik အတွက် မရှင်းတော့ပါ။ လုပ်ငန်းစဥ်ကတော့ အထက်က device တွေမှာလိုပဲ နေ့တိုင်း config backup လုပ်မယ်လို့ scheduler မှာသတ်မှတ်ပေးထားတာပဲဖြစ်ပါတယ်။ Script မှာ filename ကို ကိုယ်လိုချင်တဲ့ ပုံစံထွက်အောင်လို့ လုပ်ရင်းနဲ့ အနည်းရှည်သွားတာပဲဖြစ်ပါတယ်။

```
# configure ftp server, username and password
 :local ftphost "192.168.105.10"
 :local ftpuser "gnu-ftp01"
 :local ftppassword "Passw0rd!23"

# get the current date and time
:local GDate [/system clock get date]
:local GDay [ :pick $GDate 4 6 ]
:local GMonth [ :pick $GDate 0 3 ]
:local GYear [ :pick $GDate 7 11 ]
:local GTime [/system clock get time]
:local GResult "$GDay-$GMonth-$GYear-$GTime"

# format the file name for config export
:local ExportConf ([/system identity get name].".rsc")
:log info $ExportConf

# backup the existing configuration
/export compact file=$ExportConf
:log info message="Config export finished."

# upload the configuration to ftp server
:log info message="Uploading config export."
/tool fetch address="$ftphost" src-path=$ExportConf user="$ftpuser" mode=ftp password="$ftppassword" dst-path="$GResult-$ExportConf" upload=yes

# delay 3 seconds to trigger the upload
:delay 3s;

# feedback the user if it is completed successfully
:log info message="Configuration backup finished.";
```

**FortiGate မှာ configure လုပ်ပုံ**

```
# configure an auto-script to trigger a config backup file to ftp
config system auto-script 
    edit "backup" 
        set interval 86400
        set repeat 0 
        set start auto 
        set script " 
            config global 
            execute backup config ftp fw01.conf 192.168.105.10 gnu-ftp01 Passw0rd!23"
    next 
end
```

FortiGate မှာတော့ interval ကို 86400 seconds (တနည်းအားဖြစ် ရက်တိုင်း) ဆိုပြီးတော့ သတ်မှတ်ပေးလိုက်ပါတယ်။ MikroTik နည်းတူ script ရေးပြီးတော့ schedule လုပ်ပေးလိုက်ရုံပါပဲ။ ဒီတစ်ခုကိုလည်း syntax နဲ့ command ကို အသေးစိတ်မရှင်းလိုတော့ပါ။ Post အရမ်းရှည်သွားမှာကိုလည်း စိုးရိမ်လို့ပါ။ syntax နဲ့ commands တွေကို ကျွမ်းကျင်မှုကတော့ ကိုယ်ဘယ်လောက် သိချင်သလဲဆိုတာ ပေါ်မူတည်ပြီးတော့ လေ့လာရင်း တတ်ကျွမ်းလာနိုင်ပါတယ်။ အရမ်းခက်တဲ့ အရာတော့မဟုတ်ပါဘူး။ ဆိုလိုချင်တာက routing protocol တွေနဲ့ switching ရဲ့ အလုပ်လုပ်ပုံကို သိတာနဲ့ အဲ့ဒီ routing protocol နဲ့ switching commands တွေကို မှတ်မိတာ သိတာနဲ့ မတူပါဘူး။ အဲ့ဒါတွေဘယ်လို အလုပ်လုပ်သလဲ ဆိုတာသိပြီးတော့ ဘယ် commands တွေကို မှန်မှန်ကန်ကန် အသုံးပြုရသလဲဆိုတာကို သိမှတာ အသိပညာ အတတ်ပညာရယ်လို့ ခေါ်ရမှာ ဖြစ်ပါတယ်။ အဲ့ဒီ အချက်ကို သေသေချာချာနားလည်ဖို့တော့ လိုပါလိမ့်မယ်။ နောက်မို့ဆိုရင် ခရီးသိပ်ရောက်မှာမဟုတ်ပါဘူး။

နောက်ဆုံးအနေနဲ့ အထက်မှာရှင်းပြသလို backup လုပ်ထားတဲ့ config file တွေကို ဘယ်လို housekeeping လုပ်သလဲဆိုတာ အချပ်ပိုအနေနဲ့ နည်းနည်းရှင်းလိုပါတယ်။ အောက်မှာတော့ housekeeping.sh ဆိုတဲ့ bash script မှာပါတဲ့ commands sequence တွေပဲဖြစ်ပါတယ်။ အဲ့ဒီ script ကို မ run ခင်တော့ root directory မှာ အောက်က diretories တွေကို အရင်ဆုံး တည်ဆောက်ရပါ့မယ်။

```
# create required directories at root
root@rpm-dev02:~# mkdir -p /configs/cisco /configs/hpe /configs/huawei /configs/mikrotik /configs/fortigate

# create a bash script called housekeeping.sh
root@rpm-dev02:~# vi /opt/scripts/housekeeping.sh

#!/bin/bash

# Cisco IOS XE
# archive all cisco daily config backup into /configs/cisco/ 
mv /home/gnu-ftp01/[a-z]*[0-9] /configs/cisco/ 2> /dev/null

# HPE ProCurve
# archive all hpe daily config backup into /configs/hpe/ 
mv /tftproot/*.cfg /configs/hpe/ 2> /dev/null
# rename the file with current date
cd /configs/hpe/ 2> /dev/null
mv gnu-ce01.cfg gnu-ce01-$(date +'%Y%m%d').cfg 2> /dev/null

# Huawei VRP
# archive all huawei daily config backup into /configs/huawei/ 
mv /home/gnu-ftp01/[0-9]*.zip /configs/huawei/ 2> /dev/null

# MikroTik RouterOS
# archive all mikrotik daily config backup into /configs/mikrotik/ 
mv /home/gnu-ftp01/*.rsc /configs/mikrotik/ 2> /dev/null

# FortiGate
# archive all fortigate daily config backup into /configs/fortigate/ 
mv /home/gnu-ftp01/fw01.conf /configs/fortigate/ 2> /dev/null
# rename the file with current date
cd /configs/fortigate/ 2> /dev/null
mv fw01.conf fw01-$(date +'%Y%m%d').conf 2> /dev/null
```

အထက်က script ကို housekeeping လုပ်ဖို့အတွက် အသုံးပြုပြီးတော့ crontab နဲ့ ညတိုင်း run ဖို့ကို အောက်ကအတိုင်း schedule လုပ်ရပါလိမ့်မယ်။ နောက်ပြီးတော့ အပတ်တိုင်း ၃ လကျော်ကြာသွား ပြီးတဲ့ config file တွေကို remove လုပ်ပစ်ပါ့မယ်။ နောက်မို့ဆိုရင် config file တွေအရမ်းများလာပြီး ftp server ပေါ်မှာ space ကုန်မှာစိုးလို့ပါ။

```
# create a cron job to run the housekeeping script every night
root@rpm-dev02:~# crontab -e 

@daily /opt/scripts/housekeeping.sh
@weekly /usr/bin/find /configs/cisco -ctime +180 -exec rm {} \;
@weekly /usr/bin/find /configs/hpe -ctime +180 -exec rm {} \;
@weekly /usr/bin/find /configs/huawei -ctime +180 -exec rm {} \;
@weekly /usr/bin/find /configs/mikrotik -ctime +180 -exec rm {} \;
@weekly /usr/bin/find /configs/fortigate -ctime +180 -exec rm {} \;
```

ဒီ housekeeping.sh bash script နဲ့ cron job ဟာ စာရေးသူ လိုအပ်သလို အသုံးပြုလို့ရအောင်လို့ လုပ်ထားတာဖြစ်တဲ့အတွက် ပြီးပြည့်စုံတဲ့ workflow တော့မဟုတ်ပါ။ သို့သော်စာရေးသူ အတွက်တော့ အလုပ်ဖြစ်ပါတယ်။

ဒါကတော့ ftp/tftp ကိုအသုံးပြုပြီးတော့ multi-vendors networking device တွေရဲ့ config ကို auto backup လုပ်နိုင်တဲ့ workflow လေးတစ်ခုပဲဖြစ်ပါတယ်။ တခြားသော နည်းလမ်းတွေလည်းရှိပါတယ်။ ဒီ workflow ကတော့ စာရေးသူ အတွက် ကိုက်တဲ့ workflow ဖြစ်တဲ့အတွက် အခုလို ရှင်းပြပေးရ ခြင်းဖြစ်ပါတယ်။ ဒီ post ကို ဒီမှာပဲရပ်လိုက်ပါတော့မယ်။ အားလုံးအဆင်ပြေမယ်လို့ မျှော်လင့်ပါတယ်။
