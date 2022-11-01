# Docker မိတ်ဆက် အပိုင်း(၃)

Docker အကြောင်းတွေကို မိတ်ဆက်လိုက်တာ အခုဆို အပိုင်း ၂ ပိုင်းတောင်ရှိသွားပါပြီ။ ပထမတပိုင်းမှာတော့ Docker ရဲ့ နောက်ခံ အကြောင်းလေးနဲ့ စလိုက် ပြီးတော့၊ ဒုတိယပိုင်းမှာတော့ Docker ရဲ့ တည်ဆောက်ထားပုံနဲ့ သူ့ရဲ့ Docker image အကြောင်းလေးတွေကို အနည်းငယ်တင်ပြပြီးသွားပါပြီ။ မိတ်ဆက်ပေးရုံသာဖြစ်တဲ့ အတွက် ပြီးပြည့်စုံတယ်လို့တော့ မထင်ပါဘူး။ အလုံးစုံကိုရှင်းမယ်ဆိုရင်တော့ ပြောလို့ ပြီးမယ်လို့တောင် မထင်ပါဘူး။ မည်သို့ပင် ဖြစ်စေ Docker ရဲ့ အရသာကို အမြီး သဘောမျိုး သိလိုက်ရမယ်လို့တော့ ထင်ပါတယ်။ ဒီအပိုင်းမှာတော့ Docker ကို အခြားသော virtualization နည်းပညာ တချို့နဲ့ ရောပြီးတော့ မှားတတ်တဲ့ သဘောရှိလို့၊ Docker ကို လက်တွေ့မှာ တကယ်မသုံးခင် ရှင်းစရာရှိတာကို အရင်ဆုံး ရှင်းလိုက်ရအောင်။

<figure><img src="https://i.imgur.com/GlFy82R.png" alt=""><figcaption><p>Docker Architecture</p></figcaption></figure>

### Docker နဲ့ ဆင်တူတဲ့ Vagrant

Docker ကို တချို့က virtualization နဲ့ မှားတတ်သလို၊ WSL (Windows Subsystem for Linux ) ဆိုတဲ့ subsystem မျိုးနဲ့ လည်းမှားတတ်ပါတယ်။ Virtualization နဲ့ မတူဘူးဆိုတာကိုတော့ အရှေ့အပိုင်းတွေမှာ သရှင်းနိုင်သလောတော့ ရှင်းပြထားပါတယ်။ Virtualization နည်းပညာကို အနောက်ဘက်မှာ သုံးပြီးတော့ Docker နဲ့ခပ်ဆင်ဆင် နောက် နည်းပညာတစ်ခုရှိပါတယ်။ Vagrant လို့ခေါ်ပါတယ်။ DevOp ဘက်မှာတော့ တချို့ Developers တွေဟာ Vagrant ကိုသုံးပြီးတော့ App တွေကို develop လုပ်ကြ၊ test လုပ်ကြပါတယ်။ များသောအားဖြင့် Vagrant ကို test လုပ်ဖို့ staging အဆင့်လောက်ထိသာ အသုံးများပြီးတော့၊ Docker ကိုတော့ production environment ထိသုံးလို့ရအောင်လို့ လုပ်ထားကြပါတယ်။ Vagrant ဟာလည်း Docker လိုမျိုး CLI မှာ command တွေရိုက်ထည့်ပြီးတော့ ကိုယ်လိုချင်တဲ့ VM template Box တွေကို Vagrant Cloud ကနေပြီးတော့ ဆွဲယူပြီးတော့ အသုံးပြုလို့ရပါတယ်။ Vagrant မှာလည်း Docker မှာသုံးတဲ့ Dockerfile လိုမျိုး Vagrantfile ဆိုတာလည်းရှိပါတယ်။ Vagrant စထွက်လာတဲ့ အချိန်နဲ့ Docker စထွက်လာတဲ့ အချိန်ဟာ မရှေးမနှောင်းလို့ဆိုရမှာပါ။ Vagrant ကတော့ ထွက်တာ နည်းနည်းလေး စောပါလိမ့်မယ်။ Design concept နဲ့ purpose အရကြည့်မယ်ဆိုရင် Vagrant နဲ့ Docker ဟာ တော်တော်ဆင်တူပါတယ်။ Vagrant ရဲ့ ရည်ရွယ်ချက်ကလည်း Docker နည်းတူ DevOps သမားတွေအတွက် အဆင်ပြေအောင်လို့ လုပ်ထားတာ ဖြစ်ပါတယ်။ Vagrant အကြောင်းကို အသေးစိတ် နောက်မှ သပ်သပ်ထပ်ရေးသွားပါ့မယ်။ အခုဒီ post မှာတော့ Docker နဲ့ ဘာလို့ အလွယ်တကူ အမှတ်မှားနိုင်လည်းဆိုတာကို အလေးပေးပြီးတော့ ဆွေးနွေးချင်ပါတယ်။

<figure><img src="https://i.imgur.com/Tj6fwUx.png" alt=""><figcaption><p>Vagrant + Virtualbox</p></figcaption></figure>

<figure><img src="https://i.imgur.com/SWGkjwK.png" alt=""><figcaption><p>Vagrantfile</p></figcaption></figure>

ပုံမှန်အားဖြင့်တော့ Vagrant ဟာ Virtualbox ကိုသူ့ရဲ့ provider အနေနဲ့ သုံးပါတယ်။ Virtualbox က open-source ဖြစ်တဲ့အတွက် Vagrant တွဲပြီးတော့ သုံးကြတာပါ။ Vagrant ရဲ့ မူရင်းပိုင်ရှင် ကုမ္ပဏီဖြစ်တဲ့ HashiCorp ကတော့ VMware ကို provider အနေနဲ့ တွဲသုံးဖို့ ကို recommend လုပ်ထားပါတယ်။ သို့သော် VMware ဟာ proprietary ဖြစ်တဲ့ အတွက် ကုန်ကျစရိုက်ရှိသော်လည်း၊ stable လည်းပိုဖြစ်ပါတယ်။ Free ရတဲ့ VMware Player ကြပြန်တော့လည်း feature အပြည့်အစုံမပါလို့ သုံးတာအဆင်မပြေပါဘူး။ VMware Workstation လောက်သုံးမှ အဆင်ပြေတဲ့အတွက် နောက်ဆုံးတော့ open-source ဖြစ်တဲ့ Virtualbox ကိုသာပြေးပြီးတော့ ကပ်ရပြန်တာပါပဲ။ Vagrant ဟာ အဲ့လိုမျိုး VM တွေကို run ဖို့အတွက် Virtualization platform တစ်ခုလိုတဲ့အတွက်၊ သဘာဝအရတော့ Docker နဲ့ လုံးဝကွာခြားသွားပါတယ်။ Ruby နဲ့ Vagrant ကိုရေးထားတာဖြစ်ပြီးတော့၊ VM တစ်လုံးကို provision လုပ်တဲ့အခါသုံးတဲ့ Vagrantfile ရဲ့ syntax ဟာ Ruby language ရဲ့ syntax ပါပဲ။ Docker မှာတော့ ပိုပြီးရိုးရှင်းတဲ့ syntax ကို နောက်ပိုင်းမှာ တွေ့ရမှာဖြစ်ပါတယ်။ တချို့ developers တွေဟာ Vagrant ကို သူတို့ software developing environment နဲ့ test environment မှာ တွင်တွင်ကျယ်ကျယ် သုံးနေဆဲပါ။ စာရေးသူ အနေနဲ့တော့ Docker ကို ပိုပြီးတော့ စိတ်တိုင်းကျပါတယ်။ သို့သော် နှစ်ခုလုံးမှာ သူတို့ရဲ့ အားနည်းချက် အားသာချက်ကိုယ်စီ ရှိကြပါတယ်။ ဒီအပိုင်းမှာ Vagrant ကို နည်းနည်းထည့်ရှင်းတာဟာ Docker နဲ့ ဆင်တူလွန်းတာတကြောင်း၊ DevOps မှာလည်း လက်ရှိသုံးနေကြတာရှိတဲ့အတွက် အမှတ်မမှားရအောင်လို့ ဖြစ်ပါတယ်။ အခုတော့ Docker ကို ကိုယ့်စက်ပေါ်မှာ ဘယ်လိုတင် ပြီးသုံးလို့ ရသလဲဆိုတာရယ်၊ အခြေခံသုံးလို့ ရတဲ့ Docker command တချို့နဲ့ Docker Compose tool နဲ့ ကိုယ့်စိတ်ကြိုက် container တစ်ခုဘယ်လို တည်ဆောက်လို့ရသလဲဆိုတာတွေကို အရင်သွားလိုက်ရအောင်။

### Docker ကို ဘယ်လို install လုပ်သလဲ

အခုတလော စာရေးသူကိုယ်တိုင် Ubuntu LTS 16.04 နဲ့ CentOS7 နှစ်ခုလုံးကို တော်တော်လေး စိတ်တိုင်းကျနေတဲ့ အတွက် Docker အကြောင်းရေးဖို့ စဉ်းစားတော့၊ Ubuntu နဲ့ CentOS ပေါ်မှာ Docker ကို install လုပ်ပုံ နဲ့ ကိုယ်စက်ပေါ်မှာ Docker အတွက်လိုတဲ့ initial configuration လေးတွေကို အခြေခံပြီးတော့ ရေးသွားမှာ ဖြစ်ပါတယ်။ ဘယ်လိုပဲဖြစ်ဖြစ် Ubuntu မှာ install လုပ်လို့ အဆင်ပြေရင် Debian ကဆင်းလာတဲ့ distro တော်တော်များများ အဆင်ပြေပါတယ်။ လိုအပ်တဲ့အပိုင်းတွေကို Install လုပ်၊ initial configuration တွေလုပ်ပြီးသွားရင်တော့ ကျန်တဲ့အပိုင်းတွေမှာတော့ Docker command တွေကို သုံးတဲ့အတွက် distro agnostic ဖြစ်ပါတယ်။

<figure><img src="https://i.imgur.com/gNppaVN.png" alt=""><figcaption><p>Ubuntu + Docker</p></figcaption></figure>

ပထမဆုံး အနေနဲ့ Docker ကို install ဘယ်လိုလုပ်သလဲဆိုတာနဲ့ စလိုက်ရအောင်။ Docker ကို install လုပ်တဲ့ နည်းလမ်း အမျိုးမျိုးရှိပါတယ်။ အခုဒီမှာ သုံးတဲ့ command ကတော့ Docker နောက်ဆုံးထွက်ထားတဲ့ version ကို dowload လုပ်ပြီးတော့၊ လိုအပ်တဲ့ dependencies တွေကိုပါလိုအပ် သလို automatic ဆွဲပြီးတော့ install လုပ်တဲ့ နည်းပါ။

**Ubuntu**\
ကိုယ့်စက်ပေါ်မှာ curl နဲ့ လိုအပ်တဲ့ tool လေးတွေကို မရှိသေးရင် အရင် install လုပ်လိုက်ပါ။ ပြီးတော့မှ Docker ကို အောက်မှာပြထားတဲ့ instruction အတိုင်းဆက်ပြီးတော့ install လုပ်လိုက်ပါ။

```
$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

Docker ရဲ့ official GPG key ကိုအောက်မှာပြထားတဲ့ အတိုင်းပေါင်းထည့်လိုက်ပါ။

```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

GPG key ကို verify လုပ်ချင်တယ်ဆိုရင်တော့ အောက်ကအတိုင်းလုပ်နိုင်ပါတယ်။

```
$ sudo apt-key fingerprint 0EBFCD88

pub   rsa4096 2017-02-22 [SCEA]
      9DC8 5822 9FC7 DD38 854A  E2D8 8D81 803C 0EBF CD88
uid           [ unknown] Docker Release (CE deb) <docker@docker.com>
sub   rsa4096 2017-02-22 [S]
```

အခုဆိုရင် Docker ကိုစတင် install လုပ်နိုင်ပါပြီ။

```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
   
 $ sudo apt-get update
 $ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

Docker အလုပ်လုပ်သလား မလုပ်ဘူးလာကို စစ်ချင်ရင် hello-world ဆိုတဲ့ container နဲ့ စစ်လို့ရပါတယ်။

```
$ sudo docker run hellow-world

Unable to find image ‘hello-world:latest’ locally
latest: Pulling from library/hello-world
ca4f61b1923c: Pull complete
Digest: sha256:ca0eeb6fb05351dfc8759c20733c91def84cb8007aa89a5bf606bc8b315b9fc7
Status: Downloaded newer image for hello-world:latest
Hello from Docker!

This message shows that your installation appears to be working correctly.
```

အထက်မှာလိုမျိုး ပြရင်တော့ Docker ကို install လုပ်တာ အောင်မြင်ပါပြီ။

စမ်းသပ်လို့ အဆင်ပြေတယ်ဆိုရင်တော့ နောက်တဆင့်မှာ လိုအပ်တဲ့ initial configuration အနည်းငယ်လုပ်ပြီရင်တော့ စပြီးအသုံးပြုဖို့ ready ဖြစ်ပါပြီ။ ဒီအဆင့်မှာလည်း တခါ Ubuntu command တွေတူပါတယ်။

အရင်ဆုံး Docker Engine ရဲ့ status ကို ကြည့်လိုက်ရအောင်။

```
$ sudo systemctl status docker
```

အထက်က command ရိုက်ထည့်လိုက်ပြီးတော့ အောက်ကလိုမျိုးပြရင်တော့ Docker engine က active ဖြစ်နေပါပြီ။

```
● docker.service – Docker Application Container Engine
Loaded: loaded (/lib/systemd/system/docker.service; enabled; vendor preset: enabled)
Active: active (running) since Sun 2018-02-25 10:29:52 AEDT; 3min 53s ago
Docs: 
https://docs.docker.com

Main PID: 4813 (dockerd)
```

Docker ရဲ့ command တွေကိုရိုက်ထည့်တိုင်းမှာ super user အနေနဲ့ရိုက်ထည့်ရတဲ့ အတွက် လက်ရှိကိုယ်သုံးတဲ့ user account ကို docker ဆိုတဲ့ users group ထဲကို အောက်က command ရိုက်ထည့်ရပါလိမ့်မယ်။ ပြီးသွားရင် ကိုယ် user account က docker ဆိုတဲ့ users group ထဲမှာ ပါဝင်သွားပြီလားဆိုတာကိုလည်း တခါတည်း စစ်ကြည့်လို့ ရပါတယ်။ နောက်ပိုင်း တခြား Docker command တွေသုံးတဲ့အခါမှာ ဒီတစ်ခု မလုပ်ထားဘူးဆိုရင် troubleshoot လုပ်ရတဲ့ step အပိုတွေလုပ်ရနိုင်ပါတယ်။ ဒါကြောင့် ဒီအဆင့်က အရေးကြီးပါတယ်။

```
$ sudo usermod -aG docker ${USER}
$ su – ${USER}
$ id -nG
```

အခုဆိုရင်တော့ Docker ကို install လုပ်တာပြီးသွားပါ။ Docker ကို စပြီးတော့ သုံးလို့ရပါပြီ။

ပထမဆုံး docker မှာ သုံးလို့ရတဲ့ command တွေကို ကြည့်လိုက်ရအောင်။ docker ဆိုတာရိုက်ထည့်လိုက်တာနဲ့ docker မှာ သုံးလို့ရတဲ့ command တွေကို ပြပါလိမ့်မယ်။

Docker command တစ်ခုချင်းစီကို အသေးစိတ် မသွားတော့ပါဘူး။ စာရေးသူရဲ့ မူရင်း ရည်ရွယ်ချက်က Docker မိတ်ဆက်ပေးပြီးတော့ စိတ်ဝင်စားစရာ ဖြစ်အောင်လုပ်ပေးဖို့ပါပဲ။ ကိုယ်က စိတ်ဝင်စားတယ် အသေးစိတ် လေ့လာချင်ရင်တော့ Docker ရဲ့ documentation ကို ဒီ [link ](https://docs.docker.com/get-started/)ကနေသွားကြည့်ပြီးတော့ လေ့လာလို့ရပါတယ်။

### Docker ကိုဘယ်လိုမျိုးလက်တွေ့ အသုံးချမလဲ

Docker ရဲ့ command တွေကို အသေးစိတ် မရှင်းပေမယ့်လည်း၊ လက်တွေ့မှာ ဘယ်လိုမျိုး အသုံးချလို့ရသလဲဆိုတာကို နည်းနည်းလေး ဆွေးနွေးချင်ပါတယ်။ လက်တွေ့ အသုံးချတဲ့ပုံကို သိတဲ့အခါမှ နည်းပညာ တစ်ခုက ပိုပြီးတော့ စိတ်ဝင်စားဖို့ကောင်းတယ်လို့ စာရေးသူမြင်ပါတယ်။ အသေးစိတ်သွားတာမဟုတ်ပေမယ့် ဥပမာ နှစ်ခုလောက်နဲ့ လက်တွေ့အသုံးချပုံကို ရှင်းသွားပါ့မယ်။

#### Docker Compose Tool နဲ့ customized container တစ်ခုတည်ဆောက်ခြင်း

ပထမဆုံး အနေနဲ့ WordPress ကို Docker နဲ့ ဘယ်လို compose လုပ်သလဲဆိုတာ ဆက်ရှင်းပါ့မယ်။ အရင်ဆုံး ဒီနည်းကိုသုံးမယ်ဆိုရင် docker compose tool ကို install လုပ်ရပါလိမ့်မယ်။ အောက်က command ကို သုံးပြီးတော့ github ပေါ်ကနေ download ဆွဲရပါလိမ့်မယ်။

```
$ sudo curl -L https://github.com/docker/compose/releases/download/1.19.0/docker-compose-uname -s–uname -m -o /usr/local/bin/docker-compose
```

Download လုပ်ပြီးသွားရင်တော့ docker-compose file ကို executable mode ရအောင်လို့ attribute ကို အောက်က command နဲ့ ပြောင်းပေးရပါလိမ့်မယ်။

```
$ sudo chmod +x /usr/local/bin/docker-composeim
```

<figure><img src="https://i.imgur.com/6yb31Qp.png" alt=""><figcaption><p>Docker Compose</p></figcaption></figure>

ဒီတစ်ခုမှာလည်း ကိုယ်သုံးတာ Ubuntu သို့မဟုတ် CentOS အနေနဲ့ သုံးတယ်လို့ ယူဆပါ။ ကိုယ့်ရဲ့ home directory မှာ wordpress ဆိုတဲ့ project directory တစ်ခု အရင်တည်ဆောက်လိုက်ပါ။ ပြီးတော့ အဲ့ဒီ directory အောက်မှာ docker-compose.yml ဆိုတဲ့ file တစ်ခုကို ဖန်တီးလိုက်ပါ။ ပြီးတော့ အဲ့ဒီ ကို ကိုယ်ကြိုက်တဲ့ text editor တစ်ခုကို သုံးပြီးတော့ အောက်က script ကို ကူးယူပြီးတော့ ထည့်လိုက်ပါ။

```
version: “3.3”
services:
     db:
          image: mysql:5.7
          volumes:
               – dbdata:/var/lib/mysql
          restart: always
          environment:
                   MYSQL_ROOT_PASSWORD: !@mR00t
                   MYSQL_DATABASE: wordpress
                   MYSQL_USER: wp-admin
                   MYSQL_PASSWORD: wordpress
     wordpress:
            depends_on:
                    – db
            image: wordpress:latest
            ports:
                – “8000:80”
            restart: always
            environment:
                   WORDPRESS_DB_HOST: db:3306
                   WORDPRESS_DB_USER: wordpress
                   WORDPRESS_DB_PASSWORD: wordpress
volumes:
        dbdata:
```

အပေါ်က script ကိုကြည့်လိုက်တာနဲ့ နားလည်ဖို့ လွယ်ပါတယ်။ Services နှစ်ကို လိုချင်လို့ services အောက်မှာ wordpress နဲ့ တွဲသုံးဖို့ db: ကိုတည်ဆောက်ဖို့ ရည်ရွယ်ပါတယ်။ ယူသုံးတဲ့ image ကို mysql:5.7 ဆိုပြီးတော့ သတ်မှတ်လိုက်ပါတယ်။ database ကို /var/lib/mysql အောက်မှာ သိမ်းဖို့ကို ပြောထားပါတယ်။ နောက်ပြီးတော့ restart policy ရဲ့ default ဖြစ်တဲ့ no မလုပ်ချင်လို့ restart: always လုပ်မယ်လို့လည်းပြောထားပါတယ်။ ဘာကို ဆိုလိုသလဲဆိုတော့ လိုအပ်လို့ပဲဖြစ်ဖြစ်၊ on-failure error ဖြစ်လို့ပဲဖြစ်ဖြစ် restart အမြဲလုပ်မယ်လို့ ဆိုလိုတာပါ။ ဒါမှမဟုတ်ရင် service က ဘာမှမလုပ်ပဲ frozen ဖြစ်သွားနိုင်လို့ပါ။ နောက်တပိုင်းကတော့ environment: ဆိုတဲ့ အပိုင်းပါ။ ဒီတစ်ခုကလည်း ရှင်းပါတယ်။ WordPress ရဲ့ အခြေခံ လိုအပ်သော environmental variables တွေဖြစ်တဲ့ MYSQL\_ROOT\_PASSWORD (MySQL db management အတွက်လိုအပ်တဲ့ root passwordပါ။)၊ MYSQL\_DATABASE (db ရဲ့ နာမည် ကိုသတ်မှတ်ပေးတာပါ။)၊ MYSQL\_USER (အဲ့ဒီ db အတွက်လိုအပ်တဲ့ username ပါ။)၊ MYSQL\_PASSWORD (ဒါကတော့ create လုပ်ထားတဲ့ user account အတွက် password ပါ။)။

Services အောက်က ဒုတိယတပိုင်းကတော့ wordpress: ဆိုတဲ့ တစ်ခုပါ။ ဒီမှာလည်း အပေါ်ကတစ်ခုနဲ့ အတူတူပါပဲ။ depend-on: ဆိုတာ services နှစ်ခုဖြစ်တဲ့ အတွက် အဲ့ဒီ နှစ်ခုကို တွဲသုံးတဲ့အခါမှာ လိုအပ်တဲ့ dependencies ကို စစ်လိုက်တာပါ။ အပေါ်က db ဆိုတဲ့ အပိုင်းကို ပြန်ပြီးတော့ reference လုပ်ပါတယ်။ နောက်တခါ နောက်ဆုံးထွက်ထားတဲ့ wordpress ဆိုတဲ့ container image ကို သုံးဖို့ကို ပြောထားပါတယ်။ ports: ဆိုတဲ့ဟာကတတော့ container ကနေပြီးတော့ host ကို communicate လုပ်တဲ့အခါမှာ ဘယ် port number နဲ့ expose လုပ်မလဲဆိုတာကို ပြောထားတာပါ။ 8000:80 ဆိုတာ container က http ရဲ့ port number ဖြစ်တဲ့ 80 ကို host ပေါ်မှာ port number 8000 နဲ့ expose လုပ်ထားတာပါ။ နောက်ပိုင်းမှာ wordpress ကို access လုပ်တဲ့အခါ အဲ့ဒီ port 8000 ကို ကိုယ့်စက်ရဲ့ IP address သို့မဟုတ် localhost ဆိုတဲ့ အနောက်မှာ ထည့်ပြီးတော့ web browser ကနေ access လုပ်ရပါလိမ့်မယ်။ နောက်ဆုံး အပိုင်းကတော့ အပေါ်မှာ MySQL ရဲ့ environmental variable တွေကို သတ်မှတ်သလိုပဲ WordPress အတွက် သတ်မှတ်ပေးလိုက်တာပါ။

အခုဆိုရင်တော့ customized container တစ်ခုတည်ဆောက်ဖို့ docker compose tool နဲ့ script နှစ်ခုလုံး အဆင်သင့် ဖြစ်ပါပြီ။ အောက်က command ကို အခုက ကိုယ် တည်ဆောက်ထားတဲ့ project directory အောက်ကမှာ ရိုက်ထည့်လိုက်ပါ။

```
$ docker-compose up -d 
```

ဒီနေရာမှာ -d ဆိုတဲ့ parameter က docker-compose up command ကို detached mode မှာ run လို့ ပြောလိုက်တာပါ။ အားလုံးအဆင်ပြေရင်တော့ အောက်ကအတိုင်း တွေ့ရပါလိမ့်မယ်။

```
~/docker-wp-project$ docker-compose up -d
Creating network “dockerwpproject_default” with the default driver
Creating volume “dockerwpproject_dbdata” with default driver
Pulling db (mysql:5.7)…
5.7: Pulling from library/mysql
4176fe04cefe: Pulling fs layer
d1e86691d483: Downloading [==================================================>] d1e86691d483: Download complete
ffadeffb3eb4: Downloading [> ] ffadeffb3eb4: Downloading [=> ] ffadeffb3eb4: Downloading [====> ] ffadeffb3eb4: Downloading [======> ] 4176fe04cefe: Pull complete
d1e86691d483: Pull complete
ffadeffb3eb4: Pull complete
6c2c640eac6b: Pull complete
cec6a6ff8ae8: Pull complete
af71dde5fa23: Pull complete
2546980014e4: Pull complete
a525a4f1d664: Pull complete
af610cdb4173: Pull complete
fe36edc2517a: Pull complete
Digest: sha256:4f9323cb4aeca062fd1a341b50c7721b9aef6bff3ded806dec0897323b8b7be8
Status: Downloaded newer image for mysql:5.7
Pulling wordpress (wordpress:latest)…
latest: Pulling from library/wordpress
8176e34d5d92: Pull complete
f6c81892adaa: Pull complete
c8125c73b868: Pull complete
5ef22f6299b6: Pull complete
8537460e9a8c: Pull complete
b837671b83f0: Pull complete
366ea9d8b411: Pull complete
c4dd539af472: Pull complete
445753fb3ee6: Pull complete
6811f6b5d500: Pull complete
2ca365cdc65d: Pull complete
c91023a57f04: Pull complete
dcf0735fda8a: Pull complete
6b23fdc3538b: Pull complete
2eed880b86fe: Pull complete
798b2e547e59: Pull complete
159be43511e4: Pull complete
b5605b08f665: Pull complete
20d8e9ec2764: Pull complete
Digest: sha256:670e4156377063df1a02f036354c52722de0348d46222ba30ef6a925c24cd46a
Creating dockerwpproject_db_1 … done
Creating dockerwpproject_db_1 …
Creating dockerwpproject_wordpress_1 … done
```

နောက်အဆင့်ကတော့ ကိုယ်ကြိုက်တဲ့ web browser ထဲမှာ localhost:8000 သို့မဟုတ် ကိုယ်ရဲ့ IP Address:8000 ဆိုတာကို ရိုက်ထည့်လိုက်ပါ။ အောက်ကအတိုင်း WordPress ကို install လုပ်ဖို့အတွက် အဆင်သင့်ဖြစ်သွား ပါပြီ။

<figure><img src="https://i.imgur.com/AbUs9Tw.png" alt=""><figcaption><p>WordPress Installation (Language Selection)</p></figcaption></figure>

<figure><img src="https://i.imgur.com/Z1DsSJs.png" alt=""><figcaption><p>WordPress Installation (Welcome Page)</p></figcaption></figure>

Prompt ထဲမှာပြထားတဲ့ အတိုင်းလိုတဲ့ဟာတွေကို ထည့်ပြီးတော့ ကိုယ်ကြိုက်သလို setup လုပ်သွားပြီးတော့ WordPress installation ကို ပြီးအောင်လုပ်ဖို့ နောက်ထက် ၃ မိနစ်လောက်ဆို အားလုံး အဆင်သင့်ဖြစ် ပါပြီ။

ကိုယ်က စမ်းပြီးတော့ ဒီ project ကို ကိုယ်စက်ပေါ်ကနေ လုံးဝ remove ပြန်လုပ်ချင်ရင်တော့ အောက်က command ကိုရိုက်ထည့်လိုက်ပါ။

```
$ docker-compose down –volumes
```

Docker မှာ WordPress ကို အခုလို အလွယ်တကူ မိနစ်ပိုင်း အတွင်းမှာ setup လုပ်လို့ရပါတယ်။ Docker မသုံးခင်ကဆို XAMPP လို solution stack တစ်ခုခု သုံးပြီးတော့ ကိုယ့်ရဲ့ WordPress တို့ MediaWiki တို့လို project တွေကို ကိုယ်စက်ပေါ်မှာ စမ်းသပ်သုံးပါ။ ပြဿနာက XAMPP တို့ WAMP တို့ MAMP တို့လို solution stack တွေက resource intensive ဖြစ်ပါတယ်။ Docker ကတော့ ပိုပြီးတော့ portable လည်းဖြစ်၊ lightweight လည်းဖြစ်တဲ့အတွက် ပိုအဆင်ပြေပါတယ်။ စာရေးသူ ကိုယ်တိုင် Windows OS ပဲရှိတယ်၊ Windows OS ပဲသုံးရမယ်ဆိုရင်တော့ XAMPP ကိုပဲသုံးဖြစ်ပါတယ်။ Docker ကိုသုံးတဲ့အခါမှာ Microsoft implementation ကို ရှောင်တဲ့ သဘောပါ။

<figure><img src="https://i.imgur.com/mLAP85D.jpeg" alt=""><figcaption><p>XAMPP</p></figcaption></figure>

#### Docker နဲ့ တခြား containers တွေကို ဆွဲယူသုံးပုံ

အထက်ကတစ်ခုကတော့ docker-compose ကိုသုံးပြီးတော့ customized WordPress container တစ်ခုတည်ဆောက်ပုံကို ရှင်းပြထားတာပါ။ ဒီအပိုင်းကတော့ Docker ကိုလက်တွေ့ အသုံးချပုံကို ဒုတိယ ဥပမာ အနေနဲ့ ပြချင်တာပါ။

ဆိုပါတော့ ကိုယ်က Ubuntu ဆိုတဲ့ container ကို Docker Hub ပေါ်ကနေ ဆွဲယူ သုံးချင်တယ်ဆိုရင်တော့ အောက်က command ကို ရိုက်ထည့်လိုက်ရုံပါပဲ။

```
$ sudo docker run -it ubuntu
[sudo] password for tyla:
Unable to find image ‘ubuntu:latest’ locally
latest: Pulling from library/ubuntu
1be7f2b886e8: Pull complete
6fbc4a21b806: Pull complete
c71a6f8e1378: Pull complete
4be3072e5a37: Pull complete
06c6d2f59700: Pull complete
Digest: sha256:e27e9d7f7f28d67aa9e2d7540bdc2b33254b452ee8e60f388875e5b7d9b2b696
Status: Downloaded newer image for ubuntu:latest
root@49f8a606967a:/#
```

အထက်မှာတွေ့ရတဲ့ အတိုင်း Ubuntu container က အဆင်သင့်ဖြစ်ပြီ ဆိုရင် root ဆိုတဲ့ prompt လေးတစ်ခု ပေါ်လာပါလိမ့်မယ်။ ဒါဆိုရင်တော့ ကိုယ်က Ubuntu container ရဲ့ အထဲမှာ root အနေနဲ့ ရောက်နေပြီလို့ ပြောလို့ရပါတယ်။ တခုရှိတာက Ubuntu container မှာ သုံးလို့ရတဲ့ command တွေက Full Blown Ubuntu installation မှာလိုမျိုးတော့ အလုံးစုံ မပါဝင်ပါဘူး။ Docker container ဖြစ်တဲ့အတွက် strip down version၊ lightweight distro တခုလိုမျိုးလောက်သာဖြစ်ပါတယ်။ သို့သော်လည်း full blown Ubutnu မှာလို ကိုယ် install လုပ်ချင်တာတွေကို ထပ်ပြီးတော့ ထည့်လို့တော့ရပါတယ်။

တခြား Docker container တွေကိုလည်း စိတ်ဝင်စားလို့ စမ်းကြည့်ချင်တယ်ဆိုရင်လည်း ဒီ [link](https://hub.docker.com/explore/) မှာသွားကြည့်ပြီးတော့ pull လုပ်လို့ရပါတယ်။ run လုပ်လို့ရပါတယ်။

<figure><img src="https://i.imgur.com/w16AEEB.jpeg" alt=""><figcaption><p>Docker Hub</p></figcaption></figure>

Docker မိတ်ဆက်ကို ဒီမှာပဲ ရပ်လိုက်ပါတော့မယ်။ အပိုင်း ၃ ပိုင်းလည်း ရေးပြီးသွားပြီဆိုတော့ မိတ်ဆက်အတွက်တော့ တော်တော်လေးလုံလောက်သွားပြီလို့ စာရေးသူထင်ပါတယ်။ နောက်ပိုင်းမှာတော့ Docker နဲ့ ပတ်သတ်ပြီး ပိုပြီးတော့ အဆင့်မြင့်တဲ့ အကြောင်းလေးတွေကို ဆက်ရေးဖို့တော့ ရှိပါတယ်။
