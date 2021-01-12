# အနားမသပ်နိုင် သေးတဲ့ Infrastructure as Code \(IaC\) – အပိုင်း\(၂\)

### Vagrant မိတ်ဆက်

ပထမဆုံး မိတ်ဆက်ပေးချင်တဲ့ lightweight IaC tool ကတော့ Vagrant ပဲဖြစ်ပါတယ်။ သူ့ကို HashiCorp ကနေပြီးတော့ develop လုပ်တာဖြစ်ပြီးတော့၊ open-source လုပ်ပေးထားတဲ့ tool တစ်ခုပါ။ Virtualisation platform တော်တော်များ နဲ့ cloud platform အချို့ မှာ အသုံးပြုလို့ရတဲ့အတွက် developer တွေ၊ DevOps တွေအတွက် အတော်လေးကိုအသုံးတည့်တဲ့ tool တစ်ခုလည်းဖြစ်ပါတယ်။ အဓိက back-end core language ကိုတော့ Ruby နဲ့ ရေးထားတာဖြစ်ပြီး၊ ခုနှစ်အားဖြင့် ၂၀၁၀ ဇန်နဝါရီလတွင်းမှာ Mitchell Hashimoto ကကိုယ်တိုင်အသုံးပြုဖို့ရာအတွက် စတင်လိုက်တဲ့ project လေးတစ်ခုပါ။ ၂၀၁၀ ခုနှစ် မတ်လလောက်ကျမှ ပထမဆုံး version ကိုစတင်ပြီး release လုပ်ပါတယ်။ ပထမဆုံး stable release ဖြစ်တဲ့ Vagrant 1.0 ကိုတော့ ၂၀၁၂ မတ်လမှပဲ release လုပ်နိုင်ခဲ့ပါတယ်။ Vagrant ဟာအစပိုင်းကတည်းက Oracle ရဲ့ Virtualbox အတွက် အတော်လေးအဆင်ပြေအောင်လို့ လုပ်ထားရာကနေပြီး နောက်ပိုင်းမှာ တဖြေးဖြေးနဲ့ အခြားသော virtualisation platform တွေဖြစ်တဲ့ VMware နဲ့ KVM တွေကိုပါ support လုပ်လာတယ်။ ဒီလိုနဲ့ နောက်ပိုင်းမှာ AWS EC2 instance တွေနဲ့ Docker container တွေကိုပါ ထပ်တိုး support လုပ်ပြန်လာပါတယ်။ စာရေးသူရဲ့ အတွေ့အကြုံအရတော့ အခုအချိန်ထိ Vagrant ကိုသုံးပြီးတော့ portable dev/test environment တစ်ခုတည်ဆောက်ဖို့ Virtualbox ဟာ အကောင်းဆုံးသော platform တစ်ခုပါ။ အခြားသော platform တွေမှာလည်း အလုပ်လုပ်သော်လည်း ထပ်တိုးပေါင်းပြီးတော့ install လုပ်ရတဲ့ component လေးတွေရှိတာကြောင့် နည်းနည်းလေ အလုပ်ပိုပါလိမ့်မယ်။

Vagrant မှာ အဓိက အပိုင်း နှစ်ပိုင်းကို နားလည်ထားရပါ့မယ်။ တစ်ခုက provider လို့ခေါ်တဲ့ သူနဲ့တွဲပြီးတော့ အသုံးပြုနိုင်တဲ့ virtualisation platform တွေနဲ့ ရွေးချယ်နိုင်စရာ သူ့ရဲ့ option အချို့မှာ အနည်းအကျဉ်းစီ ကွာခြားနိုင်ပါတယ်။ Provider ဆိုတာတွေကတော့ အထက်မှာဆိုခဲ့တဲ့ Virtualbox, Hyper-V နဲ့ Docker တို့လို native support လုပ်တဲ့ platform တွေပဲဖြစ်ပြီး၊ VMware နဲ့ AWS လိုမျိုး platform တွေအတွက်တော့ plugin တွေထပ်ပေါင်းထည့်ရပါလိမ့်မယ်။ နောက်ဒုတိယ တစ်ခုကတော့ provisioner လို့ခေါ်တဲ့အပိုင်းတစ်ခုပါ။ ဒီ provisioner ဆိုတာကတော့ ကိုယ် provider နဲ့ ဖန်တီးထားတဲ့ dev environment တစ်ခုရဲ့ VM/Container တစ်ခုစီမှာထပ်ပေါင်းထည့်ချင်တဲ့ system တစ်ခုချင်းစီရဲ့ customised configuration တွေကိုပါ automate လုပ်လို့ရအောင်ပါ။ အရှင်းဆုံးပြောရရင်တော့ Vagrant ဟာ ကိုယ်သုံးမယ် virtualisation platform ရဲ့ wrapper တစ်ခုအနေနဲ့ ခြုံအုပ်ပေးထားပါတယ်။ Imperative အမျိုးအစားထဲမှာပါတာဖြစ်တဲ့ အတွက် အသေးစိတ်ရေးသားပြီးတော့ အောက်ခြေသိမ်းလိုက်ပြီးတော့ ရေးချင်ကရေးနိုင်ပါတယ်။ ကိုယ် interface လုပ်မယ့် provider ကိုပြောပြီးတော့ လိုချင်တဲ့ resource ကို ပြောပေးလိုက်ရုံပါပဲ။ Vagrantfile ဆိုတဲ့တစ်ခုကို တည်ဆောက်ပေးပြီး vagrant CLI commands တွေကို အသုံးပြီးတော့ automate/orchestrate လုပ်နိုင်ပါပြီ။ Vagrantfile ကို Ruby syntax နဲ့ရေးထားတာဖြစ်လို့ programming တစ်ခုကိုအသုံးပြုသကဲ့သို့ သုံးနိုင်သလို၊ declarative ပုံစံလိုမျိုး YAML ကိုအသုံးပြီးတော့လည်းရေးသားနိုင်ပါတယ်။

### Vagrant ကို install လုပ်ပုံ

Vagrant ကို install လုပ်ဖို့အတွက်တော့ ဒီလင့်မှာ “https://www.vagrantup.com/downloads.html” သွားပြီး ကိုယ်အသုံးပြုတဲ့ OS ပေါ်မှာမူတည်ပြီးတော့ download လုပ်ကာ၊ install လုပ်နိုင်ပါတယ်။ စာရေးသူမှာတော့ Ubuntu 20.04 LTS ကိုသုံးတဲ့အတွက် “sudo apt install vagrant” ဆိုတာနဲ့ Vagrant ကို စတင်အသုံးပြုဖို့ အတွက် အဆင်သင့်ဖြစ်ပါပြီ။

![Vagrant Download Page](https://i1.wp.com/www.itmatic101.com/wp-content/uploads/2020/12/vagrant_download-745x1024.png?resize=740%2C1017&ssl=1)

### Vagrant လက်တွေ့အသုံးဝင်ပုံ

Vagrant ကိုများသောအားဖြင့် စာရေးသူ local machine ရဲ့ Virtualbox မှာ lab environment တစ်ခုကို setup လုပ်ဖို့အတွက်အသုံးပြုပါတယ်။ ဆိုပါတော့… Nginx ရဲ့ load balancer နဲ့ web server တွေကိုစမ်းသပ်ချင်တာပဲဖြစ်ဖြစ်၊ BIND ရဲ့ DNS primary နဲ့ secondary server ဟာမျိုးစမ်းချင်တာပဲဖြစ်ဖြစ်၊ ဒီထက်ပိုပြီးတော့ DevOpsie ဆန်ချင်ရင်တော့ K8s cluster တစ်ခုကိုတည်ဆောက်ပြီး စမ်းချင်တာပဲဖြစ်ဖြစ်၊ ကိုယ်ကြိုက်တဲ့ environment ကို Vagrantfile ထဲမှာသိမ်းထားပြီးတော့ git repo တစ်ခုဖွဲ့ကာ GitHub မှာပဲဖြစ်ဖြစ်၊ GitLab မှာပဲဖြစ်ဖြစ် တင်ထားလိုက်ရုံပါပဲ။ ကိုယ်တစ်ခုခုပြောင်းချင်ပြုချင်တယ်ဆိုရင် လိုအပ်တဲ့အပိုင်းကို ပြင်ဆင်ပြီးတော့ code ကို git နဲ့ update လုပ်လိုက်ရုံပါ။ နောင်တခါ အရင် version မှာကိုယ် ဘာတွေပြောင်းလာခဲ့သလဲဆိုတာကို git ကသိမ်းပြီးတော့ version control လုပ်ပြီးသားဖြစ်သွားပါရော။ ဒီအတွက် ကိုယ်စမ်းမယ့် dev environment တစ်ခုကို VM တစ်လုံးခြင်းစီ တည်ဆောက်ပြီးတော့ configure လုပ်ယူမည့်အစား Infrastructure as Code \(IaC\) နည်းနာကို သုံးပြီးတော့ deploy လုပ်လို့ရပါတယ်။

အောက်မှာ… Vagrant ရဲ့ အရိုးရှင်းဆုံးပုံစံနဲ့ web server တစ်ခုကို virtualbox မှာ deploy လုပ်တဲ့ပုံစံပါ။

```text
VagrantfileVagrant.configure("2") do |config|
   config.vm.box = "ubuntu/trusty64"
   config.vm.synced_folder ".", "/var/www/html"
   config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = 1024
     vb.cpus = 1
   end
 
   config.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
   SHELL
end
```

ပထမဆုံး line က Vagrant ကိုအသုံးပြုပြီး configure လုပ်ချင်တဲ့ config ဆိုတဲ့ code block တစ်ခုကိုတည်ဆောက်လိုက်ပြီးတော့ ကိုယ်လိုချင်တဲ့ parameter တွေကို သတ်မှတ်ပေးတဲ့ပုံစံပါ။ config.vm.box = “ubuntu/trusty64” ဆိုတာက Vagrant Cloud ပေါ်က ubuntu ရဲ့ account အောက်မှာ trusty64 ဆိုတဲ့ vagrant box ကို download ဆွဲပြီး သုံးမယ်လို့ဆိုလိုတာပါ။ Docker Hub လိုပဲ Vagrant မှာလည်း Vagrant Cloud ဆိုပြီး vagrant box တွေကို စုစည်းပေးထားတဲ့ နေရာပါ။ URL အနေနဲ့တော့ ဒီနေရာမှာ “https://app.vagrantup.com/ubuntu/boxes/trusty64” သွားကြည့်လို့ရပါတယ်။ ကိုယ်တိုင်လည်း local machine ပေါ်မှာ vagrant box တွေကိုစိတ်ကြိုက်တည်ဆောက်ပြီးတော့ ထည့်သွင်းအသုံးပြုလို့ရပါတယ်။ နောက် line ကတော့… config.vm.synced\_folder “.”, “/var/www/html” ဖြစ်ပြီး၊ ဒီတခါဟာ virtualbox ရဲ့ shared folder feature ကိုအသုံးပြုပြီး file တွေ၊ folder တွေကို host နဲ့ VM ကြားမှာ sync လုပ်မယ်လို့ ဆိုတာပဲဖြစ်ပါတယ်။ ဒီလိုလုပ်ခြင်းအားဖြင့် VMရဲ့ “/var/www/html”တွင်းမှာရှိတဲ့ file ကို edit လုပ်ချင်ရင် ကိုယ်လက်ရှိ Vagrantfile ကို run နေတဲ့ directory ထဲနေလှမ်းပြီးတော့ပြင်ဆင်၊ ထည့်ပေါင်း၊ နုတ်ယူနိုင်အောင်လို့ပါ။ web server လိုမျိုး server တွေရဲ့ အဲ့ဒီလို directory တွေဟာ အသုံးအပြုဆုံးသော နေရာဖြစ်တဲ့အတွက် အခုလိုလုပ်ကြတာပဲဖြစ်ပါတယ်။

နောက်တခုက config.vm.provider “virtualbox” do \|vb\| ဖြစ်ပါတယ်။ ဒီ line မှာတော့ provider ကို virtualbox ပါလို့ဆိုပြီး vb ဆိုတဲ့ code block တစ်ခုကို ဖန်တီးလိုက်ခြင်းဖြစ်ပါတယ်။ အဲ့ဒီအောက်မှာ… VM မှာကိုယ်လိုချင်တဲ့ spec တွေနဲ့ option တွေကို ရွေးချယ်သတ်မှတ်ပေးနိုင်ပါတယ်။ vb.gui = false ဆိုတာက… VM boot တက်တဲ့အခါကြရင် headless ပုံစံမျိုး boot တက်စေချင်ပြီး၊ vb.memory = 1024 ဆိုတာက… RAM ကို 1GB ပေးမယ်ပြီးတော့၊ vb.cpus = 1 ဆိိုတာက… virtual cpu တစ်ခုပေးမယ်လို့ ဆိုချင်တာပါ။ ဒီလိုဆိုရင်… သက်ဆိုင်ရာ VM ရဲ့ provider နဲ့ ဆိုင်တဲ့ အပိုင်းမှာ ရပါပြီ။

နောက်တပိုင်းမှာက… config.vm.provision “shell”, inline: &lt;&lt;-SHELL ဆိုထားပါတယ်။ ဒါလည်းရှင်းပါတယ်… provision ကို Linux ရဲ့ CLI shell ကိုသုံးမယ်… inline မှာကိုယ် run ချင်တဲ့ commands ကိုထည့်ပေးလိုက်ရုံပါ။ မြင်တဲ့အတိုင်း Apache web server ကို native CLI သုံးပြီးတော့ update လုပ်သွားတာပဲဖြစ်ပါတယ်။ ကိုယ်က shell ကိုမသုံးချင်ဘူး Ansible လိုမျိုး tool set ကို provision အတွက်သုံးမယ်ဆိုလည်း ရပါတယ်။ ဒီမှာတော့ ရှင်းအောင်လို့ shell ကိုပဲသုံးပြထားပါတယ်။ Shell မှာမှ ဒီထက်ပိုပြီးတော့ ရှုပ်ထွေးတဲ့ commands တွေကို provision ထဲမှာသုံးချင်ရင် အောက်မှာပြထားတဲ့အတိုင်း လုပ်လို့ရပါတယ်။ bootstrap.sh ဆိုတဲ့ bash script တစ်ခုလိုပါလိမ့်မယ်။

```text
VagrantfileVagrant.configure("2") do |config|
   config.vm.box = "ubuntu/trusty64"
   config.vm.synced_folder ".", "/var/www/html"
   config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = 1024
     vb.cpus = 1
   end
   
   config.vm.provision "shell", path: "bootstrap.sh"
end
```

{% code title=" bootstrap.sh" %}
```text
apt-get update
apt-get upgrade

apt-get install -y git
apt-get install -y apache2
a2enmod rewrite

apt-add-repository ppa:ondrej/php
apt-get update
apt-get install -y php7.2
apt-get install -y libapache2-mod-php7.2
service apache2 restart

apt-get install -y php7.2-common
apt-get install -y php7.2-mcrypt
apt-get install -y php7.2-zip

debconf-set-selections <<< 'mysql-server mysql-server/root_password password root'
debconf-set-selections <<< 'mysql-server mysql-server/root_password_again password root'

apt-get install -y mysql-server
apt-get install -y php7.2-mysql
sudo service apache2 restart
```
{% endcode %}

ဟုတ်ပြီ… အခုအချိန်ထိတော့ VM တစ်ခုကို provider နဲ့ provisioner ကိုအသုံးပြုပြီးတော့ IaC ပုံစံမျိုး တည်ဆောက်ပြသွားတာအဆင်ပြေပါတယ်။ Git repo တွေဘာတွေအသုံးပြုပြီး version control ဆက်လုပ်လို့ရပါပြီ။ သို့သော်… ကိုယ်က Nginx အတွက်ဖြစ်ဖြစ်၊ K8s အတွက်ဖြစ်ဖြစ် cluster တစ်ခုတည်ဆောက်ဖို့အတွက်ဆိုရင်တော့ တစ်လုံးထက်ပိုတဲ့ VM တွေကိုလိုပါပြီ။ ဆိုပါတော့… VM အလုံးရေ ၆ လုံးကို တစ်ပြိုင်နက်တည်း deploy လုပ်ချင်တယ်၊ ၃ လုံးကို Ubuntu လိုချင်ပြီး၊ အခြားသုံးလုံးကိုတော့ CentOS လိုချင်တယ်ဆိုပါတော့ဗျာ။ အောက်မှာတော့… အဲ့ဒီလိုမျိုး mixed cluster လုပ်တဲ့ပုံစံကို ပြပေးထားပါတယ်။

```text
VagrantfileUBOX_IMAGE = "bento/ubuntu-20.04"
UBOX_COUNT = 3
CBOX_IMAGE = "bento/centos-8.2"
CBOX_COUNT = 3

 Vagrant.configure("2") do |config|
   (1..UBOX_COUNT).each do |x|     
     config.vm.define "ubuntu#{x}" do |subconfig|       
       subconfig.vm.box = UBOX_IMAGE       
       subconfig.vm.hostname = "ubuntu#{x}"       
       subconfig.vm.network :private_network, ip: "10.0.0.#{x + 100}"     
   end
 end 

 (1..CBOX_COUNT).each do |y|     
     config.vm.define "centos#{y}" do |subconfig|       
       subconfig.vm.box = CBOX_IMAGE       
       subconfig.vm.hostname = "centos#{y}"       
       subconfig.vm.network :private_network, ip: "10.0.0.#{y + 200}"     
     end
  end 
 
  config.vm.provider "virtualbox" do |vb|
     vb.gui = false
     vb.memory = 1024
     vb.cpus = 1
  end
 
  config.vm.provision "file", source: "./me.pub", destination: "~/.ssh/me.pub"

  config.vm.provision "shell", inline: <<-SHELL     cat /home/vagrant/.ssh/me.pub >> /home/vagrant/.ssh/authorized_keys
     SHELL
end
```

ဒီတခါတော့… variable တွေကိုအသုံးပြီးတော့ bento ရဲ့ vagrant box တွေကို Vagrant Cloud ပေါ်ကနေပြီးတော့ download ဆွဲပြီး သုံးမယ်လို့ အစမှာ ပြောလိုက်ပါတယ်။ ပြီးရင်… VM name၊ hostname နဲ့ IP address အတွက် loop ကိုအသုံးပြီးတော့ dynamic ဖြစ်အောင်လုပ်လိုက်ပါတယ်။ provider အပိုင်းမှာတော့ အထက်ကပုံစံနဲ့ အကုန်တူညီပြီးတော့၊ provisioner အပိုင်းမှာ စာရေးသူရဲ့ ssh public key ကို VM တိုင်းစီမှာ တင်လိုက်ပြီးတာနဲ့ ssh ရဲ့ authorized\_keys file မှာလည်း entry တစ်ခုသွားထည့်လိုက်တာကိုပြထားပါတယ်။ ဒီလိုလုပ်ခြင်းအားဖြင့် VM တစ်ခုချင်းစီကို password မလိုပဲနဲ့ keybase authentication လုပ်လို့ တခါတည်းရသွားပါတယ်။

Vagrantfile မှာပါတဲ့အရာတွေကို ရှင်းပြသွားတာတော့ ပြည့်စုံသလောက်ရှိပြီ။ လိုနေတာနောက်ဆုံးတစ်ခုက… အဲ့ဒီ Vagrantfile တွေကို ဘယ်လိုမျိုး run ရမှာလဲဆိုတာပါ။ CLI commands တွေက docker ရဲ့ commands တွေနဲ့ ခပ်ဆင်ဆင်ပါ။ အများကြီးလည်းမရှိပါဘူး။ အထက်မှာပြောတဲ့ Vagrantfile ရှိတဲ့ directory ထဲကိုသွားပြီး “vagrant up” လို့ရိုက်ထည့်လိုက်တာနဲ့ ကိုယ့် script မှာဘာ error မှလည်း မရှိဘူးဆိုရင်၊ လိုအပ်တဲ့ vagrant box တွေကို Vagrant Cloud ပေါ်ကနေဆွဲပြီးတော့ dev environment တစ်ခုကိုစတင်ပြီး deploy လုပ်ပါတယ်။ ပြီးတာနဲ့ “vagrant status” ဆိုပြီးတော့ လက်ရှိ run နေတဲ့ vagrant box တွေရဲ့ name နဲ့ လက်ရှိ status ကိုပြပါလိမ့်မယ်။ ကိုယ် ssh နဲ့ဝင်ချင်တဲ့ VM ကို “vagrant ssh \[VM\_NAME\]” ဆိုပြီးတိုက်ရိုက်ဝင်နိုင်ပါတယ်။ ကိုယ်စမ်းသပ်လို့ ပြီးရင် VM တွေကို shutdown ချချင်တာပဲဖြစ်ဖြစ်၊ suspend လုပ်ချင်တာပဲဖြစ်ဖြစ် “vagrant halt” နဲ့ “vagrant suspend” ကိုသုံးလို့ ရပါတယ်။ ဒီလိုမှမဟုတ်ဘူး… စမ်းထားသမျှ အားလုံးကို disk space သက်သာအောင် အားလုံးဖျက်စီးလိုက်ချင်ရင်တော့ “vagrant destroy -f” ဆိုပြီးတော့လုပ်လို့ ရသလို၊ “vagrant destroy \[VM\_NAME\]” ဆိုပြီး တစ်လုံးတည်းသော VM ကို ဖျက်စီးပစ်ချင်လည်း ရပါတယ်။

```text
Common commands:
      address         outputs the IP address of a guest.
      box             manages boxes: installation, removal, etc.
      cloud           manages everything related to Vagrant Cloud
      destroy         stops and deletes all traces of the vagrant machine
      global-status   outputs status Vagrant environments for this user
      halt            stops the vagrant machine
      help            shows the help for a subcommand
      init            initializes a new Vagrant environment by creating a Vagrantfile
      login           
      package         packages a running vagrant environment into a box
      plugin          manages plugins: install, uninstall, update, etc.
      port            displays information about guest port mappings
      powershell      connects to machine via powershell remoting
      provision       provisions the vagrant machine
      push            deploys code in this environment to a configured destination
      rdp             connects to machine via RDP
      reload          restarts vagrant machine, loads new Vagrantfile configuration
      resume          resume a suspended vagrant machine
      snapshot        manages snapshots: saving, restoring, etc.
      snapshot-info   Snapshot additional information.
      ssh             connects to machine via SSH
      ssh-config      outputs OpenSSH valid configuration to connect to the machine
      status          outputs status of the vagrant machine
      suspend         suspends the machine
      up              starts and provisions the vagrant environment
      upload          upload to machine via communicator
      validate        validates the Vagrantfile
      version         prints current and latest Vagrant version
      winrm           executes commands on a machine via WinRM
      winrm-config    outputs WinRM configuration to connect to the machine
 
For help on any individual command run vagrant COMMAND -h

Additional subcommands are available, but are either more advanced
or not commonly used. To see all subcommands, run the command
vagrant list-commands.
```

အခုဆိုရင်… ကိုယ်တည်ဆောက်ထားတဲ့ dev environment၊ တနည်းအားဖြင့် infrastructure တစ်ခုကို code တစ်ခုအသွင်နဲ့ သိမ်းဆည်းလိုက်ခြင်းဖြင့်၊ နောက် DevOps တစ်ယောက်က ၄င်း environment ကိုတစ်ပုံစံတည်း လိုချင်ရင် ကိုယ့်ရဲ့ code ကို git repo ကနေ share လိုက်ရုံပါ။ ဘာမှအများကြီး လွှဲမှားစရာမရှိတော့ပါဘူး။ ဆိုင်ရာ Vagrantfile တွေနဲ့ bootstrap.sh file တွေကို GitHub ရဲ့ ဒီ [link](https://github.com/tylalin/ITmatic101/tree/master/infra_as_code/vagrant_files) ကလေး မှာတင်ပေးထားပါတယ်။

ဒီလောက်ဆိုရင်… Vagrant နဲ့ ပတ်သတ်တဲ့ IaC ဆိုင်ရာ အသုံးဝင်ပုံ အသုံးပြုပုံ အတွက်လုံလောက်ပြီလို့ ထင်ပါတယ်။ နောက် post မှာ Terraform လို့ခေါ်တဲ့ IaC မှာသုံးတဲ့ tool set တစ်ခုအကြောင်းဆက်သွားချင်ပါတယ်။ ဒီ post ကိုတော့ ဒီလောက်နဲ့ပဲရပ်လိုက်ပါတော့မယ်။  


