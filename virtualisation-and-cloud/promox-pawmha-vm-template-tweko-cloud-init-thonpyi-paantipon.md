---
cover: >-
  https://images.unsplash.com/photo-1497290756760-23ac55edf36f?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw5fHxjbG91ZC1pbml0fGVufDB8fHx8MTY5OTE3OTQ3MXww&ixlib=rb-4.0.3&q=85
coverY: 0
---

# Promox ပေါ်မှာ VM template တွေကို cloud-init သုံးပြီး ဖန်တီးပုံ

စာရေးသူ Promox ကို home lab မှာ အများဆုံးအသုံးပြုတဲ့ ဖြစ်ပါတယ််။ အကြောင်းမူက Type 1 hypervisor တွေထဲမှာ install လုပ်ရတာလည်း လွယ်သလို၊ သူနဲ့ပါလာတဲ့ LXC container နည်းပညာဟာလည်း အလွန်ကို အသုံးတည့်တဲ့ system containerisation တစ်ခုဖြစ်လို့ပါပဲ။ ဒီနေရာမှာ ပြောစရာရှိတာက Type 1 hypervisor တွေထဲမှာ၊ VMware ရဲ့ ESXi ရှိသလို၊ qemu ကိုအသုံးပြုထားတဲ့ KVM နဲ့ Ubuntu ပေါ်မှာ run တဲ့ LXD တွေကိုအသုံးပြုချင်လည်းရတာပေါ့။ သို့သော်… VMware ESXi ကိုအသုံးပြုတဲ့အခါမှာ open-source မဟုတ်တာတစ်ခုရယ်၊ Type 1 hypervisor မှာရနိုင်တဲ့ feature တွေအကုန်လုံးကို non-commercial မှာမရနိုင်လို့ရယ်မို့ အရင်က အိမ်မှာအသုံးပြုဖူးပေမယ့် ဆက်ပြီးတော့ အသုံးပြုဖို့ စိတ်မယိုင်တော့ပါဘူး။ KVM ကို Ubuntu သို့မဟုတ် RockyLinux ပေါ်မှာတင်ပြီးတော့ အသုံးပြုချင်လည်း ဖြစ်နိုင်ပါတယ်။ ဒါပေမယ့်… သူနဲ့တွဲသုံးမည့် virtual machine manager လို tool တွေဟာပြီးပြည့်စုံတယ်လို့ မခံစားရတာတခု၊ KVM အတွက်အသုံးပြုတဲ့ virsh လို CLI tool တွေအတွက်လည်း သီးသန့်လေ့လာရမယ့် ဟာတွေဖြစ်နေတာကြောင့်ရယ်မို့ home lab အတွက်အဆင်မပြေဘူးလို့ထင်ပါတယ်။ အချိန်ရရင်တော့လည်း သီးသန့်လေ့လာချင်ပါတယ်။ အခုတော့… အချိန်မပေးချင်သေးလို့ ဆင်ခြေကန်နေသေးပုံပါ။ နောက်တခုက Ubuntu ပေါ်မှာ LXD ကို run ပြီး LXC container ရော၊ qemu ကိုပဲသုံးပြီးတော့ run တဲ့ LXC virtual machine အတွက်ပါအသုံးနိုင်ပါတယ်။ သို့ပေမယ့်… virtual machine ကိုအသုံးများမယ်ဆိုရင်တော့ သိပ်ပြီးတော့ အဆင်မပြေနိုင်ပါဘူး။ လက်ရှိ LXC မှာရနိုင်တဲ့ official VM image ကအများကြီးမရှိသေးပါဘူး။ ဒီ့အတွက်ကြောင့်… စာရေးသူအတွက်တော့ အဆင်ပြေဆုံး solution က Promox လို့ပဲထင်မိပါတော့တယ်။ အချို့လည်း Promox ကို မကြိုက်တဲ့သူတွေအများကြီးရှိပါတယ်။ စာရေးသူအတွက်တော့ ကိုယ်သုံးမယ့် use case နဲ့ ကိုက်နေလို့လည်း ဖြစ်နိုင်ပါတယ်။

ဒီ post မှာတော့… စာရေးသူ ဝေမျှချင်တာက Promox ပေါ်တွင် VM template တွေကို cloud image သုံးပြီး အလွယ်တကူ ဖန်တီးနိုင်သလဲဆိုတာပဲဖြစ်ပါတယ်။ ဤသို့ template တွေကို ဖန်တီးဖို့အတွက် cloud-init ကိုလည်း VM instance ရဲ့ ပထမအကြိမ် boot တက်တဲ့အခါမှာ update လုပ်စရာရှိတာတွေလုပ်ဖို့နဲ့ hostname ကို VM နာမည်အတိုင်းလိုက် ပြောင်းနိုင်ဖို့အတွက်သာသုံးပါတယ်။ ကျန်တဲ့အပိုင်းတွေအတွက်တော့ virt-customize နဲ့ Promox ရဲ့ qm command တွေသုံးပါတယ်။ တခုသိထားရမှာက virt-customize ကို Promox ပေါ်မှာ install လုပ်တဲ့အခါ၊ subscription မရှိရင် Promox ရဲ့ repo ကိုအရင်ဆုံး disable လုပ်ထားဖို့လိုပါလိမ့်မယ်။ ပြီးတော့မှ Debian ရဲ့ generic repo တွေကိုသုံးကာမှ virt-customize ကို install လုပ်လို့ရပါတယ်။ သူ့ကို Promox မှာ install လုပ်ဖို့အတွက် အောက်က အတိုင်း command နဲ့ install လုပ်နိုင်ပါတယ်။ Promox host ကို root account နဲ့ ssh remote connect လုပ်ဖို့တော့လိုပါလိမ့်မယ်။

```
$ apt update -y && apt install libguestfs-tools -y
```

ပြီးရင်တော့ လုပ်ငန်းစဖို့အတွက် Ubuntu 22.04 LTS cloud image ကိုအောက်မှာပြထားတဲ့အတိုင်း download ဆွဲလိုက်ပါ။ စာရေးသူ ဒီမှာ Ubuntu ရဲ့ နောက်ဆုံးထွက်တဲ့ LTS ကိုသုံးထားတယ်။ ဘယ် cloud image နဲ့ပဲဖြစ်ဖြစ် အဆင်ပြေပါလိမ့်မယ်။ ကိုယ်လိုချင်တဲ့ image ကို စိတ်ချရတဲ့ source ကနေရနိုင်ပါတယ်။ Custom image တည်ဆောက်ပုံကတော့ အတူတူပါပဲ။

```
$ wget https://cloud-images.ubuntu.com/jammy/current/jammy-server-cloudimg-amd64.img
```

လိုချင်တဲ့ cloud image ရပြီဆိုရင် virt-customize ကိုအသုံးပြုပြီး စာရေးသူတို့ install လုပ်ချင်တဲ့ package တွေကို image ထဲ inject လုပ်လို့ရပါပြီ။

```
# install all desired packages in the cloud image 
$ virt-customize -a jammy-server-cloudimg-amd64.img --install qemu-guest-agent,vim,bash-completion,wget,curl,unzip
```

ဒါပြီးတော့ install လုပ်ပြီးသား package တွေကို update လုပ်ပါ့မယ်။

```
# update all installed packages in the image
$ virt-customize -a jammy-server-cloudimg-amd64.img --update
```

Timezone ကိုလည်းအခုလိုမျိုး လိုတဲ့အတိုင်း setup လုပ်လို့ရပါတယ်။

```
# set preferred timezone
$ virt-customize -a jammy-server-cloudimg-amd64.img --timezone "Myanmar/Yangon"
```

တကယ်လို့များ public key authentication ကိုအသုံးပြုပြီးတော့ VM instance ထဲကို ssh နဲ့ဝင်ချင်ရင်တော့၊ ပထမဆုံး ကိုယ့်ရဲ့ ssh public key ကို Promox host ပေါ်အရင် copy ကူးယူလိုက်ပါ။ ဒါဆိုရင်တော့ အောက် command ကိုအသုံးပြုပြီး ssh key ကို cloud image ထဲကို inject လုပ်လို့ရပါပြီ။

```
# copy the ssh pubkey into the image
# that id_rsa.pub needs to be uploaded to the host in piror to run this command
$ virt-customize -a jammy-server-cloudimg-amd64.img --ssh-inject root:file:./id_rsa.pub
```

ဒါကိုကြည့်ခြင်းအားဖြင့် virt-customize tool ဟာ ဘယ်လောက်တောင်အလုပ်ဖြစ်သလဲဆိုတာတွေ့ရမှာပါ။ ဒီ post မှာက အသုံးများတဲ့ပုံစံမျိုးကိုသာ ထည့်သွင်းအသုံးပြုပြသွားတာဖြစ်ပါတယ်။ ဒီထက်ပိုပြီးတော့ ကိုယ့်အတွက်အသုံးတည့်နိုင်မည့် လက်တွေ့ အသုံးချချင်လည်း ဖြစ်နိုင်ပါသေးတယ်။ လိုချင်တဲ့ custom image ပုံရပြီဆိုရင် စပြီးတော့ VM တခုကိုအရင် တည်ဆောက်ကြည့်လိုက်ရအောင်ဗျ။

ဒီမှာတော့… ပထမဆုံးအနေနဲ့ ကိုယ်လိုချင်တဲ့ VM specs ကိုသတ်မှတ်ပေးပြီး “jammy-server-cloudimage-template” လို့နာမည်ပေးလိုက်ပါတယ်။ ဒီနေရာမှာ 1001 ဆိုတာက VM အတွက်သတ်မှတ်ပေးထားတဲ့ unique VM ID ပါ။

```
# create a new VM instance with desired specs
$ qm create 1001 --name "jammy-server-cloudimg-template" --memory 1024 --cores 1 --net0 virtio,bridge=vmbr0
```

VM ကိုတည်ဆောက်ပြီးတာနဲ့ အစောကကြိုတင်ပြင်ဆင်ထားတဲ့ custom image ကို system disk အနေနဲ့ VM 1001 ထဲကို import လုပ်လိုက်ပါတယ်။ local-lvm ဆိုတာက VM ရဲ့ disk အတွက် သတ်မှတ်ထားတဲ့ target storage resource ပါ။

```
# import the prep cloud image to the VM with target storage location
$ qm importdisk 1001 jammy-server-cloudimg-amd64.img local-lvm
```

ပြီးရင်… လိုအပ်တဲ့ SCSI driver ကိုအောက်မှာပြထားတဲ့ အတိုင်း setup လုပ်ပါတယ်။ ဒါ့အပြင် VM အတွက်လိုအပ်တဲ့ boot disk ရယ်၊ cloud-init disk ကိုပါတခါတည်း ပြင်ဆင်ပေးလိုက်ပါ။

```
# setup the system disk with required scsi parameters
$ qm set 1001 --scsihw virtio-scsi-pci --scsi0 local-lvm:vm-1001-disk-0

# setup the boot disk
$ qm set 1001 --boot c --bootdisk scsi0

# attach the cloudinit
$ qm set 1001 --ide2 local-lvm:cloudinit
```

Promox ရဲ့ web console မှာ out-of-band serial connection အတွက်လည်း အခုလိုမျိုး လိုအပ်တဲ့ parameter တွေကို သတ်မှတ်ပေးရပါလိမ့်မယ်။ ဒါမှမဟုတ်ရင်တော့ serial connection ကအလုပ် လုပ်မှာမဟုတ်ပါဘူး။

```
# setup the serial vga parameters for web console sessions
$ qm set 1001 --serial0 socket --vga serial0
```

အထက်မှာ virt-customize ကိုအသုံးပြီးတော့ install လုပ်ထားတဲ့ qemu-guest-agent ကိုလည်းအခုလို ကြိုတင်ပြီးတော့ enabled လုပ်ထားလို့ရပါတယ်။ Virtualbox မှာ additional guest agent ကိုသုံးသလိုပဲ၊ Promox မှာတော့ qemu-guest-agent ကိုသုံးပြီး VM ရဲ့ အချက်အလက်တွေနဲ့ feature တွေကို အသုံးပြုနိုင်ဖို့ ထည့်သွင်းပေးထားရပါတယ်။ နောက်မို့ဆိုရင် VM ရဲ့ IP Address ကိုတောင် Promox ရဲ့ dashboard မှာပြမှာမဟုတ်ပါဘူး။

```
# enable the qemu-guest-agent 
$ qm set 1001 --agent enabled=1
```

အကယ်လို့များ user account နောက်တခုပါ ဖန်တီးချင်ရင်ဖြင့် အောက်ကအတိုင်း လိုအပ်တဲ့ command ကို run လို့ရပါတယ်။ Security အတွက်တော့ password ကောင်းကောင်းသုံးဖို့လိုပါလိမ့်မယ်။

```
# create a login user
$ qm set 1001 --ciuser tyla

# set a password for the login user
$ qm set 1001 --cipassword "secret"
```

IP address ကို setup လုပ်တဲ့အခါ အသစ်သစ်သော VM တွေအတွက်တော့ DHCP နဲ့ဆိုပိုပြီး အဆင်ပြေနိုင်ပါတယ်။

```
# set the ipconfig to dhcp
$ qm set 1001 --ipconfig0 ip=dhcp
```

အားလုံးပြီးရင်တော့ ဒီ VM 1001 ကို template အဖြစ်သို့ ပြောင်းလဲလိုက်ရုံပါပဲ။ သတိထားရမှာက… template မပြောင်းခင်မှာ အဲ့ဒီ VM ကို boot မတက်ပါနဲ့၊ အကယ်လို့များ boot တက်လိုက်တယ်ဆိုရင်တော့ VM ကို အစကနေပြန်ပြီး create လုပ်ရပါလိမ့်မယ်။ Cloud-init clean နဲ့ reset လုပ်လို့ရသော်လည်း၊ troubleshoot လုပ်ရနိုင်ပါတယ်။ ဒီ့အတွက် VM အစကနေပြန်ပြီးတော့ ဖန်တီးတာပိုပြီးတော့ ကောင်းပါလိမ့်မယ်။

```
# convert the VM instance into a VM template
$ qm template 1001
```

VM template က အဆင်သင့်ဖြစ်ပြီဆိုရင်တော့ အောက်မှာပြထား တဲ့အတိုင်း VM နောက်အသစ်တစ်လုံးကို အဲ့ဒီ template ကနေပြီး clone ယူလိုက်ပါ။ ပြီးရင် VM ကိုလည်း တခါတည်း start လုပ်လိုက်ပါ။

```
# spin up a new VM instance with the VM template
$ qm clone 1001 100 --name ubuntu-srv01

# startup the VM
$ qm start 100
```

VM boot တက်လာပြီဆိုရင် Promox dashboard မှာပြထားတဲ့ VM ရဲ့ IP address နဲ့ ssh remote connection ကိုသုံးပြီး VM ထဲဝင်လို့ရပါပြီ။ Root account ကိုသုံးရင်တော့ ssh key authentication နဲ့ ဝင်နိုင်ပြီး၊ အသစ် create လုပ်ထားတဲ့ user account နဲ့ ဝင်ချင်ရင် အဲ့ဒီ username နဲ့ ကိုယ်သတ်မှတ်ပေးထားတဲ့ password ကိုသုံးကာ ssh login ဝင်လို့ရနိုင်ပါတယ်။ ကိုယ့်အတွက် အဲ့ဒီ VM မလိုတော့ဘူး၊ ပြန်ပြီးတော့ ဖျက်ချင်ရင် အောက်ကအတိုင်း ဖျက်ပစ်လို့ရပါတယ်။

```
# stop the VM and teardown
$ qm stop 100 && qm destroy 100
```

ရိုးရှင်းပြီးလွယ်သလောက် မစမ်းသပ်ဖူးရင် မသိနိုင်တဲ့ workflow process မို့အခုလိုမျိုး ပြန်လည်မျှဝေလိုက်ရခြင်းပဲဖြစ်ပါတယ်။ အားလုံးအတွက် အထောက်အကူပြုမယ်လို့ စာရေးသူ မျှော်လင့်ပါတယ်။
