# အနားမသပ်နိုင် သေးတဲ့ Infrastructure as Code \(IaC\) - အပိုင်း\(၃\)

အရှေ့ post မှာတော့ Vagrant ကိုအသုံးပြုပြီး dev/test environment တစ်ခုကို ဘယ်လိုမျိုး IaC နည်းနဲ့ တည်ဆောက်ရသလဲဆိုတာကို လက်တွေ့အသုံးပြုနည်း ၂မျိုး ၃မျိုးလောက်ကို ရှင်းပြခဲ့ပါတယ်။ Instant deployment နဲ့ Scale-up/down တို့အပြင် teardown လုပ်ရတာ လွယ်ပုံလွယ်နည်းကိုလည်း ရှင်းခဲ့တယ်။ ဒီလိုဆိုတော့ မေးစရာရှိတာက Vagrant ဟာ Virtualbox နဲ့ အချို့ သော provider တွေနဲ့သာ အလုပ်လုပ်ပြီးတော့ cloud platform တွေမှာ limit အရမ်းကို ဖြစ်လွန်းပါတယ်။ စာရေးသူ အနေနဲ့တော့ Vagrant ကိုအသေးစား စမ်းသပ်မူမျိုးအတွက်သာ ကိုယ့် local machine မှာ Virtualbox နဲ့ တွဲပြီး သုံးသင့်ပါတယ်။ ဒီ့ထက်ကြီးတဲ့ infrastructure ကိုတည်ဆောက်ဖို့အတွက်တော့ Terraform ကိုသာ သုံးသင့်ပါတယ်။ ဒီတစ်ခုမှာတော့ Terraform အကြောင်းကို ဆက်ပြီးတော့သွားလိုက်ရအောင်ဗျာ။

### Terraform မိတ်ဆက်

Terraform ကိုလည်း HashiCorp ကနေပဲ opensource အနေနဲ့ ဖန်တီးထားတာဖြစ်ပြီးတော့ Vagrant နဲ့ မတူတာတစ်ခုက HashiCorp Configuration Language \(HCL\) ဆိုတဲ့ declarative configuration language ပုံစံကို အသုံးပြုထားပါတယ်။ ဒါကြောင့် Terraform မှာ desired state တွေကိုပြောလိုက်ရုံနဲ့ အနောက်မှာလုပ်စရာရှိတာတွေ အကုန်လုံးကို သူဟာသူ API တွေနဲ့တွဲကာ လုပ်ဆောင်နိုင်စွမ်းရှိပါတယ်။ သူ့မှာလည်း provider ဆိုတဲ့ concept ကို Vagrant မှာလိုပဲ အသုံးပြုထားတာဖြစ်ပြီးတော့ virtualisation နဲ့ cloud platform တွေတော်တော်များများမှာ အလုပ်လုပ်ပါတယ်။ အချို့သော support လုပ်တဲ့ platform တွေကို ပြောရမယ်ဆိုရင်တော့ AWS, Azure, IBM cloud, GCP, DigitalOcean, Oracle Cloud Infrastructure, VMware vSphere နဲ့ OpenStack တို့လိုမျိုး platform တွေမှာ အလုပ်လုပ်ပါတယ်။ စာရေးသူ သိသလောက်တော့ Terraform ရဲ့ အနောက်မှာအသုံးပြုတဲ့ core language က Golang လို့လည်း သိရပါတယ်။ Terraform ရဲ့ GitHub repo ကိုတော့ ဒီမှာ [https://github.com/hashicorp/terraform](https://github.com/hashicorp/terraform) သွားပြီးတော့ ကြည့်ရှုလေ့လာလို့ ရနိုင်ပါတယ်။ Golang ဟာ system နဲ့ infrastructure တွေနဲ့ တိုက်ရိုက် အလုပ်လုပ်တဲ့ အခါမှာ မြန်အောင်ပေါ့အောင် လုပ်ထားတဲ့ language တစ်ခုဖြစ်တဲ့ အတွက် အခုအချိန်မှာ အငယ်တော့ တီးမိခေါက်မိလောက် အောင်သိထားသင့်တဲ့ အရာတစ်ခုပါ။ ဒါကြောင့်လည်း စာရေးသူလေ့လာချင်နေတဲ့ language ထဲမှာ Golang ဟာလည်း တစ်ခုသော programming language တစ်ခုပါ။ Python တို့ Ruby တို့မှာလိုပဲ code တွေကို ဖတ်ရလွယ်ပြီးတော့ စွမ်းဆောင်ရည်ပိုင်းမှာလည်း အခြေခံကစလို့ အဆင့်မြင့်မြင့် လုပ်ဆောင်ချက်တွေကို လုပ်နိုင်တာကြောင့် တော်တော်လေးကို မျက်စိကျမိနေပါတယ်။ Docker လိုမျိုး ဆန်းပြားတဲ့ containerisation platform တစ်ခုလုံးကို Golang တစ်ခုတည်းနဲ့ ရေးလို့ ရနိုင်ပါတယ်။ ဒီလောက်ဆိုရင် Golang နဲ့ ဆိုဘယ်လောက်ထိခရီးပေါက်မလဲဆိုတာ သိနိုင်ပါပြီ။ 

### Terraform ကို install လုပ်ပုံ

Terraform ကို Ubuntu/Debian ကိုအခြေခံထားတဲ့ distro တွေမှာအသုံးပြုချင်ရင်တော့ အောက်ကအတိုင်း command တွေကို run ရမှာဖြစ်ပါတယ်။ ပထမဆုံး HashiCorp ရဲ့ GPG ကို ကိုယ့်ရဲ့ apt package manager အတွက် အခုလိုအရင်ဆုံး ထည့်သွင်းရပါ့မယ်။

```text
$ curl -fsSL https://apt.releases.hashicorp.com/gpg | sudo apt-key add -
```

ပြီးနောက်... သူ့ရဲ့ repo ကို package manager ရဲ့ repository list ထဲမှာသွားပြီးတော့ အောက်ကအတိုင်းပေါင်းထည့်ပါ။ 

```text
$ sudo apt-add-repository "deb [arch=amd64] https://apt.releases.hashicorp.com $(lsb_release -cs) main"
```

ပြီးသွားရင်တော့... အောက်ကအတိုင်း apt package manager ကို update လုပ်ပြီးတော့၊ Terraform ကို install လုပ်ရုံပါပဲ။ 

```text
$ sudo apt-get update && sudo apt-get install terraform
```

ကိုယ်က Apple ကိုအသုံးပြုတယ်ဆိုရင်တော့ Homebrew ကိုအသုံးပြုပြီးတော့ အောက်ကအတိုင်း install လုပ်လို့ရပါတယ်။ 

```text
$ brew tap hashicorp/tap
$ brew install hashicorp/tap/terraform
$ brew upgrade hashicorp/tap/terraform
```

ဒါမှမဟုတ်ဘူး... Windows မှာအသုံးပြုချင်ရင်တော့ Chocolatety ကိုသုံးပြီးတော့ အခုလိုမျိုး install လုပ်လို့ရနိုင်ပါတယ်။

```text
$ choco install terraform
```

ဒီတော့... Terraform ကို ကိုယ်အသုံးပြုတဲ့ OS ပေါ်မှာမူတည်ပြီးတော့ ပုံစံအမျိုးမျိုးနဲ့ install လုပ်နိုင်တာကိုတွေ့ရမှာဖြစ်ပါတယ်။ 

### Terraform ကိုလက်တွေ့အသုံးချနည်း 

