# လေထုညစ်ညမ်းစပြုလာတဲ့ Linux ရဲ့ Ecosystem

ဒီနှစ်ထဲ \(၂၀၁၉ ခုနှစ်\) မေလ ၇ရက်နေ့ကနေ ၉ရက်နေ့ထိ လုပ်သွားတဲ့ Red Hat Summit 2019 မှာပြောသွားတဲ့ ဖြစ်သွားတဲ့ အကြောင်းအရာတွေကို အခြေခံပြီးတော့ ထင်သာမြင်သာရှိတဲ့ open source နဲ့ Linux တို့ရဲ့ ဦးတည်ရာကို အနည်းငယ် သုံးသပ်ကြည့်ချင်ပါတယ်။ အခုနောက်ပိုင်း open source မှာဖြစ်နေတဲ့ သတင်းတွေကြားလိုက်ရတိုင်း Linux Foundation နဲ့ ဘယ် corporation ကြီးတွေ အတူတူတွဲလုပ်မည့် project တွေအကြောင်းနဲ့ proprietary တွေက ဘယ် open source မှာတွင်တွင်ကျယ်ကျယ်သုံးတဲ့ platform တွေကိုဘယ်လောက်ပေးပြီးတော့ ဝယ်လိုက်တယ်ဆိုတာကြီးပဲ။ open source community ဘက်က မကြိုက်သော်လည်း ရှိတဲ့ဟာလေးတွေနဲ့ ရအောင်ဆက်ပြီးတော့ မဖြစ်ဖြစ်အောင်ကြံဖန်ပြီးတော့ ဆက်သွားနေရပုံရပါတယ်။ စာရေးသူ အနေနဲ့ open source နဲ့ proprietary တွေ အခုလို အုတ်ရောရော ကျောက်ရောရော ဖြစ်လာတာမျိုးကို လက်မခံနိုင်တဲ့သဘောမျိုးမဟုတ်တောင် သိပ်တော့လည်း ဘဝင်မကျပြန်ပါဘူး။ အထူးသဖြင့် နောက်ပိုင်း open source/ free software project တွေမှာ တွေ့နေရတဲ့ အနေအထားလေးတချို့ကို စာရေးသူ သိသလောက်လေးနဲ့ သုံးသပ်ပြချင်ပါတယ်။ ဒီ post မှာ controversial ဖြစ်နိုင်တဲ့ အကျိုးအကြောင်း ဆင်ချင်သုံးသပ်တချို့ပါတဲ့ အတွက် ဒီစာကို ဖတ်တဲ့သူတိုင်းလက်ခံချင်မှ လက်ခံပါလိမ့်မယ်။ စာရေးသူ အနေနဲ့ တကိုယ်ရေ မိမိသိသလောက် အချက်အလက်လေးတွေကို စုစည်းပြီးတော့ ခိုင်ခိုင်လုံလုံဖြစ်အောင်တော့ အတတ်နိုင်ဆုံး ကြိုးစား ဆင်ချင်သုံးသပ်ပြချင်ပါတယ်။ ဒါအပြင် စာရေးသူ တကိုယ်ရေ တွက်ဆချက် တချို့လည်း ပါမှာမို့ ဖြစ်နိုင်တယ် မဖြစ်နိုင်ဘူး၊ မှားနိုင်တယ္ မမှာနိုင်ဘူးဆိုတာတော့ ဒီစာကို ဖတ်တဲ့ စာဖတ်သူတို့ရဲ့လက်ထဲမှာပဲ ထားလိုက်ပါတော့မယ်။ အချက်အလက်တွေကိုတော့ ကိုယ်တတ်နိုင်သလောက် ရှာဖွေပြီးတော့ တင်ပြတာဖြစ်တဲ့ အတွက် မလုံလောက်တာရှိနိုင်သလို၊ အနည်းငယ်ကွာဟ ချက်လေးတွေရှိနိုင်တာမို့ ကြိုပြီးတော့လည်း သတိပေးချင်ပါတယ်။ General public အတွက် အကြောင်းအရာ story နဲ့ ဖြစ်ရပ် event လေးတွေကို ပေါ့ပေါ့ပါးပါး ရေးခြင်းသာ ဖြစ်တဲ့အတွက် စာသင်ကျောင်းတွေမှာ assignment တင်တဲ့ ပုံစံမျိုး reference တွေ ဘာတွေ မထည့်တဲ့အတွက် စာရေးသူကို ပွေမယူစေလိုပါ။ ဘာ label မှ မတတ်ပဲ၊ ဘာ မှန်ဘီလူး မှမပါပဲနဲ့ လက်ဖက်ရည်ဆိုင်မှာထိုင်ပြီးတော့ ရိုးရိုးထိုင်အာတဲ့ ပုံစံမျိုးသွားရတာ ပိုပြီးတော့ စာမြိန်မယ်လို့ စာရေးသူထင်ပါတယ်။

![](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2019/09/Red-Hat-Summit-2019.png?fit=525%2C295&ssl=1)

ဒီအကြောင်းလေးတွေကို စိတ်ထဲမှာ တွေးတောမိတာ ပြီးခဲ့တဲ့ နှစ်အနည်းပိုင်း အတွင်းမှာလို ဆိုရင်လည်း မမှားပါဘူး။ ကိုယ်နဲ့တိုက်ရိုက် မသက်ဆိုင်လို့ တချို့ open source project တွေဘယ်လို ပျောက်ကွယ်သွားသလဲဆိုတာ မသိနိုင်ပေမယ့်၊ အချို့ project တွေကို proprietary တွေ၊ big corporation ကြီးတွေ မည်သို့မည်ပုံ ဝါးမျိုးသွားသလဲဆိုတာတော့ မျက်မြင်ကိုယ်တွေ့လို့ ဆိုရမှာပါ။ စာရေးသူအတွက်တော့ open source / free software project တွေဟာ ကိုယ်ကြိုက်တဲ့အချိန်မှာ download ဆွဲပြီးတော့ စမ်းသပ် လေ့လာနိုင်လို့ နည်းပညာသင်ကြားမှု ဘက်မှာတော်တော်လေးကို အလုပ်ဖြစ်ပါတယ်။ ကိုယ်တိုင်က self-studying ပုံစံမျိုး ကို classroom training မျိုးထက် ပိုပြီးတော့ ကြိုက်တော့ တစ်ခုခုကိုလေ့လာချင်တယ် ဆိုရင် open source / free software project အနေနဲ့ alternative ရှိသလားဆိုတာကို အရင်ရှာတတ်ပါတယ်။ ဟိုတချိန်တုန်းက မိမိကိုယ်တိုင် Linux ရဲ့ Ecosystem နဲ့ open source project တွေဟာ ဘယ်လိုမျိုးလည်းဆိုတာ မသိလို့ နည်းပညာနဲ့ ပတ်သတ်တဲ့ အချို့အပိုင်းလေးတွေမှာ လေ့လာသင်ယူနိုင်မှု အားနည်းခဲ့ပါတယ်။ GNU/Linux ကိုစတင် လေ့လာခဲ့တဲ့ အချိန်ကစလို့ ကိုယ်တိုင်ကိုယ်ကျလေ့လာ နိုင်မှုအားကောင်းလာပါတယ်။ ဒါ့အပြင် Linux community နဲ့ open source community မှာ developer တွေ contributor တွေ ဘာလို့ အခကြေးငွေမယူပဲနဲ့ သူတို့အချိန်တွေ အများကြီး ပေးဆပ်နေနိုင်တာကိုလည်း စာရေးသူ ကောင်းကောင်းကြီးရိပ်စားမိလာပါတယ်။ အရာတိုင်းကို ငွေနဲ့ ပေးဝယ်လို့မရနိုင်ဘူး ဆိုတဲ့ သဘောကလည်း လယ်ပြင်မှာ ဆင်သွားသလို ထင်ရှားလို့နေပါတယ်။

ပြီးခဲ့တဲ့ နှစ်အကုန်ပိုင်းလောက်မှာလည်း မဆီမဆိုင် Microsoft က GitHub လို platform ကိုကောက်ကာငင်ကာ ဝယ်လိုက်ပြန်တော့ open source သမားတွေ တော်တော်လေး စိတ်ရှုပ်လိုက်ရပါသေးတယ်။ တချို့ဆို GitHub မှာ တင်ထားတဲ့ သူတို့ source code တွေနဲ့ repo တွေကို Microsoft ကင်းရှင်းရာ GitLab လို platform ကိုချက်ချင်းဆိုသလို ရွေ့ကြပြောင်းကြလုပ်လိုက်ကြပါတယ်။ အခြေခံအားဖြင့်တော့ Microsoft လို corporation က သူ့ရဲ့ code base ကို ဘယ်သူနဲ့မှ မ share ချင်လို့ အစကတည်းကမှ closed source လုပ်ထားခဲ့တဲ့ဟာ အခုအချိန်ကျမှ open source project တွေတော်တော်များများ အသုံးပြုတဲ့ GitHub ကိုကောက်ပြီးဝယ်လိုက်တော့ ဘယ်လိုနားလည်းပေးရပါ့မလဲ။ PR \(Publicity Stunt\) အရ media တွေအရှေ့မှာတော့ ပြားရည်ကို ကြံသကာ ကပ်ပြီးတော့ Microsoft ဘက်က မည်သို့ပင် ပြောပြော ဘယ်ဖြစ်လို့ ဝယ်လိုက်တယ်ဆိုတဲ့ အကြောင်းကတော့ ရှင်းပါတယ်။ စာရေးသူ အနေနဲ့ ကတော့ open source project တွေ ရဲ့ အပေါ်မှာ Microsoft ထိန်းချုပ်ချင်ပုံရပါတယ်။ open source သမားတွေရဲ့ နေနည်းထိုင်နည်း လုပ်ပုံကိုင်ပုံတွေဟာ Microsoft လို propriety တွေအတွက်တော့ စာရင်းချုပ်လိုက်ရင် အကျိုးအမြတ် မရှိတဲ့ ကိစ္စတွေမို့ ထွေထွေထူးထူး ချပြီးတော့တွက်စရာလိုမယ် မထင်ပါ။ သို့သော် Microsoft ရဲ့ အတိတ်ကို ပြန်ကြည့်လိုက်ရင် ဖြင့် DesktopStandard ကနေနဲ့ ဝယ်လိုက်တဲ့ PolicyMaker ရဲ့ component တွေတော်တော်များများဟာ အခုအချိန်မှာတော့ Microsoft ရဲ့ Group Policy Management Console \(GPMC\) ရယ်လို့သာ လူသိများပါတော့တယ်။ ဆိုလိုရင်းကရှင်းပါတယ် တချိန်ကျရင် Microsoft ရဲ့ banner အောက်မှာပဲ နောက်လူတွေ သိကြတော့မှာပါ။

![](https://i2.wp.com/www.itmatic101.com/wp-content/uploads/2019/09/Github-Acquisition.png?fit=525%2C251&ssl=1)

ဒီ post အစက Red Hat Summit 2019 အကြောင်းကို နည်းနည်းပြန်ပြီးတော့ ဆက်ချင်ပါတယ်။ Red Hat ကို IBM ကဘယ်လောက်နဲ့ ဝယ်လိုက်ပြီးပြီဆိုပြီးတော့ သတင်းထွက်လာပြီးမှ ဒီ event ဖြစ်တဲ့အတွက် IBM ရဲ့ chairman ဖြစ်တဲ့ Ginni Rometty ဆိုတဲ့ အမျိုးသမီး ကိုလည်း ဧည့်သည်အနေနဲ့ ဖိတ်ပါတယ်။ $34 billion နဲ့ နည်းပညာလောကထဲမှာ ဒုတိယ အကြီးဆုံးသော acquisition တစ်ခုဖြစ်တယ်လို့လည်း သိရပါတယ်။ IBM ရဲ့ Chairman Ginni Rometty က အဲ့ဒီ အရောင်းအဝယ် ကိစ္စအတွက်လည်း Red Hat နဲ့ open source သမားတွေကို စိတ်ပူစရာ မရှိဘူး၊ IBM အနေနဲ့ Red Hat ကို သီးသန့် ဆက်လက်ရပ်တည်စေမှာ ဖြစ်တယ်လို့ဆိုသွားပါတယ်။ အခြား ကိစ္စတွေကိုလည်း IBM ရဲ့ chairman က ရွန်းရွန်းဝေအောင်လို့ ပြောသွားတာကို တွေ့ရပါတယ်။ စိတ်ဝင်စားစရာ တစ်ခုက IBM ဘက်က Linux အကြောင်းကိုအများကြီး မပြောသွားပါဘူး။ Red Hat ဘက်ကလည်း IBM ဟာ open source သမိုင်းမှာ အစောဆုံး invest လုပ်ခဲ့တယ်လို့လည်း ဆိုသွားပါတယ်။ ထိုသို့ အပြန်ပြန်အလှန်လှန် ချီးကျူး ပြောဆိုပြီးနောက်မှာတော့ IBM ဟာ Red Hat ကို လက်ရှိအတိုင်း ဆက်လက်ရပ်တည်ခွင့်ပေးမှာဖြစ်ပြီးတော့ Enterprise Cloud Solution နဲ့ AI နည်းပညာတွေ ကို Red Hat နဲ့ ပူးပေါင်း လုပ်ဆောင်သွားမှာကိုလည်း ဆက်ပြောသွားပါတယ်။ အဲ့ဒီ Q&A video ကိုကြည့်ချင်ရင်တော့ ဒီ [Link](https://www.youtube.com/watch?time_continue=641&v=Dhp9mSdK4dU) မှာကြည့်လို့ရပါတယ်။

ပိုပြီးတော့ အံ့အားသင့်စေတဲ့ နောက်တစ်ခုကတော့ Microsoft ရဲ့ CEO Satya Nadella ကြီးကို ဒီနှစ်မှာ ဖိတ်ကြားလိုက်ပြီးတော့ Red Hat က Q&A session တစ်ခုလုပ်ပါတယ်။ အဓိက ကတော့ Red Hat ရဲ့ OpenShift နဲ့ Microsoft ရဲ့ Azure အကြောင်းတွေ ကိုနည်းနည်း မိတ်ဆက်ရင်းနဲ့ Microsoft က open source မှာ ဘယ်လောက်တောင် နေရာယူလာသလဲဆိုတာကို ပြတာပါပဲ။ Red Hat ရဲ့ CEO လည်း စစချင်းမှာပဲ မတွေ့တာကြာပြီဖြစ်တယ်ဆိုတဲ့ အကြောင်း အခုလိုတွေ့ဖို့ကိုလည်း တွေးမထင်ထားဖြစ်တဲ့ အကြောင်းနဲ့ မိတ်ဆက်ပါတယ်။ အဲ့ဒီ Q&A video အပြည့်အစုံကိုကြည့်ချင်တယ်ဆိုရင်တော့ ဒီ [Link](https://www.youtube.com/watch?v=7YYqJZIvw2U) မှာ ကြည့်လို့ရပါတယ်။ အကျဉ်းချုပ်လိုက်ရင်တော့ Cloud အကြောင်းတွေကို တော်တော်လေး ကျယ်ကျယ်ပြန့်ပြန့်ပြောသွားပါတယ်။ ဒီအချက်တွေကို တွက်ချက်ကြည့်လိုက်ရင်ဖြင့် Desktop PC နဲ့ Laptop ရဲ့ operating system ကိုအပြိုင်အဆိုင် လုပ်ရတဲ့ ခေတ်ကတဖြည်းဖြည်း ကျော်လွန်လို့လာပါပြီ။ အမြတ်အစွန်းများများနဲ့ overhead နည်းတဲ့ Cloud Computing ခေတ်ထဲကို တော်တော်လေး ထဲထဲဝင်ဝင်ရှိလာကြပြီဆိုတာရှင်းပါတယ်။ အပွင့်လင်းဆုံးပြောရရင်ဖြင့် အစကတည်း Desktop PC မှာ နေရာယူဖို့ကြိုးစားတဲ့ Microsoft ဟာ အခုအချိန်မှာ Cloud နဲ့ Data Center တွေမှာ အသုံးများတဲ့ Linux ဘက်ကို တဘက်ပြန်လှည့်ပြီးတော့ Marketing ဆင်းနေရပါတယ်။ Microsoft ဟာ mobile နည်းပညာ ဘက်မှာလည်း open source ရဲ့ အလဲထိုးခြင်းကို ခံခဲ့ ရပြီးတဲ့နောက်၊ အခုတခါ Cloud Computing အတွက် ကွင်းဆင်းပြီးတော့ ခံစစ်ယူနေရပါတယ်။ Microsoft ရဲ့ Azure platform မှာ service တော်တော်များများဟာ open source တနည်းအားဖြင့် Linux base တွေဖြစ်တာကိုလည်း Microsoft ဘက်ကငြင်းနိုင်မယ်လို့ မထင်ပါ။ နောက်တဆင့် တက်ဖို့အတွက်က အခုကတည်းက အရင်းအနှီး ရှိဖို့လိုတယ်ဆိုတာကို Microsoft ရဲ့ CEO Satya Nadella သိပုံရပါတယ်။ အခုလည်း Red Hat ရဲ့ OpenShift ဆိုတာ Containerization နည်းပညာကို Microsoft ရဲ့ Azure မှာ integration process အတွက် ကြိုးပမ်းခြင်းတာ ဖြစ်ပါတယ်။ အခုခေတ် Cloud နည်းပညာလို့ပြောလိုက်တာနဲ့ Containerization ဆိုတာကို သီးသန့်ဖယ်ထားလို့ ရတဲ့ ကိစ္စလည်း မဟုတ်ဘူးဆိုတာကို စာဖတ်သူတို့လည်း ရိပ်စားမိမယ်လို့ ထင်ပါတယ်။ ထိုထိုသော အရာတွေကို ထောက်ချင့်ခြင်း အားဖြင့် Microsoft ဘာလုပ်သလဲ၊ IBM ဘယ်သွားနေသလဲဆိုတာကို ထင်သာမြင်သာရှိမယ်လို့ထင်ပါတယ်။

![Red Hat OpenShift](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2019/09/Red-Hat-Container-Stack.png?fit=525%2C273&ssl=1)

အခုလည်း ပြီးခဲ့တဲ့ အပတ်ထဲမှာ Microsoft ဟာ exFAT ရဲ့ specification တွေကို အခြားသော open source platform တွေမှာ adopt လုပ်လို့ရအောင်လို့ patent ကို အနည်းငယ် ဖြေလျှော့ပေးမယ်ဆိုတဲ့ သတင်း ထွက်လာပါတယ်။ FAT filesystem ကို extend လိုက်ထားလို့ exFAT ဆိုပြီး ခေါ်တာပါ။ များသောအားဖြင့် exFAT ကို mobile နဲ့ portable video camera တွေမှာသုံးတဲ့ SD card အတွက်ပဲ တွင်တွင်ကျယ်ကျယ် အသုံးပြုပါတော့တယ်။ Linux နဲ့ BSD ရဲ့ filesystem တွေလောက် အစကတည်း မကောင်းပေမယ့်လည်း Microsoft ရဲ့ Public Stunt \(PR\) အတွက် open source community ကို သူတကယ် ပြောင်းလဲသွားပြီဆိုတာ ပြချင်တယ်လို့ထင်ပါတယ်။ သို့သော် specification ကို share တာဖြစ်ပြီးတော့ open source ကိုတော့ မထုတ်ပေးပါဘူး။ Linux နဲ့ BSD မှာတော့ FUSE လို solution တွေရှိပေမယ့်လည်း Microsoft ရဲ့ exFAT ကို specification မှာ မူတည်ပြီးတော့ open source community က adopt လုပ်မယ်လို့ လည်းသတင်းထွက်လာပါတယ်။ အချို့အတွက်တော့ FUSE က အသုံးပြုဖို့ရာ နည်းနည်းတော့ လက်ဝင်ပါတယ်။ ဘာဖြစ်လာမလဲဆိုတာကို ဆက်လက် စောင့်ကြည့်ရမှာဖြစ်ပါတယ်။ ပြောချင်တာက tech giant တွေဘက်က open source နဲ့ Linux ကိုချစ်သော်လည်း specification သာ share ပုံကို ထောက်ခြင်းအားဖြင့် PR အတွက်သာဖြစ်တယ်ဆိုတာရှင်းပါတယ်။ အပေါ်ယံကြည့်လိုက်ရင်ဖြင့် မျက်စိလည်ချင်စရာကြီးပါ။ Linux ဘက်မှာလည်း နည်းပညာအားဖြင့်ကောင်းပြီးတော့ funding ကောင်းကောင်း မရှိလို့ အင်အားချိနဲ့ လာတဲ့ VyOS လို့ project တွေလည်းရှိပါတယ်။ တဖတ်မှာလည်း Red Hat လို့ funding ကောင်းကောင်းနဲ့ Linux ကို monetization မှာ ကောင်းကောင်း အသုံးချပြီးတော့ Enterprise အတွက် Tech Giant ကြီးတွေနဲ့ ပူးပေါင်းသွားတဲ့ project တွေလည်း ရှိပါတယ်။ ကွာဟမှုကြီးလာတဲ့ open source community ဟာ စိုးရိမ်မူ ရေမျက်နှာပြင်အထက်သို့ တဖြည်းဖြည်းတက်လို့လာပါပြီ။ ဒီတခေါက်လည်း open source ဘက်က သက်လုံကောင်းဖို့လိုနေပါပြီ။ တချိန်က Novell လိုဖြစ်ရပ်မျိုး သမိုင်းမှာ နောက်တကြော့ပြန်အုံးမယ်လို့ ထင်ပါတယ်။ အားလုံးစိတ်ရှည်လက်ရှည်နဲ့ စောင့်ကြည့်ရအုံးမှာ ဖြစ်ပါတယ်။ ဒီလောက်နဲ့ပဲ ဒီ post ကိုရပ်လိုက်ပါတော့မယ်။
