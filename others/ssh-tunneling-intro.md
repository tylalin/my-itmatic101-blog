# SSH Tunneling အကြောင်းသိကောင်းစရာ

စာမရေးဖြစ်တာနည်းနည်း တောင်ကြာသွားပြီဖြစ်လို့ ဘယ်ကနေဘယ်လို ပြန်ပြီးတော့ စာကိုစရေး လိုက်ရမယ်မှန်းမသိတောင် ဖြစ်သွားပါတယ်။ ရေးစာရာ အကြောင်းအရာတွေကတော့ အများကြီး ရှိပါတယ်။ အခုတလော tech နဲ့ ဆိုင်တဲ့ အထူးသဖြင့် Linux နဲ့ ဆိုင်တဲ့ podcast တွေအများကြီးနားထောင်ဖြစ်လို့ နောက်ထက် အသစ်အသစ်တွေ open source ကမ္ဘာမှာ ထက်ပြီးတော့ ရှာဖွေတွေရှိလို့နေပါတယ်။ အထူးသဖြင့် Linux မှာအသုံးပြုလို့ရတဲ့ tools တွေအများကြီး သိလာတယ်။ podcast တွေက weekly update ဖြစ်လို့ open source ကမ္ဘာက နောက်ဆုံးပေါ် tools တွေအကြောင်းကို အသစ်သစ် ပိုမိုတွေ့ရှိလာရပါတယ်။ podcast တွေဟာ အသံကိုပဲနားထောင်စရာလိုလို့ ကိုယ် idle ဖြစ်လို့ရှိရင် ဖွင့်ထားလိုက်ရုံနဲ့ သင်ကြားမူ process ကအလိုလိုနေရင်းနဲ့ စပါတော့တယ်။ ဟိုတချိန်က radio ခေတ်မှာလိုပဲ podcaster တွေထဲမှာလည်း တချို့သော host တွေက rockstar တွေပမာ နာမည်ကြီးတဲ့ podcaster တွေလည်းရှိပါတယ်။ လက်ရှိ စာရေးသူ နားထောင်ဖြစ်နေတဲ့ shows တွေတော်တော်များများဟာ Jupiter Broadcasting ဆိုတဲ့ အမေရိကန် နိုင်ငံက podcast တွေကိုများသောအားဖြင့်နားထောင် ဖြစ်နေပါတယ်။ အမေရိကန်နိုင်ငံ podcast ဆိုပေမယ့်လည်း သူတို့ရဲ့ shows တွေမှာ ပါဝင်ဆွေးနွေးကြတဲ့ သူတွေထဲမှာ ဗြိတိသျှလူမျိုးတွေလည်း ပါဝင်တဲ့ အတွက် စိတ်ကူးမျိုးစုံ အတွေးအခေါ်မျိုးစုံ တော်တော်များများကို ကိုယ်ကဇာတ်ရုံတစ်ခုထဲမှာ ထိုင်ပြီးတော့ကြည့်ရတဲ့အတိုင်း ဖော်ဖြေမူအပိုင်းမှာပါမကပဲ ဗဟုသုတလည်း အများကြီးရပါတယ်။ Jupiter Broadcasting \(အတိုကောက် JB\) shows ထဲမှာလည်း ရသမျိုးစုံကို ပေးနိုင်တဲ့ shows အမျိုးမျိုးရှိပါတယ်။ ဥပမာ ကိုယ်က self-hosted servers တွေနဲ့ services တွေကြောင်းကို နားထောင်ချင်ရင် Self-Hosted ဆိုတဲ့ show ရှိသလို၊ FreeBSD နဲ့ တခြားသော BSD variants တွေအကြောင်းကို သိချင်ရင် BSD Now ဆိုတဲ့ show ရှိပါတယ်။ စိတ်ဝင်စားတယ်… ကိုယ်လည်း နားထောင်ကြည့်ချင်တယ်ဆိုရင်တော့ ဒီ link [https://www.jupiterbroadcasting.com/ ](https://www.jupiterbroadcasting.com/)ကနေသွားကြည့်လို့ပါတယ်။ ဒါကတော့ ဒီတလောမှာ စာရေးသူ ရှာဖွေတွေ့ ရှိထားတဲ့ hobby အသစ်တခုလို့ ဆိုရမှာဖြစ်ပါတယ်။ နောက်ထက်စာတွေ မရေးဖြစ်တာကလည်း ကိုယ်ဟာကို အများကြီးဖြည့်ဖို့ကျန်နေသေးတယ် အထင်ရလို့ hibernation ခဏလုပ်ထားတာလည်းဖြစ်ပါတယ်။ စာရေးသူ စာတွေအများကြီးထက်ပြီးတော့ ရေးချင်ပါတယ်။ သိချင်တာတွေလည်းအများကြီး ကျန်ပါသေးတယ်။ စာတွေလည်း အများကြီးဖတ်ချင်ပါသေးတယ်။ ဒီတော့ စာတွေအများကြီး ထက်ရေးသွားပါ့မယ်။

အထက်မှာပြောခဲ့သလိုပဲ podcast တွေနားထောင်ဖြစ်လို့ သူတို့ပြောတဲ့ သူတို့ကြိုက်တဲ့ open source tools တွေအကြောင်း အများကြီး သိခွင့် ရခဲ့ပါတယ်။ များလွန်းလို့ ဘယ်အကြောင်းစရေးရမလဲဆိုတာ တော်တော်လေးကို စဥ်းစားပြီးမှ ကိုယ်ရေးချင်တဲ့ topic ကိုရွေးချယ်ရပါတယ်။ ဒီ post မှာရေးချင်တဲ့ အကြောင်းကတော့ secured tunnel အကြောင်းပါ။ ပထမတစ်ခုက SSH Tunneling အကြောင်းနဲ့ WireGuard ဆိုတဲ့ overlay VPN အကြောင်းပဲဖြစ်ပါတယ်။ စာရေးသူ ကိုယ်တိုင် အလုပ် နဲ့ အိမ်အတွက် IPsec နဲ့ SSL VPN တွေကို နေ့တိုင်းလိုလို အသုံးပြုရပါတယ်။ အထူးသဖြင့် အိမ်အတွက်တော့ OpenVPN ကို OPNsense box မှာ တင်ပြီးတော့ အသုံးပြုပါတယ်။ OPNsense မှာ OpenVPN အတွက် 2 Factors Authentication \(2FA\) နဲ့ TLS encryption လို security feature တွေပါလို့ တော်တော်လေး တွင်တွင်ကျယ်ကျယ် အသုံးပြုဖြစ်ပါတယ်။ သို့သော် performance အပိုင်းမှာတော့ overhead များလို့ ထင်သလောက် အလုပ်မဖြစ်သလိုခံစားရပါတယ်။ security feature တွေအတွက် ပေးဆပ်လိုက်ရတဲ့ performance ပိုင်းမှာ အနည်းငယ် ထိခိုက်သွားတဲ့ သဘောမျိုးပါ။ OpenVPN ကို OPNsense ပေါ်မှာ setup လုပ်ရတာလည်း အရမ်းကြီး မခက်သလို အရမ်းလည်း အလွယ်လွန်းလှပါဘူး။ ပထမဆုံး တခေါက်ကတော့ နည်းနည်းလေးရွာလည်ပါတယ်။ နောက်ပိုင်းတော့လည်း ထင်သလောက် မရှုပ်လှပါဘူး။ စာရေးသူ ၃ခါ ၄ခါလောက်တော့ OPNsense ကို rebuilt ပြန်လုပ်ရပါတယ်။ များသောအားဖြင့် ဟိုစမ်းဒီစမ်းနဲ့ OPNsense မှာ error တက်လာတာနဲ့ ပြန်ပြီးတော့ အစကနေ rebuilt လုပ်ရပါတယ်။ စာရေးသူအတွက်တော့ အလုပ်ရှုပ်တယ်လို့မထင်ပဲနဲ့ အသစ်တခုခုကို လေ့လာသင်ကြားနိုင်တဲ့ အခွင့်လမ်းအနေနဲ့ မြင်ပါတယ်။ ဒါကတော့ open source မှာရနိုင်တဲ့ free သင်ခန်းစာတွေလို့ပဲ မြင်မိပါတယ်။

ဒီ post မှာတော့ SSH အကြောင်း အနည်းငယ်မိတ်ဆက်ပေးပြီးတော့၊ SSH Tunneling ကိုဘယ်လို အသုံးပြုရသလဲဆိုတာကို ဆက်ပြီးတော့ ရှင်းပြသွားပါ့မယ်။

### SSH မိတ်ဆက်

SSH version 1.x ကိုစတင် တီထွင်ပေးခဲ့တာကတော့ Finland နိုင်ငံသား Tatu Ylönen ဆိုတဲ့ Helsinki University of Technology က ကျောင်းသား တစ်ယောက်ဖြစ်ပါတယ်။ ဖြစ်ပုံက သူရဲ့ remote session ကို network ပေါ်မှာ sniff လုပ်ပြီးတော့ login ကို hacked ခံရတာကနေစပါတယ်။ အဲဒီမှာ သူက unsecured protocol တွေဖြစ်တဲ့ rlogin, telnet နဲ့ ftp တွေကို အစားထိုးဖို့ အတွက် ကြံဆောင်ရင်း နဲ့ SSH ကို ၁၉၉၅ခုနှစ်မှာ freeware အနေနဲ့ စတင်မိတ်ဆက်ပေးလိုက်ပါတယ်။ နောက်ပိုင်းမှာတော့ Tatu Ylönen ကိုယ်တိုင်ပဲ proprietary software အနေနဲ့ ပြန်ပြောင်းထုတ်လာခဲ့ပါတယ်။ ၁၉၉၉ ခုနှစ်မှာတော့ Björn Grönvall ဆိုတဲ့ developer တစ်ယောက်က original ssh version ဖြစ်တဲ့ version 1.2.12 release ပေါ်မှာအခြေခံပြီးတော့ OSSH ကို အခြားသော developers တွေအတွက် ပြန်လည် မိတ်ဆက်ပေးခဲ့ပါတယ်။ သို့သော်လည်း OSSH ဟာ အချိန်တစ်ခုအထိသာ ရပ်တည်နိုင်ပြီးတော့ သူ့ project က ရပ်လို့သွားပြန်ပါတယ်။ ဒါနဲ့ပဲ OpenBSD မှာ အသုံးဖို့အတွက် OSSH ကနေ fork လုပ်ပြီးတော့ OpenSSH ကိုစတင်ခဲ့ကြပါတယ်။ အခုချိန်မှာတော့ OpenSSH ကို နေရာတကာမှာ အသုံးပြုလို့နေပါပြီ။ Microsoft ရဲ့ Windows 10 မှာတောင် April 2018 Update နဲ့အတူပါလာပါတယ်။ PowerShell မှာတော့ ၂၀၁၅ မှာကတည်းက port လုပ်ထားပါတယ်။ ဒါကတော့ SSH နဲ့ ပတ်သတ်တဲ့ စတင်ခဲ့ပုံ အကျဥ်းချုပ် ဖြစ်ပါတယ်။ လက်ရှိမှာတော့ SSH ဟာ security အတွက်အကောင်းဆုံး မဟုတ်တောင်မှ အပေါ့ဆုံး နဲ့ အလုပ်အဖြစ်ဆုံး ဖြစ်လို့ အသုံးပြုနေရဆဲပါ။ အရှင်းဆုံးပြောရရင်တော့ SSH ဟာ HTTP မှာ SSL ကို အသုံးပြုသလိုပဲ၊ TCP connection ကို secure လုပ်ပေးလိုက်တဲ့ သဘောမျိုးပါ။ SSH နဲ့ တွဲပြီးတော့ သုံးလို့ရတဲ့ utilities တွေရှိတဲ့အတွက် တော်တော်လေးတော့ အဆင်ပြေပါတယ်။

SSH ကို စာရေးသူ နေ့စဥ်နဲ့ အမျှအသုံးပြုရပါတယ်။ များသောအားဖြင့် Linux server တွေနဲ့ networking devices တွေကို remote management လုပ်ဖို့အတွက် ssh နဲ့ login လုပ်ရပါတယ်။ အခုနောက်ပိုင်းမှာတော့ Windows 2019 server မှာလည်း OpenSSH server ကို add-on feature အနေနဲ့ ပါလာပါတယ်။ နောက်တစ်ခုက server တွေပေါ်ကနေ file တွေ folder တွေကို copy/transfer လုပ်တဲ့ အခါမှာလည်း server ဘက်မှာဘာ service မှထက်ပြီးတော့ install လုပ်စရာ မလိုပဲ SSH ကို အသုံးပြုပြီးတော့ SCP သို့မဟုတ် SFTP ကို အသုံးပြုပါတယ်။ ဒီနှစ်ခုကတော့ စာရေးသူ နေ့စဥ်နဲ့ အမျှအသုံးပြုတဲ့ SSH နဲ့ပတ်သတ်တဲ့ user-case နှစ်မျိုးပါ။ တခြားသော SSH feature တွေဖြစ်တဲ့ RSA public / private key တွေကိုလည်း device login တွေအတွက် အသုံးပြုပါတယ်။ ဒီတော့ SSH ဟာ လူတိုင်းအတွက် အထူးအဆန်းတော့လည်း မဟုတ်ပါဘူး။ စာရေးသူအတွက် SSH ဟာ နေ့စဥ် workflow အတွက်တော့ မရှိမဖြစ်ပါ။ သို့သော် SSH ကိုအသုံးပြုပြီးတော့ tunneling / port forwarding ကို on-the-fly လုပ်လို့ရတာကို တကယ်မသိခဲ့တာ အမှန်ပါ။ BSD အကြောင်းရေးတုန်းလည်း စာဖတ်သူ တစ်ယောက်က SSH အကြောင်းလည်း အချိန်ရရင်ရေးပါအုံးဆိုလို့ ဒီ post မှာ ပထမပိုင်း အနေနဲ့ ထည့်သွင်းရေး ဖြစ်သွားတာပါ။ JB podcast မှာလည်း SSH tunneling အကြောင်းပြောတာ နားထောင်ဖြစ်တော့ ဘယ်လိုမျိုး အလုပ်လုပ်သလဲဆိုတာက သိချင်တာနဲ့ စတင်ရှာဖွေပြီးတော့ ဖတ်ရပါတော့တယ်။ ပြီးတော့ အားလုံးအတွက် အခုလိုသိသလောက်ကို ပြန်ပြီး မျှဝေလိုက်ရပါတယ်။

### SSH Tunneling ဆိုတာဘာလဲ

SSH ဆိုတာ unsecured channel တစ်ခုမှာ secure tunnel တစ်ခုကို တည်ဆောက်ပြီးတော့ remote management အတွက်အသုံးပြုတဲ့ protocol stack တစ်ခုပါ။ open လည်းဖြစ်၊ သုံးရတာလည်း အဆင်ပြေလို့ remote access အတွက် အသုံးပြုကြတာလည်းဖြစ်ပါတယ်။ SSH ကိုယ်တိုင်က tunneling protocol တစ်ခု ပမာ အသုံးပြုနိုင်တဲ့ feature တွေပါတာဖြစ်တဲ့ အတွက်လိုအပ်တဲ့ port ကို forward လုပ်နိုင်ပါတယ်။ SSH tunneling အတွက် port 22 ကို ကိုယ့် network အပြင်ဘက်နေ မြင်ရအောင်တော့ NAT နဲ့ firewall ကို ဖောက်ပေးထားရပါ့မယ်။ အရှင်းဆုံးပြောရရင်တော့ ကိုယ့်ရဲ့ home internet router မှာ port 22 ကို ကိုယ့်ရဲ့ network အထဲက Linux box ရဲ့ IP address နဲ့ port mapping လုပ်ပေးလိုက်ရုံပါပဲ။ အခြားလိုအပ်တဲ့ application တွေကို ကိုယ်လိုသလို SSH tunnel ထဲကနေ forward လုပ်ဖို့အတွက် အခုဆိုရင် ready ဖြစ်ပါပြီ။ ဥပမာ… remote desktop RDP ကို ကိုယ့်ရဲ့ home internet router ပေါ်မှာ ဒီအတိုင်း port 3389 ကို port forwarding လုပ်လို့ရပါတယ်။ သို့သော် RDP ကိုယ်တိုင်မှာက security အတွက် လိုအပ်တဲ့ defense mechanism မပါတဲ့အတွက် network ပေါ်မှာ sniff လုပ်လိုက်ရင် အလွယ်တကူ hack လို့ရနိုင်ပါတယ်။ တဘက်မှာတော့ SSH ကတော့ security အတွက် ဦးစားပေးတဲ့အတွက် RDP ထက်တော့ ပိုပြီးတော့ လုံခြုံစိတ်ချရတယ်လို့ ယူဆနိုင်ပါတယ်။ ဒါပေမယ့်လည်း Edward Snowden က SSH tunneling လို secure protocol တွေကို အသုံးပြုထားတာတောင် NSA က သူဘာလုပ်ထားသလဲဆိုတာကို ပြောနိုင်ပုံထောက်ရင်တော့ SSH လို secured protocol တွေတောင် အပြည့်အဝ လုံခြုံစိတ်ချနိုင်တယ်လို့ မဆိုနိုင်တော့ပါ။ မည်သို့ပင်ဖြစ်စေ… လက်ရှိမှာ secure channel အတွက်တော့ စာရေးသူတို့ SSH ကို တွင်တွင်ကျယ်ကျယ် အသုံးပြုနေရအုံးမှာပါ။

### SSH ကို အသုံးပြုပြီးတော့ tunneling သို့မဟုတ် port forwarding ကိုဘယ်လိုလုပ်မလဲ

SSH port forwarding ကိုလုပ်တဲ့အခါ လုပ်ပုံလုပ်နည်း ၃ မျိုးရှိပါတယ်။ ပထမတစ်ခုက local forwarding ဖြစ်ပြီးတော့၊ အသုံးပြုဖို့အတွက် -L switch ကို ssh command နဲ့ တွဲပြီးတော့ အသုံးပြုရပါတယ်။ ဒုတိယတစ်ခုက remote forwarding ဖြစ်ပါတယ်။ remote forwarding အတွက်တော့ ssh command မှာ -R switch ကို အသုံးပြုရပါတယ်။ နောက်ဆုံးတစ်ခုကတော့ dynamic forwarding သို့မဟုတ် SOCKS tunnel ဖြစ်ပြီးတော့ အရှေ့က နှစ်မျိုးနဲ့ အသုံးပြုနိုင်တဲ့ ပုံစံကနည်းနည်းတော့ ကွာပါတယ်။ အောက်မှာတော့ SSH tunnel တွေကို ဘယ်လို setup လုပ်သလဲ၊ ဘယ်လို အခါမျိုးမှာအသုံးပြုသလဲဆိုတာကို အသေးစိတ်ဆက်ရှင်းပါ့မယ်။

#### SSH local forwarding အလုပ်လုပ်ပုံ

ဒီတစ်ခုကတော့ရှင်းပါတယ်။ ကိုယ်ရဲ့ Linux box တစ်ခုမှာ SSH server ကို run ထားပြီး internet ကနေ အဲဒီ port 22 ကို မြင်ရအောင် home internet router ပေါ်မှာ Linux box ရဲ့ IP address နဲ့ port 22 ကို NATing သို့မဟုတ် port forwarding လုပ်ပေးထားတယ်ဆိုရင် ကိုယ်ဘယ်ကနေ မဆိုကိုယ် public IP address သို့မဟုတ် ကိုယ့်မှာ static public IP address မရှိဘူးဆိုရင် dynamic DNS name ကို အသုံးပြုလို့ရပါတယ်။ အောက်က command ကတော့ local forwarding အတွက် SSH command ကိုဘယ်လို အသုံးပြုသလဲဆိုတာပြထားတာပါ။

```text
ssh -N -L 3389:10.10.2.100:3389 tyla.lin@123.1.2.210
```

![SSH Local Forwarding](https://i1.wp.com/www.itmatic101.com/wp-content/uploads/2020/01/SSH-Local-Forwarding.png?fit=525%2C142&ssl=1)

ပထမဆုံး ssh ဆိုတာကတော့ ssh protocol ကို အသုံးပြုမယ်၊ -N ဆိုတာက not executing ဘာ command ကိုမှ မ run ဘူးဆိုပြီးတော့ ပြောတာပါ။ ပုံမှန် ssh command ကို terminal ထဲမှာ run တဲ့အခါမှာ remote connection ကိုအောင်မြင်စွာ ချိတ်ဆက် ပြီးသွားတာနဲ့ remote host ရဲ့ prompt လေးပေါ်လာပါတယ်။ အဲ့ဒီ prompt ကိုမလိုချင်လို့ -N ဆိုတဲ့ switch ကိုအသုံးပြုထားတာဖြစ်ပါတယ်။ -L ဆိုတာကတော့ local forwarding လုပ်မယ်လို့ ပြောတာပါ။ ပထမဆုံး 3389 ဆိုတာက ကိုယ်ရဲ့ local machine မှာသုံးမယ့် port number ဖြစ်ပါတယ်။ 10.10.2.100 ဆိုတာကတော့ remote network မှာရှိတဲ့ ကိုယ်သွားချင်တဲ့ destination IP address ဖြစ်ပြီးတော့၊ နောက် 3389 ဆိုတာကတော့ အဲ့ဒီ remote network က destination host မှာကိုယ် map လုပ်မယ့် remote port number ပဲဖြစ်ပါတယ်။ နောက်ဆုံးအပိုင်းဖြစ်တဲ့ tyla.lin@123.1.2.210 ဆိုတာကတော့ စာရေးသူရဲ့ ssh အတွက် username နဲ့ remote ssh server ဖြစ်တဲ့ 123.1.2.210 ကို authenticate လုပ်မယ်ဆိုပြီးတော့ ပြောတာပါ။ ပုံမှန် remote host ကို ssh နဲ့ login ဝင်မယ်ဆိုရင် ssh tyla.lin@123.1.2.210 ဆိုပြီးတော့ command ရိုက်ထည့်လိုက်ရုံပါပဲ။ အခုက ssh ကိုအသုံးပြုပြီးတော့ ကိုယ်လိုချင်တဲ့ port ကို forward လုပ်ပေးတဲ့ သဘောပါ။ လုံခြုံရေးမကောင်းတဲ့ RDP လို port မျိုးကို internet ပေါ်မှာ surface ပေးမယ့်အစား ssh tunneling လုပ်ပြီးတော့ အခုဆိုရင် RDP ကို ကိုယ်လိုချင်တဲ့ remote host ပေါ်ကို ssh server ကနေတဆင့် local forwarding လုပ်သွားတာပဲဖြစ်ပါတယ်။ တကယ်လို့ ကိုယ့်ရဲ့ RDP server က remote ssh server နဲ့ အတူတူပဲဆိုရင် command က အခုလိုဖြစ်သွားပါတယ်။

```text
ssh -N -L 3389:localhost:3389 tyla.lin@123.1.2.210
```

အဲ့ဒီ localhost ဆိုတာက remote host ကိုဆိုလိုရင်းဖြစ်ပါတယ်။၊ ကိုယ့် local machine ရဲ့ localhost ကိုပြောတာမဟုတ်ပါဘူး။ အဲ့ဒီ _LocalPort:RemoteHost:RemotePort_ ဆိုတဲ့ format ကိုကိုယ် ကြိုက်သလို သင့်သလို အသုံးပြုနိုင်ပါတယ်။ ထက်ပြီးတော့ ထည့်လိုရတဲ့ switch တွေတော့ အများကြီးရှိပါတယ်။ အကုန်လုံးကို တော့ မရှင်းလိုတော့ပါဘူး။

အခုဆိုရင် ကိုယ်ရဲ့ အိမ်က RDP server ကို internet ပေါ်မှာ expose လုပ်စရာမလိုတော့ပဲနဲ့ ssh port 22 ကို port forwarding လုပ်ထားရုံနဲ့ ကိုယ်လိုတဲ့ service ရဲ့ port number တွေကို လိုသလို local port forwarding လုပ်သွားလို့ရပါပြီ။ အထက်က ssh command ကိုရိုက်ထည့်ပြီးသွားတာနဲ့ terminal ထဲက command prompt က -N switch ကြောင့် ရပ်နေသလိုဖြစ်နေပါလိမ့်မယ်။ အဲ့ဒါဆိုရင် ကိုယ်ရဲ့ ssh tunnel က စတင်အသုံးပြုလို့ရပါပြီ။ အခုဆိုရင် RDP server ဖြစ်တဲ့ IP address 10.10.2.100 ကို RDP နဲ့ စတင် ဝင်လို့ ရပါပြီ။ SSH tunnel ထဲကနေသွားတဲ့အတွက် တိုက်ရိုက် RDP ဝင်တာထက်တော့ အနည်းငယ် နှေးပါလိမ့်မယ်။

#### SSH remote forwarding အလုပ်လုပ်ပုံ

Remote forwarding ကတော့ အသုံးပြုတဲ့ပုံ အနည်းငယ်ကွာသွားပါတယ်။ ဘယ်လိုအခါမျိုးမှာ အသုံးပြုသလဲဆိုတော့၊ ဥပမာဆိုပါတော့ ကိုယ်က ကိုယ်ရဲ့ laptop ပေါ်မှာ work in progress ဖြစ်နေတဲ့ web application project တစ်ခုအတွက် local machine မှာပဲ web server ကို run ပြီးတော့ အလုပ် လုပ်နေတယ်ဆိုပါတော့။ ကိုယ့်ရဲ့ လက်ရှိ web app ကို အခြားသူတွေကိုပြလို့ရအောင်လို့ public internet မှာ အစမ်းသဘောမျိုးနဲ့ တင်ချင်တယ်။ သို့သော် အလုပ်မှာက firewall ကို ကိုယ်က manage မလုပ်ဘူးလို့ ဆိုကြပါတော့။ ဒါပေမယ့် အလုပ်က web server ကိုတော့ ssh နဲ့ login ဝင်နိုင်တဲ့ account တစ်ခုရှိတယ်လို့ ဆိုရင် အလုပ်ဖြစ်ပါပြီ။ အဲ့ဒီ web server ကတော့ internet public IP တစ်ခုနဲ့ လက်ရှိ production sites တွေကို run ထားတယ်ဆိုကြပါတော့။ ဒါဆိုရင် အစမ်းသဘောမျိုး ကိုယ်ရဲ့ web app ကို အဲ့ဒီ web server ကနေပြီးတော့ internet ပေါ်မှာ expose လုပ်လို့ရနိုင်ပါပြီ။ အခြေခံအားဖြင့် ကိုယ်ရဲ့ laptop က localhost မှာ run ထားတဲ့ web app နဲ့ web server ကြားထဲမှာ secure tunnel တည်ဆောက်ပေးပြီးတော့ ssh remote forwarding လုပ်ပေးလိုက်ရုံပါပဲ။ တခါတလေ reverse forwarding လို့လည်းခေါ်ပါတယ်။ အောက်မှာ ssh remote forwarding ကို terminal မှာ အခုလိုက်ရိုက်ထည့်လိုက်ရုံပါပဲ။

```text
ssh -N -R 8080:localhost:80 tyla.lin@123.1.2.210
```

![SSH Remote Forwarding](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/01/SSH-Remote-Forwarding.png?resize=740%2C172&ssl=1)

အထက်က ssh command ကိုရိုက်ထည့်လိုက်ပြီးတော့ ကိုယ်ရဲ့ SSH login password ကို ရိုက်ထည့်လိုက်ပြီးသွားရင်တော့ ssh tunneling က အဆင့်သင့်ဖြစ်ပါပြီ။ အခုဆိုရင် web browser ထဲမှာ www.itmatic101.com:8080 လို့ရိုက်ထည့်လိုက်ရင် ကိုယ့်ရဲ့ workstation မှာ run ထားတဲ့ development environment က web site ကို ssh tunnel ကနေတဆင့် public internet မှာ စတင် access လုပ်လို့ရပါပြီ။ ဒီနေရာမှာ www.itmatic101.com ဆိုတဲ့ web site မှာ port 8080 ကို အခြားဘယ်နေရာမှာမှ အသုံးပြုမထားသေးဘူးလို့ ယူဆပါတယ်။ အဲ့ဒီ port မအားရင်တော့ အခြားသော port number ကို သင့်သလိုအသုံးပြုလို့ရပါတယ်။ ဒီနည်းနဲ့ သင့်ရဲ့ web app ကို တခြားဘာမှ ထွေထွေထူးထူး setup လုပ်စရာမလိုပဲနဲ့ internet မှာ အစမ်း သဘောမျိုး အလွယ်တကူ တင်လို့ရပါတယ်။ ပြီးရင် ssh tunnel ကို Control + C နဲ့ရပ်လိုက်တာနဲ့ ကိုယ်ရဲ့ web app ကို internet ပေါ်မှာ ဆက်ပြီးတော့ expose မလုပ်တော့ပါဘူး။ အရမ်းကို ရိုးရှင်းတဲ့ ssh ရဲ့ technique တစ်ခုပါ။

#### SSH dynamic forwarding အလုပ်လုပ်ပုံ

နောက်ဆုံးတစ်ခုကတော့ ssh dynamic forwarding ဖြစ်ပါတယ်။ ဒီတစ်ခုကတော့ -D switch ကို အသုံးပြုပြီးတော့ ကိုယ်ရဲ့ ssh server ကို SOCKS proxy server အနေနဲ့ အသုံးနိုင်ပါတယ်။ ထားပါတော့ ကိုယ့်အလုပ်မှာ Facebook တို့ YouTube တို့ကိုအလုပ်က computer ပေါ်မှာ သုံးလို့ မရအောင် firewall/web filtering တို့လုပ်ထားတယ်ဆိုပါတော့။ ကိုယ်က ကိုယ့်အိမ်မှာ ssh server တစ်ခုကို internet ကနေတဆင့် ဝင်လို့ရအောင် ကိုယ့် home internet router မှာ port forwarding လုပ်ထားတယ်ဆိုရင်ပဲ၊ ကိုယ့်ရဲ့ ssh server ကို SOCKS proxy အနေနဲ့ အသုံးပြုလို့ရပါပြီ။ SSH dynamic forwarding လုပ်ချင်တယ်ဆိုရင်တော့ အောက်က ssh command ကို terminal မှာရိုက်ထည့်လိုက်ရုံပါပဲ။

```text
ssh -D 8080 -f -C -q -N tyla.lin@123.1.2.210
```

![SSH Dynamic Forwarding](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/01/SSH-Dynamic-Forwarding.png?fit=525%2C123&ssl=1)

အထက်က ssh command မှာ အသုံးပြုထားတဲ့ switch တွေကတော့၊ -D ဆိုတာ dynamic forwarding လုပ်မယ်လို့ ဆိုလိုရင်ဖြစ်ပြီး၊ -f ဆိုတာကတော့ background မှာ process ကို fork ပါလို့ ဆိုလိုပါတယ်။ -C ဆိုတာက data ကို link ကနေ မပို့ခင် compress လုပ်မယ်။ -q ဆိုတာ quiet mode မှာ ssh ကို run ဖို့ပြောတာပါ။ နောက်ဆုံး -N ကတော့ ဘာ command မှ ssh session မှာ မ run ဖို့ကို ဆိုလိုတာပါ။ ssh login ကို authenticate လုပ်ပြီးသွားတာနဲ့ ကိုယ့်အလုပ်က စက်ရဲ့ browser ပေါ်မှာ proxy setting ကိုအောက်ကအတိုင်း configure လုပ်ပေးလိုက်ရုံပါပဲ။

![SOCKS Proxy Configuration for SSH dynamic forwarding](https://i1.wp.com/www.itmatic101.com/wp-content/uploads/2020/01/SOCKS-Proxy-Config.png?resize=740%2C604&ssl=1)

အခုဆိုရင်တော့ ကိုယ့်အလုပ်က firewall/web filtering ကို bypass လုပ်ပြီးတော့ ကိုယ့်အိမ်က SSH server ကို proxy အနေနဲ့ အသုံးပြုလို့ရတဲ့အတွက် ကိုယ့် web browser ထဲမှာ သုံးသမျှ traffic အားလုံးဟာ အဲ့ဒီ ssh server ရဲ့ WAN IP ကနေပဲ ခုန်ပြီးတော့ ထွက်သွားမှာဖြစ်ပါတယ်။ ဘာ proxy server မှ setup လုပ်စရာမလိုပဲနဲ့ အခုလို ssh dynamic forwarding လုပ်လိုက်ရုံနဲ့ အားလုံး အဆင့်သင့်ဖြစ်သွားမှာဖြစ်ပါတယ်။ ရိုးရှင်းသလောက် အစွမ်းထက်တဲ့ ssh tunneling ရဲ့ technique တွေဖြစ်ပါ။ SSH tunneling နဲ့ အခြားအခြားသော လုပ်လို့ရတဲ့ နည်းလမ်းတွေအများကြီးရှိပါတယ်။ ဒီ post မှာတော့ လက်တွေ့ အသုံးပြုနိုင်တဲ့ technique သုံးခုလောက်ကို ပြထားတာပဲဖြစ်ပါတယ်။

အခုလောက်ဆို ssh ဟာဘယ်လောက် အသုံးတည့်ပြီးတော့ powerful ဖြစ်သလဲဆိုတာ ရိပ်စားမိလောက်ပါပြီ။ With great power comes with great responsibility ဆိုတဲ့အတိုင်း ssh ရဲ့ port 22 ကို နေရာတကာ port forwarding လုပ်တာမျိုးတော့ best practice မဟုတ်ပါဘူး။ အကယ်လို့ ကိုယ့်ရဲ့ ssh login ဟာ compromise ဖြစ်သွားတယ်ဆိုရင် hacker တွေအတွက် လုပ်ချင်တာလုပ်လို့ရတဲ့ backdoor တစ်ခုဖြစ်သွားနိုင်ပါတယ်။ အဲ့ဒါကြောင့် Fail2Ban လို addtional security layer နောက်တစ်ခုထားနိုင်ရင်တော့ ssh အတွက်စိတ်အချရဆုံး ဖြစ်မှာပါ။ ဒီ post ကိုတော့ ဒီမှာပဲရပ်လိုက်ပါတော့မယ်။ နောက် post တွေမှာလည်း လမ်းကြုံရင် ssh နဲ့ သူ့ရဲ့ အသုံးတည့်တဲ့ဟာလေးတွေကို ထည့်ပြီးတော့ ရှင်းပြသွားပါ့မယ်။
