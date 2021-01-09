# Ubuntu မှာအလုပ်ဖြစ်သော tool နဲ့ application \(၁၀\) ခုအကြောင်း

Ubuntu စတင်အသုံးပြုသူတွေ တခါတခါမေးလေ့ ရှိတဲ့မေးခွန်းလေးတစ်ခုရှိပါတယ်။ အခုမှစသုံးတာမို့ install လုပ်ပြီးတာနဲ့ ဘာတွေလုပ်သင့်သလဲ။ ဘယ်လို application လေးတွေက ကောင်းသလဲဆိုတာပါ။ ဒီတခါတော့ distro အကြောင်းတွေ Linux certification အကြောင်းတွေကို နည်းနည်းလေး ရိုးလာလောက်ပြီ ဖြစ်တဲ့အတွက် ပေါ့ပေါ့ ပါးပါး အကြောင်းရေးမယ်လို့ စိတ်ကူးမိတာနဲ့ Ubuntu မှာ install လုပ်လုပ်ပြီးချင်း ကိုယ့်အတွက် အဆင်ပြေမယ့် tool လေးတွေ application လေးတွေ အကြောင်းရေးဖို့ ဖြစ်လာပါတော့တယ်။ Ubuntu သုံးတာနည်းနည်း ကြာလာတဲ့သူတွေ အတွက်တော့သိပြီးသားလည်း ဖြစ်ကောင်းဖြစ်နိုင်ပါတယ်။ အခုမှစသုံးတဲ့ သူတွေအတွက်တော့ အသုံးဝင်မယ်လို့ မျှော်လင့်ပါတယ်။ အောက်မှာတော့ တစ်ခုခြင်းစီ အကြောင်းနဲ့ ဘယ်လို install လုပ်ရတယ်၊ ဘယ်လို အသုံးပြုသလဲဆိုတာကို ရှင်းပြသွားပါ့မယ်။

## ၁. Grub Customizer

ဒီ grub customizer ကတော့ GUI ကနေပြီး GNU/Linux ရဲ့ grub bootloader ကို အလွယ်တကူ ပြင်ဆင်လို့ရအောင်လို့ Daniel Richter ဆိုတဲ့ developer တစ်ယောက်ကရေးပေးထားတဲ့ tool လေးပါ။ ပုံမှန်အားဖြင့် ကိုယ်က Windows နဲ့ Ubuntu ကို dual boot တင်တဲ့အခါမှာ များသောအားဖြင့် Windows ကိုအရင်တင်ပြီးတော့မှ Ubuntu တင်တာပိုပြီး ခေါင်းစားသက်သာ ပါတယ်။ အဲ့ဒီလို Windows ကိုတင်ပြီးမှ Ubuntu တင်တဲ့အခါ Ubuntu က လက်ရှိ Windows နဲ့ တွဲပြီး dual boot တင်မလားဆိုတဲ့ ဟာပါတဲ့အတွက် အဲ့ဒါလေးကို ရွေးလိုက်တာနဲ့  သူ့ဟာသူWindows ရဲ့ system file တွေနဲ့ data တွေကိုလည်း ပျက်စီးထိခိုက် သွားမှာကို စိုးရိမ်စရာမလိုတော့ပါဘူး။ အဲ… ကိုယ်ရဲ့ စက်ပေါ်မှာတော့ unallocated  partition တော့ရှိဖို့လိုပါလိမ့်မယ်။ အဲ့ဒါကတော့ Windows ဘက်အခြမ်းကနေ disk management နဲ့ပဲ ဖြစ်ဖြစ် third party disk manager/director တစ်ခုခုသုံးပြီးတော့ ပဲဖြစ်ဖြစ် unallocated partition ကို အရင်ဖန်းတီးပေးခဲ့ဖို့တော့လိုပါတယ်။GNU GRUB Bootloader

![](https://itmatic101.files.wordpress.com/2019/09/c2fe7-grub.png?w=660)

ထားပါတော့… အသေးစိတ်တော့ မရှင်းတော့ပါဘူး။ grub customizer အကြောင်းရေးတာဆိုတော့ လိုရင်းကိုဆက်လိုက်ရအောင်။ အရှေ့မှာပြောခဲ့သလို Ubuntu ကိုရှိပြီးသား Windows နဲ့တွဲ ပြီးတော့ install လုပ်မယ်လို့ပြောလိုက်ရင် Ubuntu က Windows ရဲ့ bootloader ကို မသုံးတော့ပဲ သူ့ရဲ့ grub ကို default bootloader အနေနဲ့ သုံးပါတယ်။ install လုပ်လို့ပြီးသွားရင် reboot လုပ်ပြီးတဲ့အခါမှာ အဲ့ဒီ grub ကိုအရင်ရောက်ပါတယ်။  Windows ကို ရွေးစရာရဲ့ အောက်ဆုံးမှာ ထားပြီး ၁၀ စက္ကန့် အချိန်ရပါတယ်။ ကိုယ်တက်ချင်တဲ့ OS ကို keyboard ကနေ up down keys သုံးပြီး Enter ခေါက်လိုက်တာနဲ့ OS တက်ပါတယ်။ ပြဿနာက ကိုယ်က အဲ့ဒီ Menu လေးကိုပြင်ချင်တယ် ဆိုရင် Ubuntu ဘက်အခြမ်းမှာ terminal ကနေ command တွေသုံးပြီးတော့ ပြင်လို့ရပါတယ်။ စသုံးတဲ့သူတွေအတွက် ဆိုရင်တော့နည်းနည်း စိတ်ရှုပ်ရမှာဖြစ်ပါတယ်။ ခက်တော့လည်း မခက်ပါဘူး။ ဒါပေမယ့် ကိုယ်က GUI ကနေအလွယ်တကူ ပြင်လိုတယ်ဆိုရင်တော့ grub customizer ကို install လုပ်ပြီးတော့ GUI ကနေ သွားပြင်လို့ရပါတယ်။GRUB Customizer

![](https://itmatic101.files.wordpress.com/2019/09/d3b62-grubcustomizer01.png?w=660)

grub customizer ကို install လုပ်မယ်ဆိုရင်တော့ အောက်က command လေးတွေကို Ubuntu ရဲ့ terminal မှာ တစ်ကြောင်းပြီး တစ်ကြောင်းရိုက်ထည့်လေးလိုက်ရုံပါပဲ။

```text
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer
```

Grub customizer ကို install လုပ်ပြီးရင်တော့ Ubuntu မှာသူ့ကိုရှာပြီး launch လုပ်လိုက်တဲ့ GUI နဲ့ grub customizer တက်လာမှာပါ။ root privilege လိုတဲ့အတွက် sudo password တော့ တောင်းပါလိမ့်မယ်။ ရိုက်ထည့်ပေးလိုက်တာနဲ့ grub customizer စတင်သုံးလို့ရပါပြီ။ သုံးရတာတော့ GUI မှာလွယ်တဲ့အတွက် အသေးစိတ်မရှင်းတော့ပါဘူး။ ကိုယ်တိုင်တာ အသုံးပြုရင်းနဲ့ စမ်းကြည့်ပါ။ တခုရှိတာကတော့ သေချာမသိပဲနဲ့  grub customizer ထဲမှာ သွားပြီး ဟိုဖျက်ဒီဖျက်တော့ မလုပ်ပါနဲ့။ boot မတက်တော့မယ့်ထိ ပြဿနာရှိနိုင်ပါတယ်။ သတိလေးနဲ့တော့ အသုံးပြုပါ။

## ၂. Google Chrome

ဒီတစ်ခုကတော့ သိပ်ပြီးရှင်းပြစရာတောင် မလိုပါဘူး။ Ubuntu မှာအလွန်ကောင်းတဲ့ Firefox browser နဂိုအတိုင်းပါလာပြီးသားပါ။ သို့ပေမယ်လည်း Google ရဲ့ Chromecast လို device တွေသုံးရင်တော့ Google Chrome ကို သုံးမှရမှာပါ။ စာရေးသူ အမြင်မှာတော့ Chrome ကတော့ လက်ရှိမှာ အလုပ်အဖြစ်ဆုံး internet browser တစ်ခုပါ။ Chrome ကိုတော့ Google ရဲ့ download လုပ်တဲ့ ကနေ deb file ကို download ဆွဲပြီးတော့ deb file ကို double click လုပ်လိုက်တာနဲ့  Ubuntu Software တက်လာပြီးတော့ install လုပ်လိုက်ရုံပါပဲ။ ဘာ command မှမလိုပါဘူး။

![](https://itmatic101.files.wordpress.com/2019/09/1a103-1-startinstallation.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/89f11-google-chrome-ubuntu.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/8b1d3-chromecast.jpg?w=660)

## ၃. Notepadqq

Windows မှာ အရိုးအရှင်းဆုံးနဲ့ အလုပ်အဖြစ်ဆုံး text editor တစ်ခုရှိပါတယ်။ အဲ့ဒါကတော့ Notepad++ ဖြစ်ပါတယ်။ Ubuntu Linux မှာတော့ Notepad++ မရှိတဲ့အတွက် အစားထိုးဖို့အတွက် ဒီ Notepadqq ဆိုတဲ့ application နဲ့ အစားထိုးလို့ရပါတယ်။ Notepad++ နဲ့ပုံစံတူဖြစ်တဲ့အတွက် မျက်စိလည်စရာမရှိပါဘူး။ GUI မှာသုံးလို့ရတဲ့ text editor တွေထဲမှာတော့ Notepadqq ကတော်တော်လေး ပေါ့ပါးပါတယ်။ coding သမားတွေ အတွက်တော့ color markup ဖြစ်တဲ့အတွက် အလွယ်တကူ troubleshoot လို့ရတဲ့အပြင်မျက်စိလည်း ရှင်းပါတယ်။ Notepadqq ကို Ubuntu မှာ install လုပ်ချင်ရင်တော့ အောက် command တစ်ခုချင်းစီ ကို terminal ထဲမှာရိုက်ထည့်လိုက်ပါ။

```text
sudo add-apt-repository ppa:notepadqq-team/notepadqq
sudo apt-get update
sudo apt-get install notepadqq
```

![](https://itmatic101.files.wordpress.com/2019/09/3b8f5-screen.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/09d08-scsh_gui_functionlist.png?w=660)

## ၄. Dropbox

Ubuntu လို Linux distro တွေကို သုံးချင်ရင် Google Drive တို့ Onedrive တို့ကို စက်ပေါ်မှာ install လုပ်ရတာနဲ့အသုံးပြုရတာ နည်းနည်းလက်ဝင်ပါတယ်။ ကိုယ်က Ubuntu လို Linux တင်ထားတဲ့ စက်နဲ့ တခြား Windows စက်တွေမှာ file တွေ folder တွေကို sync လုပ်ချင်တယ် ဆိုရင်တော့ Dropbox က Ubuntu အတွက် Ubuntu Software ပေါ်မှာရှိပါတယ်။ အဲ့ကိုသွားပြီးတော့ Dropbox ဆိုပြီးရှာလိုက်ရုံပါပဲ။ ပြီးရင်တော့ install လုပ်ပြီးတော့ ကိုယ် account နဲ့ setup လုပ်လိုက်ပါ။ 2GB ထိတော့ အခမဲ့ရပါတယ်။ ပိုပြီးလိုရင်တော့ ဝယ်ရပါလိမ့်မယ်။

![](https://itmatic101.files.wordpress.com/2019/09/7ef87-nywqgnc.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/af4cc-install-dropbox-ubuntu-linux-3.png?w=660)

## ၅. GParted

GParted ဟာ GNU/Linux distro တွေရဲ့ LiveCD တော်တော်များများမှာ partitioning tool အနေနဲ့ ထည့်ပေးထားပါတယ်။ သုံးရတာ အဆင်ပြင်တဲ့အပြင် အလုပ်ဖြစ်လွန်းတဲ့ partitioning tool တစ်ခုအနေနဲ့လူသိများကြပါတယ်။ Ubuntu ကို ကိုယ့်စက်ပေါ်မှာ install လုပ်ရင် GParted သပ်သပ် install လုပ်ပေးရပါတယ်။ သူကိုလည်း Ubuntu Software ကနေရှာပြီး တော့ install လုပ်ပေးလိုက်ရုံပါပဲ။ GParted ဟာ Windows က Disk Management လိုပါပဲ။ ဒါပေမယ့် ပိုပြီးအလုပ်ဖြစ်ပါတယ်။ သတိထားပြီးတော့ အသုံးပြုစေချင်ပါတယ်။ GParted မှာ မှားဖျက်မိတဲ့အခါ ကိုယ်ရဲ့ bootloader တွေ system file တွေကို ပြဿနာပေးပြီး boot မတက်တော့တဲ့ထိဖြစ်တတ်ပါတယ်။ သတိလေးနဲ့ တော့ အသုံးပြုစေချင်ပါတယ်။

![](https://itmatic101.files.wordpress.com/2019/09/97c9e-dual-boot-windows-8-ubuntu-gparted.jpg?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/ff33b-gparted.jpg?w=660)

## ၆. VLC Player

Ubuntu မှာလည်း နဂိုအတိုင်းပါလာတဲ့ video player တစ်ခုရှိပါတယ်။ ဒါပေမယ့် VLC Player ကိုတော့ စာရေးသူ အနေနဲ့ ပိုပြီး အကြိုက်တွေ့မိပါတယ်။ VLC player က video format နဲ့ audio format တော်တော်များများကို ဖတ်ပါတယ်။ နောက်ပြီး VLC Player က player သီးသန့် မဟုတ်ပဲ hidden feature တွေပါဝင်ပါတယ်။ ဥပမာ VLC Player ကို video format အတွက် converter အနေနဲ့ အသုံးပြုလို့ရပါတယ်။ ဒါ့အပြင် screen capture လုပ်လို့လည်းရပါတယ်။ သူ့မှာ သုံးလို့ရတဲ့ feature တွေအများကြီးပါဝင်ပါတယ်။ VLC Player ကို install လုပ်ချင်ရင်တော့ အောက်က command တစ်ခုချင်းစီကို terminal မှာရိုက်ထည့်သွားပါ။

```text
sudo apt-get install vlc browser-plugin-vlc
```

![](https://itmatic101.files.wordpress.com/2019/09/0b859-install_vlc-_player_ubuntu12_04.jpg?w=660)

## ၇. Teamviewer

Teamviewer ကတော့ လူသုံးများတဲ့ အလုပ်ဖြစ်တဲ့ remote session ဖို့ အကောင်းဆုံး application တစ်ခုဖြစ်ပါတယ်။ အိမ်သုံးဖို့ အတွက်ကိုတော့ အခမဲ့ဖြစ်ပြီးတော့ လုပ်ငန်းခွင်အတွက်ဆိုရင်တော့ ဝယ်ရပါလိမ့်မယ်။ ကိုယ့်အသိ ကိုယ်မိတ်ဆွေတွေကို အဝေးတစ်နေရာကနေ remote desktop နဲ့ လှမ်းချိတ်ပြီး အကူအညီပေးချင်ရင်တော့ Teamviewer က အသုံးဝင်ပါတယ်။ Internet connection တော့ ရှိဖို့လိုပါတယ်။ သုံးရတာ အရမ်းအဆင်ပြေတဲ့အတွက် ကုမ္ပဏီ ကြီးတွေမှာတောင် Teamviewer နဲ့ပဲ Desktop Support လုပ်ကြပါတယ်။ Teamviewer ကိုတော့ သူ့ကို download လုပ်တဲ့ နေရာကနေ Ubuntu အတွက်ဆိုတဲ့ဟာကို download ဆွဲပြီးတော့ deb file ကို double click လုပ်ပြီးတော့ install  လုပ်လိုက်ရုံပါပဲ။

![](https://itmatic101.files.wordpress.com/2019/09/01a88-teamviewer.png?w=660)

## ၈. KeePassX

တချို့ က email တွေ social media account တွေနဲ့ တခြားသော ကိုယ့်အတွက်လိုအပ်မယ့် account တွေများလွန်းလှလို့ password ကိုတစ်ခုတည်းထားပြီး account အကုန်လုံးအတွက် အဲ့ဒီ password ကိုပဲသုံးပါတယ်။ ပြဿနာက အဲ့ဒီ password ကို တစ်ယောက်ယောက်က တနည်းနည်းနဲ့ ရသွားလို့ကတော့ ကိုယ့် ရဲ့ digital ဘဝတခုလုံး ဆုံးရှုံးတယ်လို့သာ မှတ်လိုက်ပါတော့။ အဲ့ဒီတော့ account တစ်ခုကို password အသစ်တစ်ခုနဲ့  အသုံးပြုခြင်းသာ ကိုယ့်အတွက် အကောင်းဆုံး ဖြစ်မှာပါ။ အဲ… နောက်ပြဿနာတစ်ခုက password များလာတော့ password တွေမှတ်ရတဲ့ ကိစ္စတစ်ခုထက်တိုးလို့ လာပါတယ်။ အဲ့လိုအခါမျိုးမှာ password manager ဆိုတာမျိုးကို အသုံးပြုရပါတယ်။ ပြောရရင်တော့ ကိုယ့် password တွေအကုန်လုံးကို password manager ထဲမှာထည့်သိမ်းထားပြီးတော့ အဲ့ဒီ password manager ကို နောက် password တစ်ခုနဲ့ ထည့်ပိတ်ထားလိုက်တဲ့ သဘောပါ။ အဲ့ဒီ password ကတော့ အရမ်းအရေးကြီးပါတယ်။ သေချာမှတ်ထားရမဲ့ master key password လိုဖြစ်သွားမှာပါ။ Ubuntu Linux အတွက်တော့ KeePassX ဆိုတဲ့ password manager တစ်ခုရှိပါတယ်။ အဲ့ password manager က ကိုယ့်ရိုက်ပြီးထည့်ထားတဲ့ password တွေကို သူ့ရဲ့ database file တစ်ခုမှာ အကုန်သိမ်းပြီးတော့ နောက် password တစ်ခုနဲ့ အဲ့ဒီ database ကို encrypt လုပ်ပေးထားပါတယ်။ encryption အကောင်းစားကို အသုံးပြုထားတဲ့အတွက် hack ဖို့လည်းမလွယ်ပါဘူး။ ကိုယ့်ကတော့ password manager က database file ကို lock လုပ်ပေးထားတဲ့ password ကိုတော့ သေချာသိမ်းထား မှတ်ထားရပါမယ်။ အဲ့ဒါအပြင် 2 way authentications လုပ်ချင်ရင်လည်း password တစ်ခုတည်း မဟုတ်ပဲ key file ကိုပါ ထပ်ထည့်လို့ ရပါတယ်။ နောက်ပြီး အဲ့ဒီ database file လေးကို usb flash drive နဲ့ ဖြစ်ဖြစ် dropbox နဲ့ပဲဖြစ်ဖြစ် ကိုယ်အတွက် အလွယ်တကူ access လုပ်လို့ရမယ့် နေရာမျိုးမှာ သိမ်းထားဖို့တော့ လိုပါလို့မယ်။ database file ကိုတော့ နှစ်ခုသုံးခုလောက်တော့ မတူတဲ့နေရာမျိုးမှာ backup အနေနဲ့ ခွဲပြီးတော့ သိမ်းထားသင့်ပါတယ်။ KeePassX password manager ကို install လုပ်ချင်ရင်တော့ အောက်က command တစ်ခုစီကို terminal တစ်ခုချင်းစီရိုက်ထည့်ပေးလိုက်ပါ။

```text
sudo add-apt-repository ppa:eugenesan/ppa
sudo apt-get update
sudo apt-get install keepassx
```

![](https://itmatic101.files.wordpress.com/2019/09/87376-keepass2-ubuntu.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/3793c-keepassx-running-in-ubuntu.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/ffb9a-keepassx-2.jpg?w=660)

## ၉. Virtualbox

Virtualbox ကတော့ ကိုယ့်စက်ပေါ်မှာ Virtualization Environment တစ်ခု တည်ဆောက်ဖို့အတွက်လိုအပ်တဲ့ hypervisor platform ပါ။ VMware ရဲ့ ပိုက်ဆံပေးဝယ်ရတဲ့ Workstation လိုမျိုး platform ဖြစ်ပါတယ်။ Virtualbox ကတော့ အခမဲ့ပါ။ တခုတော့ရှိပါတယ်… ကိုယ့်စက်မှာတော့ CPU, RAM နဲ့  Hard Disk လိုမျိုး resource တွေ အပိုရှိဖို့တော့လိုပါတယ်။ VMs တွေ run ဖို့ကတော့ အနည်းဆုံး နောက်ပိုင်းထွက်တဲ့ အလယ်အလတ် CPU မျိုး၊ RAM ကတော့ 8GB ကနေ 32 GB လောက်တော့ရှိရမှာပါ။ Hard Disk ကလည်း SSD ဆိုရင်တော့ ပိုကောင်းပါတယ်။ ပြီးတော့ 256GB ကနေ 500GB လောက်ဆိုရင်တော့ VM သုံးလုံး လေးလုံးလောက်တော့ တပြိုင်နက်တည်း run ပြီး virtual lab တစ်ခုတည်ဆောက်လို့ရပါတယ်။ Virtualbox ကိုတော့ သူရဲ့ download လုပ်တဲ့ နေရာကနေ download ဆွဲပြီးတော့ deb file ကို double  click လုပ်ပြီး install လုပ်လိုက်ရုံပါပဲ။ Ubuntu Software မှာလည်း virtualbox ဆိုပြီးရှာလိုက်ရင်တွေ့ နိုင်ပါတယ်။ ကိုယ်အဆင်ပြေမယ့် နည်းနဲ့သာ install လုပ်ပြီးတော့ သုံးပါ။

![](https://itmatic101.files.wordpress.com/2019/09/1246f-install-virtualbox-on-linux-mint-ubuntu-02.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/1b163-install-virtualbox-on-linux-mint-ubuntu-04.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/a8a23-virtualbox-for-ubuntu.jpg?w=660)

## ၁၀. Zawgyi Keymagic Keyboard

ဇော်ဂျီလား ယူနီကုဒ်လား ဆိုတဲ့ပြဿနာ ကအခုထိတိုင်ရှိနေဆဲပါ။ မြန်မာနိုင်ငံမှာတော့ အင်တာနက် အသုံးပြုသူတွေ တော်တော်များများဟာ ဇော်ဂျီ ဖောင့်\(ထ်\) နဲ့ ကီးဘုတ်ကို အခုထိ de facto standard တစ်ခုအနေနဲ့ အသုံးများနေဆဲပါ။ အင်တာနက်မှာ စာဖတ် တဲ့သူတွေကလည်း ဇော်ဂျီ ဖောင့်\(ထ်\) နဲ့သာ ဖတ်ကြပါတယ်။ သို့သော် ဇော်ဂျီမှာက ပြဿနာတွေအများကြီးရှိပါတယ်။ အဓိက ကတော့ Unicode Standard ကို မလိုက်နာထားတာဟာ အဆိုးဆုံးထဲက တစ်ခုပါ။ အဲ့ဒီတော့ မသုံးသင့်တော့ပါဘူး။ ဘယ်လိုပဲဖြစ်ဖြစ် လက်ရှိမှာတော့ ဇော်ဂျီကတော့ သုံးနေရတုန်းပါ။ Ubuntu မှာတော့ ယူနီကုဒ်မြန်မာ ကီးဘုတ်နဲ့ ဖောင့်\(ထ်\) သုံးမယ်ဆိုရင်တော့ နဂိုအတိုင်းပါလာပြီးသားပါ။ ဇော်ဂျီသုံးမယ်ဆိုရင်တော့ ကီးဘုတ်အတွက် ရွေးစရာတွေများပါတယ်။ အဲ့ဒီရွေးစရာ အများကြီးထဲမှာတော့ စာရေးသူက Ubuntu မှာအဆင်အပြေဆုံး ဖြစ်ပြီးတော့ ibus မှာ run တဲ့ ဇော်ဂျီအတွက် keymagic ကို အလုပ်ဖြစ်တယ်လို့ ထင်ပါတယ်။ Apple ရဲ့ Macbook တို့ iMac တို့ မဟုတ်တဲ့ ရိုးရိုး PC သို့မဟုတ် Laptop တွေရဲ့ Keyboard မှာတော့ စာရေးသူ အသုံးပြုကြည့်မိ သလောက်တော့ ibus-keymagic ကအဆင်ပြေဆုံးလို့တော့ ထင်ပါတယ်။ Apple စက်တွေရဲ့ keyboard မှာတော့ နည်းနည်းလေး အဆင်သိပ်မပြေပါဘူး။ ibus-keymagic ကိုတော့ ကို ကိုကိုရဲ ရဲ့ launchpad ကို repository အနေနဲ့ သုံးပြီးတော့ install လုပ်ရပါ့မယ်။ Zawgyi ibus-keymagic keyboard နဲ့ Zawgyi Font ကို install လုပ်ချင်ရင်တော့ အောက်က command တွေကို တစ်ခုချင်းစီ terminal ထဲမှာရိုက်ထည့်ပေးလိုက်ပါ။ ဒီမှာ စကားချပ် အနေနဲ့ တခုပြောချင်တာကတော့ ဇော်ဂျီဖောင့်\(ထ်\) ကို Ubuntu မှာ install လုပ်လိုက်တာနဲ့ Ubuntu ရဲ့ system font နေရမှာ မြန်မာစာကို ပြတဲ့အခါ ဇော်ဂျီကိုသာ သုံးပါတော့တယ်။ မြန်မာယူနီကုဒ် ကိုသုံးတဲ့သူအတွက်တော့ နည်းနည်း အခက်တွေ့နိုင်ပါတယ်။ စာကိုရိုက်တဲ့ အခါမှာလည်း မျက်စိတွေလည်ကုန်တော့တာပါပဲ။ မြန်မာယူနီကုဒ်နဲ့ ရိုက်ပေးမယ့်လည်း ဇော်ဂျီ ဖောင့်\(ထ်\) နဲ့သာ ပြလို့ အကုန်ရှုပ်ကုန်နိုင်ပါတယ်။ ဇော်ဂျီတစ်ခုတည်း အသုံးပြုသူတွေအတွက်တော့ Ubuntu မှာပြဿနာ မရှိပါဘူး။ ဇော်ဂျီဟာ Unicode ရဲ့ Code Point တွေအများကြီးကိုယူသုံးထားတဲ့ အတွက် ဇော်ဂျီကို install လုပ်ပြီးတာနဲ့ system font အနေနဲ့ ပြောင်းသုံးတာ ဖြစ်နိုင်တယ်လို့လည်း Ubuntu Myanmar က developer တစ်ယောက် ကဆိုခဲ့ဘူး ပါတယ်။ အောက်မှာတော့ ဇော်ဂျီအတွက် ibus-keymagic keyboard နဲ့ font ကို install လုပ်ဖို့အတွက် အောက်က command တစ်ကြောင်းချင်းစီကို terminal ထဲမှာရိုက်ထည့်ပေးလိုက်ရုံပါပဲ။

```text
sudo add-apt-repository -y ppa:kokoye2007/ppa
sudo apt-get update
sudo apt-get install ibus-keymagic
sudo apt-get install ibus-table-my-zawgyi
sudo apt-get install ttf-myanmar-fonts-zawgyi
```

![](https://itmatic101.files.wordpress.com/2019/09/0f5e7-zawgyi-l-keymagic.png?w=660)

![](https://itmatic101.files.wordpress.com/2019/09/fcae7-ibus-keymagic.png?w=660)

အထက်မှာတော့ Ubuntu မှာ အသုံးပြုနိုင်တဲ့ အလုပ်ဖြစ်တဲ့ tool တွေနဲ့ application တွေအကြောင်း ကိုဖော်ပြပေးခဲ့တာဖြစ်ပါတယ်။ ဒီ ​post ကိုတော့ ဒီမှာပဲရပ်လိုက်ပါတော့မယ်။

