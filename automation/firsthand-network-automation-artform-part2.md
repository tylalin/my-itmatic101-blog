# ကြုံတွေ့ရသမျှ Network Automation အနုပညာ အပိုင်း\(၂\)

ဒီ တပိုင်းမှာတော့ Ansible အကြောင်းကို အရင်ဆုံးရှင်းချင်ပါတယ်။ Ansible ကိုတော့ Red Hat က maintain လုပ်တဲ့ project တစ်ခုပါ။ Michael DeHaan ဆိုတဲ့ ပုဂ္ဂိုလ်ဆီကနေပြီးတော့ Red Hat ဟာ ၂၀၁၅ ခုနှစ်မှာ ပြန်ဝယ်လိုက်ပြီးတော့ ဆက်ပြီးတော့ develop လုပ်နေတာလည်းဖြစ်ပါတယ်။ Unix-like environment တွေမှာ ssh ကိုအားပြုပြီးတော့ device configuration တွေကို manage လုပ်တဲ့၊ orchestrate လုပ်တဲ့ tool set တစ်ခုပါ။ အခြားသော orchestration tool တွေနဲ့ မတူတဲ့ အချက်ကတော့ Ansible ကို အသုံးပြုဖို့အတွက် client ဘက်မှာ ဘာ agent မှ install လုပ်စရာမလိုတာပဲဖြစ်ပါတယ်။ နောက်ပြီးတော့ cross-platform ဖြစ်တဲ့အတွက် Windows လို environment မှာလည်း Windows Remote Management ကိုအသုံးပြုပြီးတော့ PowerShell ကို အသုံးပြုနိုင်တဲ့အတွက် အသုံးပြုဖို့ရာအတွက် တော်တော်လေးကို အဆင်ပြေပါတယ်။ Ansible မှာ အလွယ်တကူ တစ်ကြောင်းတည်းနဲ့ ပြီးမယ့် command ဆိုရင် သူ့ကို ad-hoc ပုံစံမျိုးနဲ့ အသုံးပြုလို့ ရပါတယ်။ ဒါမှမဟုတ်ပဲနဲ့ အဆင့်ပေါင်းများစွာ လုပ်ရမယ်၊ command တွေကို အခေါက်ခေါက်အခါခါလုပ်ရမယ်ဆိုရင်တော့ Ansible Playbook ကို အသုံးပြုနိုင်ပါတယ်။ Folder structure တစ်ခုထဲမှာ inventory list တွေ၊ role တွေ နဲ့ အခြားသောလိုအပ်တဲ့ variable တွေအပြင် ssh မှာသုံးမယ့် password တွေကို လုံခြုံစွာသိမ်းထားနိုင်တဲ့ vault လိုဟာမျိုးတွေလည်း ပါတာကြောင့် အသုံးပြုတဲ့နေရာမှာ နားလည်ထားရမယ့် အစိတ်အပိုင်းတွေများစွာပါဝင်ပါတယ်။ Ansible ရဲ့ documentation ဟာတော်တော်လေးကို စုံစုံလင်လင်ရှိတဲ့အတွက် မသိတာတွေကိုလည်း အလွယ်တကူရှာဖွေဖို့ရာလည်း လွယ်ကူပါတယ်။ Ansible အကြောင်းကို အလုံးစုံတော့ ဒီ post မှာမရှင်းလိုပါ။ အဓိကအနေနဲ့တော့ စာရေးသူအတွက် Ansible ဟာ network automation မှာဘယ်လို နေရာကနေပါဝင်ခဲ့သလဲဆိုတာတယ်။ လုပ်ငန်းခွင့်မှာ အခြေခံကနေပြီးတော့ အဆင့်မြင့်မြင့် Ansible ကို လက်တွေ့ အသုံးပြုနိုင်မယ့် ပုံစံအကျဥ်းချုပ်ကိုသာတင်ပြလိုတာပါ။ စာရေးသူကိုယ်တိုင်လည်း စတင်လေ့လာနေကာစမို့ ရှင်းပြတဲ့နေရာမှာလိုအပ်တာတွေလည်း ရှိနိုင်တာမို့ ဂရုဏာစိတ်လေးနဲ့ နားလည်စေချင်လိုပါတယ်။

![](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/05/Ansible-1.png?fit=525%2C341&ssl=1)

### Ansible နဲ့ တွေ့ဆုံခြင်း

စာရေးသူ Ansible ကို အရင်တုန်းက ကြားသာကြားဖူးပြီးတော့ ဘယ်လိုသုံးရသလဲဆိုတာလည်းမသိသလို၊ ဘာအတွက်သုံးသလဲဆိုတာလည်း သဲသဲကွဲကွဲ မသိခဲ့ပါဘူး။ ကိုယ်နဲ့ မဆိုင်သလို၊ အလုပ်အတွက် အသုံးပြုရမှာမဟုတ်တဲ့အတွက် Ansible ကိုလေ့လာဖို့လည်း အကြောင်းမရှိခဲ့ပါဘူး။ လွန်ခဲ့တဲ့တစ်နှစ် နှစ်နှစ်လောက်မှာမှ အလုပ်ခွင်မှာ networks team နဲ့တွဲပြီး အလုပ်လုပ်ရဖို့ အကြောင်းပါလာတော့ Cisco နဲ့ Huawei ရဲ့ networking devices တွေနဲ့ production မှာထိတွေ့ဖို့ ဖြစ်လာပါတော့တယ်။ ကိုယ်တိုင်က network ဘက်မှာ CCNA လောက်သာသာ skill နဲ့ CCNP၊ CCIE တို့လို senior network engineers တွေနဲ့ တွဲပြီးတော့ လုပ်လာရတဲ့အခါမှာ ကိုယ့်ရဲ့ networking skill ဘယ်လောက်ပဲရှိတယ်ဆိုတာကို ရှင်းရှင်းလင်းလင်း သိလာရပါတယ်။ တဘက်မှာလည်း CCNPတို့ CCIE တို့ ကိုင်ထားတဲ့ senior network engineer တွေလည်း အလုံးစုံမသိတာကို တဖြည်းဖြည်းတော့ သိလာရပါတယ်။ Enterprise network နဲ့ Service Provider network မှာသုံးတဲ့ networking technology တွေအများကြီးနဲ့ နေ့တိုင်း ထိတွေ့ပြီးတော့ လုပ်ကိုင်နေကြတဲ့ networking ဘက်မှာ အားသာတဲ့ senior network engineer တွေဟာ ရှေးရိုးစွဲ networking professional သီးသန့်ဆိုတာလည်းသိလာရပါတယ်။ ရှင်းရှင်းပြောရရင် Cisco နဲ့ Huawei တွေလို platform တွေမှာ train ထားတဲ့ network engineer တွေဟာ သူတို့အားသန်တဲ့ platform မှာပဲလှည့်ပြီးတော့ network ရဲ့ architecture design နဲ့ configuration မှာ network device တစ်ခုချင်းစီကို configure လုပ်ဖို့၊ setup လုပ်ဖို့ ကို ဝင်မလေးကြပါဘူး။ Troubleshoot လုပ်တဲ့အခါမှာလည်း debug ကိုသုံးပြီးတော့ syslog တွေကိုကြည့်ပြီးတော့ ဘယ်နားသွားပြီးတော့၊ ဘယ် device မှာဖြင့် ဘယ် protocol ဟာမှာ ဘယ်လိုပြဿနာတတ်နေသလဲဆိုတာကို ကိုယ့်မျက်စိရှေ့မှာ အစပိုင်းလုပ်ပြတော့ အံ့အားသင့်ခဲ့ရပါတယ်။ အားကျစရာတစ်ခုဖြစ်ခဲ့သလို၊ တပိုင်းနက်တည်းမှာပဲ အဲ့ဒီထက်လွယ်အောင်လုပ်လို့ မရတော့ဘူးလားလို့ လည်းကိုယ်ဟာကို မေးခွန်းထုတ်မိပါတယ်။ စာရေးသူ ဟိုးအရှေ့ post မှာရေးခဲ့သလိုပဲ ကိုယ်က network team ထဲမှာစပြီးတော့ လုပ်ကာစမို့ level 1 လုပ်ရမယ့်ဟာ အကုန်လုံးနီးပါးကို ကိုယ့်လက်နဲ့ ကိုလုပ်ဖို့ကို senior engineer တွေက ကိုယ့်ကို assign လုပ်ပါတယ်။ ပြဿနာက ကိုယ်ကပျင်းတော့ အစပိုင်းမှာ ထပ်ကာသလဲလဲ လုပ်ရတဲ့ အလုပ်မျိုးကို စာရေးသူ မကြိုက်ခဲ့ပါဘူး။ စာရေးသူရဲ့ background က sysadmin မို့ systems ဘက်မှာလည်း ကိုယ်တတ်နိုင်သလောက် script တွေကို ရေးပြီးတော့ automate လုပ်လေ့ရှိတဲ့အတွက်၊ network ဘက်မှာလည်း အဲ့လိုမျိုး လုပ်လို့မရဘူးလားဆိုတော့ ရှာပုံတော်စထွက်ရာကနေပြီးတော့ ပထမဆုံး ကိုယ်ကဘာလုပ်ချင်တာလည်းမသိတာတကြောင်း၊ ဘယ်လိုလုပ်ရမှာလဲဆိုတာ မသိတာတကြောင်းမို့ အစပိုင်းမှာသိပ်ပြီးတော့ ခရီးမပေါက်လှပါဘူး။ သို့သော်ကိုယ်ဘာလိုချင်တာလည်း ဆိုတာတော့ ခပ်ရေးရေးသိသလိုရှိခဲ့ပါတယ်။ အဲ့ဒါကတော့ repetitive task တွေ အားလုံးကို automate လုပ်ချင်ပါတယ်။ ကိုယ်တနေ့တနေ့ ရုံးမှာထိုင်ပြီးတော့ ဒီတစ်ခုတည်းကိုပဲ ထပ်ကာထပ်ကာလုပ်တာမျိုး မလုပ်ချင်တော့ပါ။ အသစ်အသစ် တွေကို ပိုမိုသိချင်တဲ့စိတ်နဲ့ လေ့လာဖို့ကိုသာ ပိုပြီးတော့ အားသန်ခဲ့ပါတယ်။

![](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/05/Automating-Automation-1.jpg?resize=625%2C415&ssl=1)

အစမှာတော့… parallel ssh sessions တွေကို တပြိုင်နက်တည်း တူညီတဲ့ commands တွေကို ရိုက်ထည့်ဖို့ရာအတွက် pssh လိုမျိုး tool တွေကိုသုံးဖို့အတွက် အကြံရခဲ့ပါတယ်။ တကယ်တန်းမှာ ကိုယ်ထင်ထားသလောက် အလုပ်မဖြစ်တာကို တစ်ပတ်လောက် ဟိုစမ်းကြည့် ဒီစမ်းကြည့်နဲ့ သိလာခဲ့ပါတယ်။ ကိုယ့်ရဲ့ workflow နဲ့ ဘယ်လိုမှ အဆင်မပြေတာသိလာတဲ့အတွက် တော်တော်လေးကြံရာမရဖြစ်ခဲ့တဲ့ နေ့တွေကိုလည်း မှတ်မိနေပါသေးတယ်။ ဘယ်ကနေစလိုက်ရမလဲဆိုတာကို သေချာမသိခဲ့တဲ့ အစမကောင်းခဲ့ခြင်းလိုပဲဆိုရမှာပါ။ အဲ့ဒီနောက် ဟိုရှာဒီရှာ နဲ့ configuration management လို orchestration tool set တွေကို အကြောင်းကို စတင်တွေ့ရှိခဲ့ပါတော့တယ်။ အဲ့ဒီမှာလည်း ဘယ် tool set ကကိုယ်နဲ့ အဆင်ပြေနိုင်သလဲဆိုတာကို မစမ်းကြည့်ပဲနဲ့ မသိနိုင်တဲ့အတွက် တစ်ခုခုတော့ စပြီးတော့ စမ်းသပ်ကြည့်ဖို့ ဖြစ်လာပြန်ပါတယ်။ ပထမဆုံးတစ်ခုတွေ့ရှိချက်ကတော့ TCL Expect ပဲဖြစ်ပါတယ်။ network device တွေမှာ script တွေအသုံးပြုပြီးတော့ automate လုပ်ဖို့အတွက် ရှိနေခဲ့တဲ့ scripting language တစ်ခုပါ။ စပြီးတော့ implement လုပ်ဖို့ရာလေ့လာ ကြည့်အခါမှာတော့ တော်တော်လေး bulky ဖြစ်တာကိုတွေ့ရပါတယ်။ နောက်ပြီးတော့ language style မှာလည်း နည်းနည်းလေး out-of-date ဖြစ်သလိုခံစားရပါတယ်။ လက်ရှိအချိန်ထိ network engineer တော်တော်များများရဲ့ လက်စွဲ scripting language တစ်ခုအဖြစ်ရှိနေတုန်းပါ။ စာရေးသူအတွက်တော့ အနည်းငယ်လေ့လာကြည့်ပြီးတာနဲ့ ဒီတစ်ခုငါ့အတွက်မဟုတ်ဘူးဆိုတဲ့ စိတ်ခံစားချက်ဖြစ်လာလို့ နောက်တစ်ခုကို ဆက်သွားဖို့ဖြစ်လာခဲ့ပါတယ်။ အဲ့ဒီမှာပဲ… Ansible ရဲ့ lightweight ပုံစံနဲ့ agentless ဆိုတဲ့ feature နှစ်ခုတည်းနဲ့ပဲ စာရေးသူစတင် စိတ်ဝင်စားခဲ့ရပါတယ်။ ကံကောင်းချင်တော့… youtube မှာ network engineer တစ်ယောက်က Ansible ကိုအသုံးပြုပြီးတော့ သူ့ရဲ့ Cisco networking device တွေကိုဘယ်လို manageလုပ်သလဲဆိုတာကို တွေ့ရလို့၊ စာရေးသူဘဝင်ကျလို့ လိုက်လုပ်ကြည့်ရာကနေပြီးတော့ production environment မှာ Cisco ရဲ့ read-only show commands တွေနဲ့ စတင်စမ်းသပ် ဖြစ်ပါတော့တယ်။ တစ်ပတ်လောက် စမ်းသပ်ပြီးတဲ့အခါမှာတော့ Ansible ရဲ့ အစွမ်းထက်ပုံကို ချက်ချင်းသိလာခဲ့ပါတယ်။ စနစ်တကျသုံးနိုင်ရင် ထိထက်အကျိုးရှိဖို့လည်း မြင်တာကြောင့် အသေးစိတ် အချိန်ပေးပြီးတော့ စမ်းသပ်ဖို့ကို ဆုံးဖြတ်ခဲ့ပါတော့တယ်။

![](https://i2.wp.com/www.itmatic101.com/wp-content/uploads/2020/05/Exploring-Expect-1.jpg?fit=525%2C689&ssl=1)

တစ်ပတ်ကျော် နှစ်ပတ်ကြာကြာလောက်မှာတော့ အခြားသော မသိသေးတဲ့ engineer ကိို ကြွားဖို့လောက်တော့ အဆင်သင့်ဖြစ်နေပါပြီ။ လိုအပ်တဲ့ inventory ကိုလည်း ကိုယ့်စိတ်ကြိုက်ပြင်ဆင်ပြီးနောက် Cisco platform နဲ့ အလုပ်စတင်လုပ်ဖို့ ကြိုးစားကြည့်ပါတော့တယ်။ Ansible ad-hoc command လေးတွေသုံးကြည့်ပါတယ်။ ထိုမှတဆင့် Ansible Playbook မှာ ထပ်ကာထပ်ကာ လုပ်ရတဲ့ task တွေကို stage လုပ်ပြီးတော့ အသုံးပြုကြည့်ပါတယ်။ စစချင်းမှာစိတ်ချရအောင်လို့ GNS3 မှာ lab environment တစ်ခုတည်ဆောက်ပြီးတော့မှ Network Automation ဆိုတဲ့ docker container node ကို အသုံးပြုပြီးတော့ အရင်ဆုံး စမ်းဖြစ်ပါတယ်။ ကိုယ့်ဟာကို လုံးဝစိတ်ချရပြီဆိုမှဖြင့် production မှာ read-only ပဲဖြစ်တဲ့ show commands တွေနဲ့ ထည့်ပြီးတော့ သုံးကြည့်ပါတယ်။ တော်တော်လေးကို စိတ်တိုင်းကျစရာ ဖြစ်လာခဲ့ပါတယ်။ အဲ့ဒီကနေမှတဆင့် ကိုယ် manage လုပ်တဲ့ Linux box တွေကိုပါ patch လုပ်တဲ့အခါအဆင်ပြေအောင်လို့ Ansible ထဲမှာထည့်သုံးကြည့်ပါတယ်။ အဆင်ပြေပါတယ်။ သို့သော် bash မှာလိုတော့ ရိုးရှင်းတဲ့ ပုံစံမျိုးမဟုတ်ပဲနဲ့ YAML မှာထည့်ပြီးတော့ သုံးတဲ့ ပုံစံနဲ့မို့ အနည်းငယ်တော့ကွာခြားပြန်ပါတယ်။ ထိုမှာတဆင့် HPE networking platform နဲ့ Huawei ရဲ့ Routing နဲ့ Switching မှာအသုံးပြုဖို့အတွက်တော့ အနည်းငယ် အခက်ကြုံရပြန်ပါတယ်။ Vendor ကဘက်က ပြည့်ပြည့်ဝဝ support မလုပ်သလို အခြားသော လုံလောက်တဲ့ documentation နဲ့ tutorial တွေ စုံစုံလင်လင် မရှိတာကြောင့် ဆက်သွားဖို့ အဆင်မပြေပြန်ပါဘူး။ သို့သော် အခြား engineer တွေ တစ်လုံးဝင် တစ်လုံးထွက်နဲ့ လိုက်ပြီးတော့ စစ်ဆေးရတဲ့အချိန်မှာ ကိုယ်က Ansible Playbook နဲ့ command တစ်ခုတည်းရိုက် ထည့်လိုက်ရုံနဲ့ parallel ssh session တွေနဲ့အတူ အလုပ်ကို ပိုပြီးတော့ တွင်တွင်ကျယ်ကျယ်လုပ်လာနိုင်ပါတယ်။ ကိုယ်လိုချင်တဲ့ workflow ပုံစံတစ်ခုဖြစ်ဖို့တော့ ကိုယ့်စိတ်ကူး စိတ်သန်း ကောင်းကောင်းတစ်ခုရှိဖို့တော့ လိုမယ်ဆိုတာသိလာပါတယ်။ သူ့ကို ထဲထဲဝင်ဝင် အသုံးပြုနိုင်ဖို့ရာကတော့ Guitar တစ်လုံးကို ကိုင်ပြီးတော့ သီချင်းတစ်ပုဒ်ကို ကောက်ပြီးတော့ တီးသလို မျိုးပဲ Guitar ရဲ့ မှာရှိတဲ့ Chord တွေကို ပိုင်နိုင်ဖို့တော့ အရင်ဆုံးလိုအပ်ပါလိမ့်မယ်။ Guitar မှာရှိတဲ့ Chord တွေကို ပိုင်နိုင်သွားပြီဆိုတော့မှ ကိုယ်ကြိုက်တဲ့ colour နဲ့ flavour ကို ကိုယ်အကြည်ဓာတ်ရှိရင်ရှိသလောက် ဆက်ပြီးတော့ ဖန်တီးသွားနိုင်တဲ့ အနုပညာ ပုံစံမျိုးလိုပဲလို့ စာရေးသူထင်မိပါတယ်။

![Ansible for Network Automation](https://i0.wp.com/www.itmatic101.com/wp-content/uploads/2020/05/network-ansible.png?fit=525%2C295&ssl=1)

အောက်မှာကတော့ user EXEC mode မှာအသုံးပြုနိုင်တဲ့ show arp ကို Cisco ရဲ့ router နဲ့ switch တွေပေါ်မှာ တပြိုင်နက်တည်း parallel run လို့ရအောင် လုပ်နိုင်တဲ့ Ansible Playbook codelet လေးတစ်ခုကိုဖော်ပြပေးထားပါတယ်။ ဒီတစ်ခုမှာ raw ဆိုတဲ့ module ကိုပဲအသုံးပြုပြီးတော့ show arp ဆိုတဲ့ command ကိုထည့်ပြီးတော့ ပေးပို့ပါတယ်။ Play တစ်ခုဖြစ်တဲ့ Get ARP information အောက်မှာ tasks နှစ်ခုကို လုပ်ဆောင်ပါတယ်။ ပထမတစ်ခုက show arp ဖြစ်ပြီးတော့၊ နောက်တစ်ခုကတော့ debug ဆိုတဲ့ task နဲ့ standard out ကို screen ပေါ်မှာ print လုပ်ခိုင်းတာပဲဖြစ်ပါတယ်။

```text
---
- name: Get ARP information
  hosts: all
  gather_facts: false

  tasks:
    - name: show arp
      raw: "show arp"
      register: print_output

    - debug: var=print_output.stdout_lines
```

ပြီးတော့ နောက်တစ်ခုကတော့ Privileged EXEC mode မှာ တဆင့်တက်ပြီးတော့ run နိုင်တဲ့ codelet နောက်တစ်ခုပါ။ သူလည်း play တစ်ခုနဲ့ task နှစ်ခုပါ။ ဒီတစ်ခုမှာတော့ ios\_command ဆိုတဲ့ module ကို အသုံးပြုထားပြီးတော့ authorize: yes ဆိုတာကတော့ Cisco IOS ရဲ့ enable command နဲ့ တူညီတဲ့ YAML ရဲ့ key value pair ပုံစံဖြစ်ပါတယ်။ auth\_pass: \[password\] ဆိုတာကတော့ enable password ကို plaintext ထဲမှာဒီအတိုင်းထည့်တဲ့ပုံစံပါ။ \[password\] ဆိုတဲ့နေရာမှာ ကိုယ့်ရဲ့ enable password ကို ထည့်သွင်းရမှာဖြစ်ပါတယ်။ ဒီလိုမျိုး plaintext နဲ့ password ကို စမ်းသပ်တဲ့အခါမျိုးမှာပဲ သုံးသင့်ပြီးတော့ production မှာတော့ vault ကို သုံးပြီးတော့ credentials တွေကို transport လုပ်သင့်ပါတယ်။

```text
---
- name: Show IP Interface brief 
  hosts: cs
  gather_facts: false
  connection: local

  tasks:
    - name: Getting ip interface brief
      ios_command:
        authorize: yes
        auth_pass: [password]
        commands:
          - show ip int bri
      register: print_output

    - debug: var=print_output.stdout_lines
```

အထက်က YAML file တွေကို run ဖို့အတွက်တော့ အောက်က Ansible Playbook ရဲ့ command ကို run ရပါ လိမ့်မယ်။

```text
$ ansible-playbook -u tylalin -k arp-playbook.yml
$ ansible-playbook -u tylalin -k sh-ip-int-bri.yml
```

Ansible ရဲ့ ad-hoc command အသုံးပြုပုံနဲ့ playbook command အသေးစိိတ်ကိုတော့ နောက်မှပဲ Ansible နဲ့ပတ်သတ်တဲ့ post တွေရေးတဲ့ အခါမှပဲ ထည့်သွင်းရှင်းသွားပါ့မယ်။ ဒီ post မှာတော့ high-level ပဲ ခပ်သွက်သွက် သွားလိုက်ပါတော့မယ်။ Ansible ရဲ့ use case နဲ့ network platform တွေမှာအသုံးဝင်ပုံကို အသားပေးရှင်းလိုခြင်းသာဖြစ်ပါတယ်။

ဒီတော့ဖြင့်…Ansible ဟာ Cisco network platform နဲ့ Linux server တွေကို manage လုပ်ဖို့၊ orchestrate လုပ်ဖို့ အဆင်ပြေသော်လည်း၊ အခြားသော platform တွေဖြစ်တဲ့ Huawei နဲ့ HPE တွေမှာ အဆင်မပြေတာတွေတော်တော်လေးရှိနေသေးတဲ့အတွက် Python ကိုလေ့လာပြီးတော့ multi-vendor platform တွေကို manage လုပ်နိုင်အောင်၊ automate လုပ်နိုင်အောင် ထပ်မံအားထုတ်ရပြန်ပါတယ်။ Ansible ရဲ့ backend မှာလည်း module တွေကိုလည်း Python နဲ့ပဲရေးထားတာဖြစ်တဲ့အတွက် ထပ်တိုးလေ့လာသင့်တဲ့ learning pathway တစ်ခုလို့ စာရေးသူမြင်မိပါတယ်။ Python နဲ့ ပတ်သတ်တဲ့ network automation အကြောင်းကိုတော့ နောက်တပိုင်းမှပဲ ဆက်လိုပါတယ်။ ဒီ တပိုင်းကိုတော့ Ansible နဲ့ ဘယ်လိုမျိုးစတင်တွေ့ရှိခဲ့သလဲဆိုတာနဲ့ပဲ ရပ်လိုက်ချင်ပါတော့တယ်။  

