# ကြုံတွေ့ရသမျှ Network Automation အနုပညာ အပိုင်း\(၃\)

အရှေ့တပိုင်းမှာတော့ Ansible အကြောင်းကို အကျဉ်းချုပ်ပြီးတော့ ရှင်းနိုင်သလောက်ရှင်းသွားပြီးတဲ့ နောက်မှာတော့ ဒီတစ်ခုမှာတော့ Python အသုံးတည့်ပုံဆက်သွားလိုပါတယ်။ နောက်ပြီးတော့… Python ကိုဘယ်ကနေ ဘယ်လိုဆက်ပြီးတော့ လေ့လာဖြစ်သလဲဆိုတာကိုလည်း အတိုချုပ်ပြီးတော့ ပြန်လည်မျှဝေပါ့မယ်။ စာရေးသူ Ansible ကို အချိန်ပေးပြီးတော့ ကိုယ်အသုံးပြုမည့် network environment မှာ ဘယ်လိုအသုံးတည့်အောင်လုပ်မလဲဆိုတာ သုံးပတ်လေးပတ်လောက် ရှာဖွေဖတ်ရှုရင်း သူ့ရဲ့ module တွေ အနောက်မှာ .py ဆိုတဲ့ file တွေကို စတင်တွေ့ရှိခဲ့တယ်။ Ansible ရဲ့ module တစ်ခုတစ်ခု ရေးဖို့ဆိုတာ Python ကိုသိဖို့လည်း လိုလာတာကို သိလာတယ်။ ပထမတော့… Ansible မှာ Cisco နဲ့ဆိုင်တဲ့ module တွေကို အသုံးပြုတယ်။ နောက်ပြီးတော့ Huawei နဲ့ အခြားသော vendor တွေကိုပါ ထည့်သွင်း automate လုပ်လိုတာကြောင့် Ansible ရဲ့ module တွေကို ရှာဖွေပြီးတော့ အသုံးပြုကြည့်ဖို့ ကြိုးစားတော့မှ တော်တော်လေးကို မလွယ်တဲ့ ကိစ္စပါ။ Ansible version တစ်ခုနဲ့ တစ်ခု ကွာခြားချက်တွေ အများကြီးရှိနေလို့ အချို့ module တွေဆို သုံးလို့ မရအောင်ကို ဖြစ်နေသေးတယ်။ အဲ့ဒါကြောင့်လည်း… module တစ်ခုတစ်ခုကို ဘယ်လိုတည်ဆောက်ထားသလဲဆိုတာကို သိချင်စိတ်ပေါက်လာရာကနေပြီးတော့၊ module တွေတဲ့ source code တွေကို ဟိုလျှောက်ကြည့်၊ ဒီလျှောက်ကြည့်နဲ့ Python ကို အနောက်မှာအသုံးပြုထားတယ်ဆိုတာကို သဘောပေါက်လာပါတယ်။ Module တိုင်းအတွက် support ကောင်းကောင်းရဖို့ဆိုတာလည်း တော်တော်လေးကို မလွယ်တဲ့ကိစ္စမို့ Python ကို တိုက်ရိုက်အသုံးပြုဖို့ဆိုရင် ဖြစ်နိုင် မဖြစ်နိုင်ဆိုတာကို စဉ်းစားမိတယ်။ အဲ့ဒီမှာတင်… Python နဲ့ automate လုပ်တဲ့ workflow ကို ပိုပြီးတော့ စိတ်ကြိုက်တွေ့မိလို့ Python ဟာ Ansible ရဲ့ module တွေအတွက် အရေးပါသလို၊ Ansible နဲ့ တွဲပြီးတော့ အသုံးပြုလိုတယ် ဆိုရင်လည်း ဖြစ်နိုင်တယ်လို့ သိလာတဲ့နောက်မှာ အသိသစ်တစ်ခုသိလိုက်ရတာတော့ automation မှာ ဘာဘောင်မှ မရှိပါဘူး။ ကိုယ်လုပ်ချင်တာကို ကိုယ်သိသလောက် scripting skill နဲ့ programming language တွေအသုံးပြုပြီးတော့ ပေါင်းစပ်ရတဲ့ အနုပညာတစ်ခု ပဲဖြစ်တယ်ဆိုတာပါပဲ။

စာရေးသူ ကိုယ်တိုင်တွေ့ကြုံရတဲ့ အတွေ့အကြုံအရဆိုရင်တော့ ကိုယ်ပိုင် automation project လေးတွေက စလုပ်ရင်းနဲ့ပဲ နည်းနည်းချင်းစီ လေ့လာရတာပိုပြီးတော့ ကောင်းပါတယ်။ ဒါမှမဟုတ်ရင် ကိုယ်တိုင်က Computer Science \(CS\) နဲ့ ကျောင်းပြီးထားတယ်၊ programming fundamental လဲပိုင်တယ်၊ framework တွေကိုလည်း ကောင်းကောင်းနားလည် ထားတယ်ဆိုရင်တော့ အတိုင်းထက်အလွန်ပါပဲ။ စာရေးသူ အတွက်တော့ sysadmin တစ်ယောက်၊ network engineer တစ်ယောက်အနေနဲ့ DevOps ဘက်ကိုလိုက်ဖို့ဆိုတာ အသိပညာ ကွာဟမှု \(knowledge gap\) နဲ့ အတတ်ပညာ ကွာဟမှု \(skill gap\) တွေအပြင်၊ စိန်ခေါ်မှုတွေ မြောက်များစွာ ရှိပါတယ်။ ကိုယ်တိုင်မှာက programming fundamental ကို ဟိုတကွက် ဒီတကွက် အနည်းအကျဉ်း လေ့လာထား၊ သိထားသော်လည်း programming နဲ့ coding အပိုင်းမှာတော့ ဘာမှ သိပ်ပြီးတော့ သိတာလည်းမဟုတ်ပါ။ အရှေ့အပိုင်းတွေမှာ ပြောခဲ့သလိုပဲ လိုအပ်ရင် လိုအပ်သလိုတော့ script လေးတွေတော့ ရေးခဲ့ဖြစ်ပါတယ်။ နောက်တစ်ခု ပိုဆိုးတာက automation နဲ့ orchestration လုပ်ဖို့အတွက် tool set နဲ့ တစ်ခုချင်းစီရဲ့ အသုံးပြုပုံ အပြင်၊ တစ်ခုနဲ့ တစ်ခုချိတ်ဆက်ပြီးတော့ ပြုလုပ်လို့ရတဲ့ workflow ကို နားလည်ဖို့ကတော့ အချိန်အများကြီးလိုတယ်။ ဒါတောင်မှ Python လို language နဲ့ တွဲပြီးတော့ အသုံပြုနိုင်တဲ့ Django တို့၊ Flask တို့လို web framework တွေမပါသေးပါဘူး။ ကိုယ်လိုက်ပြီးတော့ လေ့လာချင်တယ်ဆိုရင်တော့ automation platform တစ်ခုလုံးကို end-to-end ဆောက်လုပ်နိုင်တဲ့အထိ လေ့လာစရာ မကုန်ပါဘူး။ ဒီအတွက်… ကိုယ်လိုတဲ့ အပိုင်းကို လိုသလို သိသလောက် တတ်နိုင်သလောက် လေ့လာပြီးတော့ ကိုယ်ပိုင် project သေးသေးလေးတွေက စရင် ပိုပြီးတော့ ခရီးပေါက်နိုင်မယ်လို့ထင်ရပါတယ်။ အစပိုင်းမှာ အခက်အခဲတွေ၊ လုပ်နိုင်သမျှအမှားတွေ ပေါင်းများစွာနဲ့ ဖြတ်သန်းလိုက်ပါ။ လေ့လာရင်းနဲ့ ပိုပြီးတော့ သိလာတဲ့ တစ်နေ့ကြရင် ကိုယ်မှားခဲ့ အမှားလေးတွေကို ဂရုဏာသက်မိပါလိမ့်မယ်။ ဪ… ငါတော့ဖြင့် လွယ်လွယ်လေး လုပ်လို့ရတဲ့ အဆင့်လေးတွေကို ဒီလိုကြီး ပင်ပင်ပန်းပန်း ခဲရခဲဆစ် အများကြီး ပေပွနေအောင်လုပ်ခဲ့ပါလာဆိုပြီးတော့ ကိုယ်ဟာကို ပြုံးမိနေပါလိမ့်မယ်။ နောင်အခါ လုပ်ငန်းဆိုင်ရာ ကျွမ်းကျင်တတ်မြောက်ဖို့ ဆိုရင်တော့ ပထမဆုံးအဆင့်အနေနဲ့ မရှက်မကြောက် အများကြီးမှားရဲဖို့လိုပါလိမ့်မယ်။ ကဲ… လိုရင်းဖြစ်တဲ့ Python အကြောင်းလေးကို ခပ်သွက်သွက်လေးသွားလိုက်ရအောင်…

### Python မိတ်ဆက်

Python ကိုတော့ Guido van Rossum ဆိုတဲ့ ပုဂ္ဂိုလ်က ၁၉၉၁ တွင်းမှာ စတင်မိတ်ဆက်ပေးလိုက်ပါတယ်။ သူကတော့ Netherlands နိုင်ငံသား Dutch လူမျိုးတစ်ယောက်ဖြစ်ပါတယ်။ လူတွေကတော့ သူကို Python programming language ရဲ့ Benevolent Dictator For Life \(BDFL\) ဆိုတော့ အသိများကြပါတယ်။ ၂၀၁၈ ခုနှစ် ဇွန်လိုင်လ မှာတော့ သူက တသက်စာ အနားယူခရီးထွက် မယ်ဆိုပြီးတော့ Python community တစ်ခုလုံးကို ဒီအတိုင်း ကြိုက်သလိုသာ လုပ်ဆိုပြီးတော့ ထားခဲ့တဲ့ လူပါ။ အဲ့ဒီမတိုင်ခင် သူက Python မှာဖြစ်သမျှ ကိစ္စကို သူကိုယ်တိုင် အားလုံးကို ကိုင်တွယ် ဆုံးဖြတ်တဲ့ BDFL လို့ အားလုံးကသဘောတူထားပါတယ်။ ၂၀၁၈ ခုနှစ် Python community ကနေထွက်သွားတဲ့ အချိန်မှာတော့ community ကို ခင်ဗျားတို့ ကြိုက်သလိုသာ လုပ်ကြလို့ ဆိုပြီးတော့ ထားခဲ့တာပါ။ အဲ့ဒီ သတင်းဟာ Python community အတွက်အတော်လေးကို ခြောက်ခြားစရာ သတင်းတစ်ခုပါ။ BDFL ကိုယ်တိုင်က နောက်ဆုတ်သွားပြီဆိုတော့ Python community အတွက် ဘာလဲပေါ့နော်။ Guido van Rossum ဆီမှာလည်း သူပဲသိနိုင်တဲ့ အကြံဉာဏ်တွေ ရှိကောင်းရှိနိုင်ပါတယ်။ သူတစ်ယောက်တည်း Python community ကို ထိန်းချုပ်ဖို့ဆိုတော့ ရေရှည်မှာ လက်တွေ့မကျနိုင်တာမို့ သူက community လက်ထဲမှာ ဒီအတိုင်း ထားသွားခဲ့တာလည်း ဖြစ်ကောင်းဖြစ်နိုင်တယ်။ ပြန်စဉ်းစားကြည့်ရင် သူဘက်မှာ ရည်ရွယ်ချက် ရှိရှိနဲ့ ဘာတွေဖြစ်မလဲဆိုတာစောင့်ကြည့်တာလည်း ဖြစ်နိုင်သလို၊ အမှန်တကယ် အနားယူတာလည်းဖြစ်နိုင်တယ်လို့ ဆိုရမှာပါ။ မည်သို့ပင် ဖြစ်စေကာမူ… အဲ့ဒီလိုလုပ်လိုက်တော့ Python community ဟာ အရင်ထက်အရှိန်အဟုန်ကောင်းစွာနဲ့ ပြန်လည် တည်ဆောက်ယူဖို့ကို ကြိုးစားလိုက်တာဖြင့် အခုဆိုတော်တော်လေးကို ဟုတ်နေပါပြီ။ လက်ရှိအချိိန်ထိတော့ ဆုံးဖြတ်ချက်ချဖို့အတွက် board member ၅ ယောက် ကို Python Steering Council လို့ခေါ်တဲ့ အဖွဲ့မှာ နှစ်စဉ်ရွေးကောက်လာခဲ့တာ အခုဆိုရင် Guido van Rossum ကိုယ်တိုင် လက်ရှိ Python Steering Council ရဲ့ member တစ်ယောက်ပြန်ပြီးတော့လုပ်နေပါတယ်။ သူကိုယ်တိုင်က diversity ကို မြတ်နိုးတာကြောင့် အဖွဲ့ဝင်တွေထဲမှာ ယောက်ျား မိန်းမ မခွဲခြားပဲ အားလုံး ပါစေနိုင်ရန်တိုက်တွန်း အားထုတ်လေ့ရှိပါတယ်။

![Guido van Rossum &#x2013; Benevolent Dictator For Life \(BDFL\) \(Origin: Wikipedia &#x2013; Guido van Rossum\)](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/06/Guido-van-Rossum.jpg?fit=525%2C350&ssl=1)

Python programming language ဟာ ABC ဆိုတဲ့ programming language ကိုအစားထိုးဖို့အတွက် ၁၉၈၀ ခုနှစ်နှောင်းပိုင်းမှာ စတင် သန္ဓေယူပါတယ်။ ABC ဟာလည်း SETL ဆိုတဲ့ language ကနေပြီးတော့ ဆင်းသက်လာတယ်လို့သိရပါတယ်။ Programming language တစ်ခုဖြစ်လာပုံကို လိုက်ပြီးတော့လေ့လာကြည့်ပြန်တော့ Linux ရဲ့ distro တွေအဆင့်ဆင့် ဆင်းသက်လာပုံနဲ့ ဆင်တူလို့နေပြန်ရော။ အစဉ်အလာအရတော့ ထိပ်ဆုံးမှာ အခြေခံတော်တော်များများကို ခြုံငုံနိုင်တဲ့ C တို့လို high-level programming နဲ့ Assembly တို့လို low-level programming language တွေရှိတယ်။ ထိုမှတဆင့် ပိုပြီးတော့ လွယ်တဲ့ ကောင်းမွန်တဲ့ language တွေကို Computer Science \(CS\) သမားတွေက အဆင့်ဆင့် တိုးတက်လာအောင် ကြုံဆောင်ရင် အခုလိုမျိုး Python လိုမျိုး human-readable language တွေထွက်လာပြန်ပါတယ်။ စာရေးသူ အနေနဲ့ အပြင်သင်တန်းတွေနဲ့ ကျောင်းမှာ လုပ်ရတဲ့ project တွေအတွက် C/C++၊ Java၊ C\# နဲ့ Perl တို့လို Language တွေကိုလေ့လာဖူးသော်လည်း၊ Python ကတော့ အခုနောက်ပိုင်းမှ စတင် စမ်းသပ်ရင်း အသုံးပြုခြင်းဖြစ်ပါတယ်။ တော်တော်လေးကို နားလည်ရလွယ်တဲ့ programming language တစ်ခုဖြစ်သလို၊ အသုံးပြုဖို့အတွက်လည်း နေရာတော်တော်များမှာ ဘောင်ဝင်လို့ နှစ်သက်မိခြင်းပါ။ ပြီးတော့ Linux မှာလိုပဲ philosophical thinking တွေ Python programming language မှာလည်း ရှိတယ်။ အခြေခံအားဖြင့် ၅ချက်ကတော့…

* Beautiful is better than ugly. \(လှတာဟာ အကျဉ်းတန်တာထက်တော့ ပို၍ကောင်း၏။\)
* Explicit is better than implicit. \(ရှင်းလင်းပြတ်သားတာဟာ သွယ်ဝိုက်တာထက်တော့ ပို၍ကောင်း၏။\)
* Simple is better than complex. \(ရိုးရှင်းတာဟာ ရှုပ်ထွေးတာထက်တော့ ပို၍ကောင်း၏။\)
* Complex is better than complicated. \(ရှုပ်ထွေးတာဟာ နားလည်ရခက်ထက်တော့ သာသေး၏။\)
* Readability counts. \(အမြင်နဲ့ ဖတ်ရလွယ်ဖို့အတွက်လည်း ထည့်တွက်ရမည်။\)

အဓိပ္ပာယ်ဟာ ရှင်းလင်းသလောက် လက်တွေ့မှာ ထိုအချက်လေးတွေဟာ programming language တစ်ခုကို တည်ဆောက်ယူကြတဲ့ အခါကျော်ကျော်သွားတတ်လွန်းလို့နဲ့ တူတယ်။ Python programming language ဟာလည်း ထိုထိုသော အချက်လေးတွေနဲ့ ကိုက်ညီမူရှိစေရန် အားထုပ်ထားတဲ့ အခြေခံကောင်းသော language ရယ်ပါ။ ဒီလောက်ဆိုရင် Python ကို အနည်းငယ် မိတ်ဆက်ပြီးသား ဖြစ်ပြီလို့ထင်ပါတယ်။ လက်တွေ့ Python ဘက်ကို အနည်းငယ် ဆက်သွားလိုက်ရအောင်။

### လက်တွေ့ Python

Python ရဲ့ syntax structure နဲ့ library တွေအကြောင်းကို ပြောရင် တော်တော်နဲ့ ကိုပြီးနိုင်မယ်လို့ မထင်ပါ။ ဒီ post ရဲ့ မူလ လိုရင်းကတော့ Python code တွေကို network device တွေနဲ့ ဘယ်လိုမျိုးတွဲပြီးတော့ network automation အတွက် လက်တွေ့မှာ အသုံးချနိုင်သလဲဆိုတာ ပြချင်တာဖြစ်တဲ့အတွက် စာရေးသူ scenario တစ်ခု နဲ့ အဲ့ဒီ scenario မှာဖြစ်နေတဲ့ ပြဿနာကို ဖြေရှင်းပုံကို solution code အနေနဲ့ ထည့်သွင်း ဖော်ပြပါ့မယ်။

#### Scenario

ဒီ scenario မှာတော့ Cisco ရဲ့ ASR 1006-x series router တွေမှာ သုံးတဲ့ IOS XE အတွင်းရှိတတ်တဲ့ software bug တစ်ခုအတွက် Python ကို အသုံးချပြီးတော့ conflict ဖြစ်နေတတ်တဲ့ uidb ကို ရှာဖွေရမှာပါ။ Cisco ASR 1006-x series router တွေမှာသုံးထားသော IOS XE ရဲ့ အချို့ version တွေမှာ known issues လေးတွေရှိနေတတ်ပါတယ်။ အဲ့ဒီထဲမှာမှ သူ့ရဲ့ port-channel အတွက် အသုံးပြုတဲ့ Rx/Tx uidb ဆိုတဲ့ နံပါတ်ဟာ port-channel နဲ့ port-channel ရဲ့ subinterface တစ်ခု ဖန်တီးတိုင်းမှာ process id လိုပဲ uidb တစ်ခုစီ ကို IOS XE ပေါ်မှာ ဖန်တီးပြီးတော့ context အနေနဲ့ အသုံးပြုထားတာပါ။ ASR 1006-x series router တွေကို reboot လုပ်လိုက်တိုင်း အဲ့ဒီ uidb တွေဟာ အမြဲတည်း ပြောင်းလဲသွားတတ်ပါတယ်။ ဒီတော့… အကြိမ်ရေတော်တော်များများ device တစ်ခုတည်းပေါ်မှာတင် port-channel တစ်ခုရဲ့ Rx uidb နဲ့ အခြားသော port-channel တစ်ခုရဲ့ Tx uidb တစ်ခု နဲ့ သွားပြီးတော့ တူနေတတ်ပါတယ်။ Router ရဲ့ ပုံမှန် routing operation အတွက်တော့ အပေါ်ယံမှာ ပြဿနာကြီးကြီးကျယ်ကျယ် မရှိလှပါဘူး။

![Cisco ASR 1006-x Router](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/06/Cisco-ASR-1006-x-Serie.png?resize=569%2C358&ssl=1)

သို့သော်… အခိုက်မသင့်ရင်တော့ အဲ့ဒီ Rx နဲ့ Tx မှာ တူနေတဲ့ port-channel နှစ်ခုဟာ အခုလိုပြဿနာတတ်ပါတယ်။ ဆိုကြပါတော့… ပထမ port-channel ရဲ့ Rx မှာ interface သို့မဟုတ် routing protocol တွေ flap ဖြစ်တဲ့အခါမှာတော့ ဒုတိယ port-channel ရဲ့ Tx မှာ လာပြီးတော့ flap ဖြစ်တဲ့ အတွက် Core Routing မှာ Bidirectional Forwarding Detection \(bfd\) ကို implement မလုပ်ထားဘူးဆိုခဲ့ရင် တော်တော်လေးကို ဒုက္ခပေးတတ်တဲ့ IOS XE ရဲ့ software bug တစ်ခုပါ။ ဒီ router တွေ ပေါ်မှာ port-channel နှစ်ခု သုံးခုဆိုရင် ပြဿနာ မရှိနိုင်သော်လည်း၊ MPLS ရဲ့ core routing အတွက်တော့ တစ်ခုချင်းစီ လိုက်ပြီးတော့ စစ်ဖို့ဆိုတာမလွယ်ပါဘူး။ အဲ့ဒီ conflict ဖြစ်နေတဲ့ uidb တွေကို ရှာဖို့အတွက် Ansible နဲ့ Bash သို့မဟုတ် Ansible နဲ့ Python ကို တွဲပြီးတော့ အသုံးပြုနိုင်ပါတယ်။ သို့သော်… ဒီ post မှာတော့ Python ကြီးပဲ သီးသန့် အသုံးပြုပြီးတော့ conflict ဖြစ်နေတဲ့ port-channel နဲ့ သူ့ရဲ့ uidb ကိုရှာဖွေပါ့မယ်။ netmiko library ရဲ့ ConnectHandler module ကို ssh session အတွက် အသုံးပြုထားပါတယ်။ အောက်မှာတော့ Python ရဲ့ codelet လေးကို ဖော်ပြပေးထားပါတယ်။ အခုထက်ကောင်းအောင်တော့ ထပ်ပြီးတော့ ပြင်ရေးရင်တော့ ရပါသေးတယ်။ သို့ပေမယ့်လည်း… Python code ကို network automation မှာ အသုံးပြုဖို့ အကြမ်းထည် တည်ဆောင်နိုင်ခြင်း မြင်အောင်ပြလိုတဲ့ ဆန္ဒနဲ့ ပိုပြီးတော့ compact ဖြစ်အောင်၊ ပိုပြီးတော့ code base ကောင်းမွန်လာ မရည်ရွယ်ပါ။ ကဲရဲ့လိုက ကြိုက်သလို ကဲရဲ့ နိုင်၏။

```text
from netmiko import ConnectHandler
import getpass
import sys
from datetime import datetime

# define vendor platform
platform = 'cisco_ios'

# obtain username and password
usr = input("Username: ")
pwd = getpass.getpass("Password: ")

# open devices list inventory file which needs to be created by hand
file = open('dev')

# write output on screen to output_log.txt
log = open("output_log.txt","w")
start_time = datetime.now()

#connect each device to pull config individually
for line in file:
    print ("\n===================================")
    print ("\nGetting config from " + (line) + "\n===================================\n")
    log.write ("\n===================================")
    log.write ("\nGetting config from " + (line) + "\n===================================\n")
    host = line.strip()
    net_connect = ConnectHandler(device_type=platform, ip=host, username=usr, password=pwd)
    net_connect.enable()
        
    # split lines based on port-channel interface only output
    olist = net_connect.send_command("sh ip int bri | i Port-channel").splitlines()
        
    # dict for port-channel and it's status values
    pslist = {
        "po": [p.split()[0] for p in olist], #port-channel 
        "sa": [s.split()[5] for s in olist]  #status
    }
    
    polen = len(pslist["po"])
    a = 0
    count = 0 
    
    # outer loop for Rx
    while a < polen:
        if pslist["sa"][a] == "up":
            Rxuidlist = net_connect.send_command("show platform hardware qfp active interface if-name " + pslist["po"][a] + " info | in uidb")
            Rxlist = Rxuidlist.splitlines()
            Rxuid = Rxlist[0].split()[2]
            
            b = 0
            
            # inner loop for Tx
            while b < polen:
                Txuidlist = net_connect.send_command("show platform hardware qfp active interface if-name " + pslist["po"][b] + " info | in uidb")
                Txlist = Txuidlist.splitlines()
                Txuid = Txlist[1].split()[2]
                if Rxuid == Txuid:
                    count += 1
                    print (str(count) + ". " + pslist["po"][a] + "'s Rx uidb: "+ Rxuid + " conflicts with " + pslist["po"][b] + "'s Tx uidb: " + Txuid + " on " + (line))
                    log.write (str(count) + ". " + pslist["po"][a] + "'s Rx uidb: "+ Rxuid + " conflicts with " + pslist["po"][b] + "'s Tx uidb: " + Txuid + " on " + (line))
                b += 1 
        a += 1

# total time taken time stamp               
end_time = datetime.now()
total_time = end_time - start_time
print ("\n\n" + "## Total Time Taken ##")
print (total_time)
log.write ("\n\n" + "## Total Time Taken ##")
log.write (str(total_time))
log.close()
```

ဒီထက် Python နဲ့ programming fundamental ဆိုင်ရာ အကြောင်းတွေကို ပိုပြီးတော့ နားလည်ရင်တော့ class တွေ၊ function တွေကို အသုံးပြုပြီးတော့ ဒီထက်ရှုပ်ထွေးတဲ့ code တွေကို ဖန်တီးနိုင်ပါတယ်။ ဒီ codelet မှာတော့ Python ရဲ့ code ကို အသုံးပြုပြီးတော့ networking device ပေါင်းမြောက်များစွာ ပေါ်မှာ native IOS command တွေ အသုံးချပြီး ကိုယ်လိုတဲ့အရာ မှန်သမျှကို ရိုးရှင်းလှတဲ့ automated workflow တစ်ခု တည်ဆောင်နိုင်ကြောင်း ပြချင်တာပါ။ DevNet ပိုင်းကို ဆက်လိုက်ရင်တော့ data parsing/data format တွေဖြစ်တဲ့ XML၊ JSON နဲ့ YAML လို format တွေအပြင် YANG လို data modelling အကြောင်းတွေကို ထပ်မံ့ တိုးချဲ့လေ့လာ နိုင်ပါတယ်။ ဒီ post မှာတော့ အထက်က Python script ကို သုံးတဲ့နေရာမှာလည်း device အရေအတွက် များရင် များသလောက် မိနစ်ပေါင်းများစွာ ကြာနိုင်သည့်တိုင်အောင်မှ manual process ထက်တော့ အများကြီးသက်သာသွားပါပြီ။ နောက်ပိုင်းမှပဲ… အချိန်ရှိရင် ရှိသလောက် Python နဲ့ ပတ်သတ်တဲ့ အသေးစိတ်အကြောင်းလေးတွေကို ဆက်လက် ရေးသားသွားပါ့မယ်။ အခု “ကြုံတွေ့ရသမျှ Network Automation အနုပညာ” အကြောင်းကို ဒီအပိုင်း ဖြစ်တဲ့ အပိုင်း \(၃\) နဲ့ ပဲရပ်လိုက်ပါတော့မယ်။ Automation ရဲ့ အနုပညာ အကြမ်းဖျင်းကိုတော့ ဒီစာကို ဖတ်တဲ့သူတွေ အနေနဲ့ တီးမိခေါက်မိမယ်လို့ ယုံကြည်ရပါတော့လေသတည်း။

