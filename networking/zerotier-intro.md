---
cover: https://i.imgur.com/rc5t9J8.jpeg
coverY: 0
---

# ZeroTier မိတ်ဆက်

VPN တို့၊ MPLS တို့၊ Tunnelling တို့နဲ့ပတ်သတ်ရင် စာရေးသူ အတွက်စိတ်ဝင်စားစရာတစ်ခု လိုလိုဖြစ်နေတတ်ပါတယ်။ Networking ရဲ့ routing နဲ့ switching တို့မှာ basic နားလည်းထားဖို့လိုတာတွေရှိသလို၊ ကိုယ်နောက်ပိုင်း network ဆိုင်ရာ concept တစ်ခုကို သိလွယ်တတ်လွယ်ဖို့အတွက် အထောက်အကူ ပြုတတ်မြဲမို့ အခြေခံကောင်းနေဖို့လည်းလို ပါတယ်။ အခြေခံကိုမှ ကိုယ်ကနားမလည် ထားရင်အချို့သော နည်းပညာဆိုင်ရာမှာ လွယ်သလောက် နားလည်သလိုလို၊ နားမလည်သလိုလို ဖြစ်တတ်လို့ပါ။ စာရေးသူလည်း ဒီလိုမျိုး ဖြစ်တတ်လို့ သိနေခြင်းကြောင့်ပါ။ လက်တွေ့အတွေ့အကြုံ တွေတော်တော်များများမှာ စာရေးသူ အခြေခံမကောင်းလို့ အခြေခံကို ပြန်သွားပြီးတော့ အစကနေလေ့လာပြီးတော့မှ ကိုယ်လုပ်နေတဲ့ အရာတစ်ခုကို ပြန်လာရတာမျိုးလည်း ခဏခဏ ဖြစ်ဖူးပါတယ်။ တခါတလေလည်း အခြေခံများသွားလို့ ကိုယ်လုပ်နေတဲ့ အရာကိုတောင်မေ့သွားပြီးတော့ ကိုယ် သိသလိုလိုရှိပြီးသားဟာတွေကို အစကနေပြန်သွားရင်းနဲ့ ပျင်းလာပျင်းသွားတတ်တဲ့ ကိစ္စမျိုးလည်း ဖြစ်တတ်ပါတယ်။ ဒီ့အတွက်ကိုယ့်ဟာကို အခြေအနေကြည့်ပြီးတော့ ဘယ်လောက်တော့ဖြင့် အခြေခံအားဖြင့် သိသင့်ပြီးတော့၊ ဘယ်ဟာကိုတော့ဖြင့် နည်းနည်းပါးပါး နားလည်ရုံဖြင့် ကိုယ်လက်ရှိလေ့လာနေတဲ့ အရာအတွက် ခရီးပေါက်လောက်နိုင်တယ်ဆိုတာကို အတိုင်းအဆ အားဖြင့် ချိန်ဆနိုင်မှတော်ရုံကြပါတော့တယ်။ ဒီလိုဖြစ်တာမျိုးကိုတော့ အင်္ဂလိပ်လိုပြောတာတစ်ခုရှိပါတယ်။ ဘာလဲဆိုတော့… Yak Shaving လုပ်တယ်လို့ ဆိုပါတယ်။ အဓိပ္ပာယ်ကတော့ အရှေ့မှာ စာရးသူပြောသွားသလိုပဲ၊ ကိုယ်လုပ်နေတဲ့ဟာကတစ်ခု… အဲ့ဒီတစ်ခုအတွက် အခြားလိုအပ်တဲ့ဟာ တစ်ခုပြီးတော့ တစ်ခုလုပ်ရင် ကိုယ်လုပ်ရင်းဟာတွေကို မေ့သွားပြီးတော့ ခရီးမရောက်နိုင်တော့တဲ့ အနေအထားတစ်ခုကို ဆိုလိုချင်းဖြစ်ပါတယ်။ နည်းပညာအသစ်အသစ်တွေကို လေ့လာတဲ့ အခါမှာ ဒီသဘောတရားလေးတွေကို သိထားဖို့လိုပါတယ်။ ကိုယ်သိချင်လို့ ရှာပြီးတော့ ဖတ်လိုက်တဲ့ material တွေကလည်း marketing လုပ်ဖို့အတွက် လုပ်ထားတဲ့ video တွေ၊ info-graph တွေဖြစ်နေရင်ဖြင့် ဘာကိုမှ နားမလည်နိုင်တော့ပဲ နဲ့၊ ဟာ… ဒါတော့ဖြင့် ကိုယ့်အတွက် လုံးဝအသစ်ကြီးဖြစ်နေလို့ စိတ်ပျက်လက်ပျက် ဖြစ်တဲ့အခါမျိုးလည်း ကြုံရဖူးပါတယ်။ ဥပမာ… နောက်ပိုင်း SD-WAN product တွေနဲ့၊ SDN product တွေတော်တော်များများမှာ zero-trust network (ZTN) ဆိုပြီးတော့ marketing material တွေမှာ သုံးနေကြတော့၊ ဪ… concept အသစ်၊ implementation အသစ်ဆိုပြီးတော့ ထင်နိုင်စရာ ရှိပါတယ်။ အမှန်ကတော့… VPN ဆိုပြီးတော့ သုံးလည်းရသော်လည်း၊ marketing material မှာ အခေါ်အဝေါ်တစ်ခုကို refresh လုပ်လိုက်ခြင်းပါပဲ။ မည်သို့ပင်ဖြစ်စေ၊ trend အရကတော့ feature အချို့ကို အပေါ်ကနေထပ်ထည့်ပြီးတော့ နာမည်ပေးကင်ပွန်းတက်လိုက်ခြင်းသာ ဖြစ်တဲ့အတွက်၊ VPN ရဲ့ အခြေခံကိုနားလည်ရင် zero-trust network (ZTN) ရဲ့ သဘောကို နားလည်ရတာလွယ်တယ်။ WireGuard ကိုစာရေးသူ အနေနဲ့ သုံးလို့ရတဲ့ VPN setup တိုင်းမှာ မဖြစ်မနေ ကိုယ်တိုင် အသုံးပြုပြီးတော့၊ အခြားသူတွေကို လည်းလမ်းကြုံတိုင်း WireGuard ကိုသာ အသုံးပြုဖို့အတွက် တိုက်တွန်းလေ့ရှိတာလည်း နှစ်နှစ်ကျော်ကျော်၊ သုံနှစ်လောက်ရှိပါပြီ။ WireGuard အကြောင်းကိုရေးတဲ့ post မှာ စာရေးသူ mesh network ကို WireGuard နဲ့တည်ဆောက်နိုင်သလိုမျိုးပဲ၊ Slack ကနေ opensource လုပ်ပေးထားတဲ့ [Nebula](https://github.com/slackhq/nebula) ဆိုတဲ့ project တစ်ခုရှိပါတယ်။ WireGuard ရော၊ Nebula ရော နှစ်ခုလုံးမှာ setup လုပ်ရတာနဲ့၊ configure လုပ်ရတာတွေဟာ ထင်သလောက်တော့ မရိုးရှင်းလှပါ။ သို့သော်… အခြေခံ public key encryption နဲ့ networking အခြေခံကိုသိရင်တော့ လွယ်ကူသင့်သလောက်တော့ လွယ်ကူမယ်လို့ ထင်ပါတယ်။

ဒီ post မှာကတော့ စာရေးသူ [ZeroTier](https://www.zerotier.com/) ဆိုတဲ့ mesh network အကြောင်းကို မိတ်ဆက်ပေး လိုပါတယ်။ ZeroTier ကတော့ အထက်ကနှစ်ခုလောက်တော့ setup လုပ်ရတာမခက်ပါဘူး၊ လွယ်ကူပါတယ်။ အဓိက ကတော့ opensource project တစ်ခုဖြစ်ပြီးတော့၊ enterprise customer တွေအတွက်လည်း offering ကောင်းကောင်း ရှိတာမို့ စိတ်ကြိုက်တွေ့မိတာတော့ အမှန်ပါ။ အောက်မှာတော့ သူ့ရဲ့ free မှာသုံးလို့ရတဲ့ feature အကျဉ်းချုပ်နဲ့ professional တို့၊ Enterprise တို့မှာ ဘာတွေကွာခြားသွားသလဲဆိုတာကို ယှဉ်ကြည့်လို့ရအောင် ဖော်ပြပေးထားပါတယ်။ စာရေးသူအတွက်တော့… free မှာရနိုင်တဲ့ feature တွေ၊ limit တွေ နဲ့ကို တော်တော်လေး လုံလောက်နေပြီ ဖြစ်တဲ့အတွက် အဆင်ပြေနေပါတယ်။ များသောအားဖြင့် WireGuard ကို အဓိကသုံးဖြစ်ပြီးတော့၊ နောက်ဆုံး WireGuard အဆင်မပြေရင် သုံးလို့ရအောင်လို့ ZeroTier ကို Plan B အနေနဲ့ အသုံးပြုပါတယ်။

<figure><img src="https://i.imgur.com/ApCpzSG.png" alt=""><figcaption><p>ZeroTier Pricing</p></figcaption></figure>

အထက်မှာပြထားတဲ့ အတိုင်း တကိုယ်ရေသုံးမယ်ဆိုရင် admin တစ်ယောက်ပဲလိုနိုင်ပြီးတော့၊ ကိုယ့်အိမ်က environment ကို ဘယ်နေရာကနေမဆို access လုပ်နိုင်အောင်လို့ လုပ်ထားလို့ရပါတယ်။ ပြီးတော့ devices ပေါင်းအခု ၅၀လောက် ချိတ်ဆက်ပြီးတော့ အသုံးပြုနိုင်တာမို့ ကိုယ့်အိမ်က network နဲ့ချိတ်ဖို့အတွက်တော့လောက်မယ်လို့ထင်ပါတယ်။ တခါမှတော့ သတ်မှတ်ထားတဲ့ limit ကိုရောက်တာမရှိသေးလို့ ဘယ်လိုမျိုး သတ်မှတ်သလဲဆိုတော့ သေချာမသိပါဘူး။ WireGuard တို့၊ Nebula တို့နဲ့ မတူတာတစ်ခုက ZeroTier ကိုကိုယ့်ရဲ့ environment မှာ deploy လုပ်စရာမလို၊ configure လုပ်စရာမလိုတာပဲဖြစ်ပါတယ်။ ZeroTier မှာက web portal တစ်ခုကို [https://accounts.zerotier.com](https://accounts.zerotier.com/) မှာသွားရောက် account တစ်ခုဖွင့်လိုက်ရုံဖြင့် အားလုံးနီးပါး အဆင်သင့်ဖြစ်ပါပြီ။ ဒီတော့ ဘယ်လိုမျိုး စတင်အသုံးပြုနိုင်သလဲဆိုတာကို တချက်လောက်ကြည့်လိုက်ရအောင်။ Account ဖွင့်ပုံ အသေးစိတ်ကိုတော့ ဒီနေရာမှာ မရှင်းတော့ ပါဘူး။ အဲ့ဒီ account ရပြီဆိုတာနဲ့ network တစ်ခုဘယ်လိုတည်ဆောက်သလဲ၊ အဲ့ဒီ network ကိုဘယ်လိုချိတ်သလဲဆိုတာကို မတူတဲ့ cloud providers နှစ်ခုကိုအသုံးပြုပြီးတော့ VPS နှစ်လုံးကို ချိတ်ပြပါ့မယ်။ ပထမဆုံး အနေနဲ့ ZeroTier account နဲ့ သူ့ web portal ထဲကိုဝင်လိုက်တာနဲ့ အောက်ကအတိုင်းတွေ့ရမှာပါ။

<figure><img src="https://i.imgur.com/jShVd9A.png" alt=""><figcaption><p>ZeroTier Portal</p></figcaption></figure>

ရိုးရှင်းတဲ့ interface တစ်ခုဖြစ်ပြီးတော့ ရှင်းလင်းတဲ့ အဆင့်ဆင့်လုပ်ဆောင်ရမယ့် အရာတွေကိုပုံမှာအတိုင်းတွေ့ရမှာပါ။ ပြောထားတဲ့ အတိုင်း network တစ်ခုကိုတည်ဆောက်ကြည့်လိုက် ရအောင်။ “Create A Network” ဆိုတဲ့နေရာနှိပ်လိုက်ပါ။ ZeroTier ဟာ random ID တစ်ခုနဲ့ network name တစ်ခုကို တည်ဆောက်ပေးပါလိမ့်မယ်။ အောက်မှာတွေ့တဲ့ အတိုင်းမြင်ရပါလိမ့်မယ်။

<figure><img src="https://i.imgur.com/t091SLH.png" alt=""><figcaption><p>ZeroTier Networks</p></figcaption></figure>

ကိုယ့်အနေနဲ့ တစ်ခုထက်ပိုတဲ့ network တွေကိုတည်ဆောက်ခြင်းလည်း ရပါတယ်။ ပုံမှာမြင်တဲ့ အတိုင်း ကိုယ့်ရဲ့ network ကအဆင်သင့်ဖြစ်ပြီ ဆိုတာနဲ့ network ID ရဲ့ အပြာရောင် hyperlink လေးကို click လုပ်လိုက်ပါ။ ဒါဆိုရင်ဖြင့် အောက်ကအတိုင်း network နဲ့ဆိုင်တဲ့ အချက်အလက်တွေကို ရှိတဲ့ နေရာကိုခေါ်သွားပါလိမ့်မယ်။

<figure><img src="https://i.imgur.com/VcWZbaX.png" alt=""><figcaption><p>ZeroTier – Basic Settings</p></figcaption></figure>

ကိုယ်က network ရဲ့ နာမည်ကိုပြောင်းချင်တယ်၊ description ထည့်ချင်တယ်၊ private လုပ်မှာလား public လုပ်မှာလားကိုလည်း ရွေးချယ်နိုင်ပါတယ်။ အောက်ကို scroll down ဆက်လုပ်လိုက်တာနဲ့ အခုလိုမျိုး မြင်ရမှာဖြစ်ပါတယ်။

<figure><img src="https://i.imgur.com/BvLcwfv.png" alt=""><figcaption><p>ZeroTier – Advanced Settings</p></figcaption></figure>

အပေါ်မှာပြထားတဲ့ ပုံထဲကအတိုင်း ကိုယ်ကြိုက်တဲ့ subnet ကိုရွေးချယ်နိုင်ပြီးတော့ အခြားသော routing ဆိုင်ရာရွေးချယ်အချို့ကို ဆက်လက်ရွေးလို့ ရပါတယ်။ နောက်တဆင့်အနေနဲ့ network members တွေကို ဘယ်လိုမျိုးထည့်သလဲဆိုတာ တချက်လောက်ကြည့်လိုက်ရအောင်။

<figure><img src="https://i.imgur.com/WRozSCW.png" alt=""><figcaption><p>ZeroTier – Add members to a network</p></figcaption></figure>

Node ID ကို ZeroTier ရဲ့ network မှရိုက်ထည့်ပြီး ထည့်သွင်းနိုင်သလို၊ ကိုယ့်ရဲ့ ချိတ်ဆက်ချင်တဲ့ server တွေပေါ်မှာ ZeroTierOne application ကို install လုပ်ပြီးတော့ network member အနေနဲ့ ထည့်လို့ရပါတယ်။ ကိုယ်အဆင်ပြေသလိုထည့်လို့ရ နိုင်ပါတယ်။ VPS နှစ်ခုမှာ တစ်ခုက CentOS၊ နောက်တစ်ခုက Ubuntu ဖြစ်တဲ့အတွက် ZeroTier ရဲ့ [https://www.zerotier.com/download/](https://www.zerotier.com/download/) documentation ကအတိုင်း အောက်မှာပြထားတဲ့ command နဲ့ install လုပ်လို့ရပါတယ်။ https://install.zerotier.com/ ဆိုတဲ့ URL ကနေ file တစ်ခုကို curl နဲ့ download လုပ်ပြီးတော့ sudo bash အတွင်း script ကို run ဖို့အတွက် pipeline ကိုသုံးထားပါ။

```
curl -s https://install.zerotier.com | sudo bash
```

Download လုပ်လိုက်တဲ့ bash script ရဲ့ အသေးစိတ်ကို စိတ်ဝင်စားရင်တော့ အောက်မှာတွေ့ရတဲ့ အတိုင်းပါပဲ။

```
#!/bin/bash
<<ENDOFSIGSTART=
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

ENDOFSIGSTART=

export PATH=/bin:/usr/bin:/usr/local/bin:/sbin:/usr/sbin:/usr/local/sbin

#
# ZeroTier install script
#
# All this script does is determine your OS and/or distribution and then add the correct
# repository or download the correct package and install it. It then starts the service
# and prints your device's ZeroTier address.
#

# Base URL for download.zerotier.com tree; see https://github.com/zerotier/download.zerotier.com if you want to mirror.
# Some things want http, some https, so we must specify both. Must include trailing /
ZT_BASE_URL_HTTPS='https://download.zerotier.com/'
ZT_BASE_URL_HTTP='http://download.zerotier.com/'

echo
echo '*** ZeroTier One Quick Install for Unix-like Systems'
echo
echo '*** Tested distributions and architectures:'
echo '***   MacOS (10.7+) on x86_64 (just installs ZeroTier One.pkg)'
echo '***   Debian (7+) on x86_64, x86, arm, and arm64'
echo '***   RedHat/CentOS (6+) on x86_64 and x86'
echo '***   Fedora (16+) on x86_64 and x86'
echo '***   SuSE (12+) on x86_64 and x86'
echo '***   Mint (18+) on x86_64, x86, arm, and arm64'
echo
echo '*** Please report problems to contact@zerotier.com and we will try to fix.'
echo

SUDO=
if [ "$UID" != "0" ]; then
	if [ -e /usr/bin/sudo -o -e /bin/sudo ]; then
		SUDO=sudo
	else
		echo '*** This quick installer script requires root privileges.'
		exit 0
	fi
fi

# Detect MacOS and install .pkg file there
if [ -e /usr/bin/uname ]; then
	if [ "`/usr/bin/uname -s`" = "Darwin" ]; then
		echo '*** Detected MacOS / Darwin, downloading and installing Mac .pkg...'
		$SUDO rm -f "/tmp/ZeroTier One.pkg"
		curl -s ${ZT_BASE_URL_HTTPS}dist/ZeroTier%20One.pkg >"/tmp/ZeroTier One.pkg"
		$SUDO installer -pkg "/tmp/ZeroTier One.pkg" -target /

		echo
		echo '*** Waiting for identity generation...'

		while [ ! -f "/Library/Application Support/ZeroTier/One/identity.secret" ]; do
			sleep 1
		done

		echo
		echo "*** Success! You are connected to port `cat '/Library/Application Support/ZeroTier/One/identity.public' | cut -d : -f 1` of Earth's planetary smart switch."
		echo

		exit 0
	fi
fi

# Detect already-installed on Linux
if [ -f /usr/sbin/zerotier-one ]; then
	echo '*** ZeroTier One appears to already be installed.'
	exit 0
fi

rm -f /tmp/zt-gpg-key
echo '-----BEGIN PGP PUBLIC KEY BLOCK-----' >/tmp/zt-gpg-key
cat >>/tmp/zt-gpg-key << END_OF_KEY
Comment: GPGTools - https://gpgtools.org

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
=JgAv
END_OF_KEY
echo '-----END PGP PUBLIC KEY BLOCK-----' >>/tmp/zt-gpg-key

echo '*** Detecting Linux Distribution'
echo

if [ -f /etc/debian_version ]; then
	dvers=`cat /etc/debian_version | cut -d '.' -f 1 | cut -d '/' -f 1`
	$SUDO rm -f /tmp/zt-sources-list

	if [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F -i LinuxMint`" ]; then
		echo '*** Found Linux Mint (using Ubuntu Xenial packages), creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/xenial xenial main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F trusty`" ]; then
		echo '*** Found Ubuntu "trusty", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/trusty trusty main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F wily`" ]; then
		echo '*** Found Ubuntu "wily", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/wily wily main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F xenial`" ]; then
		echo '*** Found Ubuntu "xenial", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/xenial xenial main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F zesty`" ]; then
		echo '*** Found Ubuntu "zesty", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/zesty zesty main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F precise`" ]; then
		echo '*** Found Ubuntu "precise", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/precise precise main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F artful`" ]; then
		echo '*** Found Ubuntu "artful", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/artful artful main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F bionic`" ]; then
		echo '*** Found Ubuntu "bionic", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/bionic bionic main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F yakkety`" ]; then
		echo '*** Found Ubuntu "yakkety", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/yakkety yakkety main" >/tmp/zt-sources-list
	elif [ -f /etc/lsb-release -a -n "`cat /etc/lsb-release 2>/dev/null | grep -F disco`" ]; then
		echo '*** Found Ubuntu "disco", creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/disco disco main" >/tmp/zt-sources-list
	elif [ "$dvers" = "6" -o "$dvers" = "squeeze" ]; then
		echo '*** Found Debian "squeeze" (or similar), creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/squeeze squeeze main" >/tmp/zt-sources-list
	elif [ "$dvers" = "7" -o "$dvers" = "wheezy" ]; then
		echo '*** Found Debian "wheezy" (or similar), creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/wheezy wheezy main" >/tmp/zt-sources-list
	elif [ "$dvers" = "8" -o "$dvers" = "jessie" ]; then
		echo '*** Found Debian "jessie" (or similar), creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/jessie jessie main" >/tmp/zt-sources-list
	elif [ "$dvers" = "9" -o "$dvers" = "stretch" ]; then
		echo '*** Found Debian "stretch" (or similar), creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/stretch stretch main" >/tmp/zt-sources-list
	elif [ "$dvers" = "10" -o "$dvers" = "11" -o "$dvers" = "sid" -o "$dvers" = "buster" -o "$dvers" = "bullseye" -o "$dvers" = "parrot" ]; then
		echo '*** Found Debian "buster", or "sid" (or similar), creating /etc/apt/sources.list.d/zerotier.list'
		echo "deb ${ZT_BASE_URL_HTTP}debian/buster buster main" >/tmp/zt-sources-list
	else
		echo "*** FAILED: unrecognized or ancient distribution: $dvers"
		exit 1
	fi

	$SUDO mv -f /tmp/zt-sources-list /etc/apt/sources.list.d/zerotier.list
	$SUDO chown 0 /etc/apt/sources.list.d/zerotier.list
	$SUDO chgrp 0 /etc/apt/sources.list.d/zerotier.list
	$SUDO apt-key add /tmp/zt-gpg-key

	echo
	echo '*** Installing zerotier-one package...'

	# Pre-1.1.6 Debian package did not properly enumerate its files, causing
	# problems when we try to replace it. So just delete them to force.
	if [ -d /var/lib/zerotier-one ]; then
		$SUDO rm -f /etc/init.d/zerotier-one /etc/systemd/system/multi-user.target.wants/zerotier-one.service /var/lib/zerotier-one/zerotier-one /usr/local/bin/zerotier-cli /usr/bin/zerotier-cli /usr/local/bin/zero
	fi

	cat /dev/null | $SUDO apt-get update
	cat /dev/null | $SUDO apt-get install -y zerotier-one
elif [ -f /etc/SuSE-release -o -f /etc/suse-release -o -f /etc/SUSE-brand -o -f /etc/SuSE-brand -o -f /etc/suse-brand ]; then
	echo '*** Found SuSE, adding zypper YUM repo...'
	cat /dev/null | $SUDO zypper addrepo -t YUM -g ${ZT_BASE_URL_HTTP}redhat/el/7 zerotier
	cat /dev/null | $SUDO rpm --import /tmp/zt-gpg-key

	echo
	echo '*** Installing zeortier-one package...'

	cat /dev/null | $SUDO zypper install -y zerotier-one
elif [ -d /etc/yum.repos.d ]; then
	baseurl="${ZT_BASE_URL_HTTP}redhat/el/7"
	if [ -n "`cat /etc/redhat-release 2>/dev/null | grep -i fedora`" ]; then
		echo "*** Found Fedora, creating /etc/yum.repos.d/zerotier.repo"
		baseurl="${ZT_BASE_URL_HTTP}redhat/fc/22"
	elif [ -n "`cat /etc/redhat-release 2>/dev/null | grep -i centos`" -o -n "`cat /etc/redhat-release 2>/dev/null | grep -i enterprise`" ]; then
		echo "*** Found RHEL/CentOS, creating /etc/yum.repos.d/zerotier.repo"
		baseurl="${ZT_BASE_URL_HTTP}redhat/el/\$releasever"
	elif [ -n "`cat /etc/system-release 2>/dev/null | grep -i amazon`" ]; then
		echo "*** Found Amazon (CentOS/RHEL based), creating /etc/yum.repos.d/zerotier.repo"
		if [ -n "`cat /etc/system-release 2>/dev/null | grep -F 'Amazon Linux 2'`" ]; then
			baseurl="${ZT_BASE_URL_HTTP}redhat/el/7"
		else
			baseurl="${ZT_BASE_URL_HTTP}redhat/amzn1/2016.03"
		fi
	else
		echo "*** Found unknown yum-based repo, using el/7, creating /etc/yum.repos.d/zerotier.repo"
	fi

	$SUDO rpm --import /tmp/zt-gpg-key

	$SUDO rm -f /tmp/zerotier.repo
	echo '[zerotier]' >/tmp/zerotier.repo
	echo 'name=ZeroTier, Inc. RPM Release Repository' >>/tmp/zerotier.repo
	echo "baseurl=$baseurl" >>/tmp/zerotier.repo
	echo 'enabled=1' >>/tmp/zerotier.repo
	echo 'gpgcheck=1' >>/tmp/zerotier.repo

	$SUDO mv -f /tmp/zerotier.repo /etc/yum.repos.d/zerotier.repo
	$SUDO chown 0 /etc/yum.repos.d/zerotier.repo
	$SUDO chgrp 0 /etc/yum.repos.d/zerotier.repo

	echo
	echo '*** Installing zerotier-one package...'

	if [ -e /usr/bin/dnf ]; then
		cat /dev/null | $SUDO dnf install -y zerotier-one
	else
		cat /dev/null | $SUDO yum install -y zerotier-one
	fi
fi

$SUDO rm -f /tmp/zt-gpg-key

if [ ! -e /usr/sbin/zerotier-one ]; then
	echo
	echo '*** Package installation failed! Unfortunately there may not be a package'
	echo '*** for your architecture or distribution. For the source go to:'
	echo '*** https://github.com/zerotier/ZeroTierOne'
	echo
	exit 1
fi

echo
echo '*** Enabling and starting zerotier-one service...'

if [ -e /usr/bin/systemctl -o -e /usr/sbin/systemctl -o -e /sbin/systemctl -o -e /bin/systemctl ]; then
	$SUDO systemctl enable zerotier-one
	$SUDO systemctl start zerotier-one
	if [ "$?" != "0" ]; then
		echo
		echo '*** Package installed but cannot start service! You may be in a Docker'
		echo '*** container or using a non-standard init service.'
		echo
		exit 1
	fi
else
	if [ -e /sbin/update-rc.d -o -e /usr/sbin/update-rc.d -o -e /bin/update-rc.d -o -e /usr/bin/update-rc.d ]; then
		$SUDO update-rc.d zerotier-one defaults
	else
		$SUDO chkconfig zerotier-one on
	fi
	$SUDO /etc/init.d/zerotier-one start
fi

echo
echo '*** Waiting for identity generation...'

while [ ! -f /var/lib/zerotier-one/identity.secret ]; do
	sleep 1
done

echo
echo "*** Success! You are ZeroTier address [ `cat /var/lib/zerotier-one/identity.public | cut -d : -f 1` ]."
echo

exit 0
-----BEGIN PGP SIGNATURE-----

iQJJBAEBCAAzFiEEdKXpxFjhpDHx2lenFlcZiCPlKmEFAl1xWtcVHGNvbnRhY3RA
emVyb3RpZXIuY29tAAoJEBZXGYgj5SphwG0P/ivxhHR3pdh4JllFVUcw6JM0zbzQ
eeURN0edizgjXMSIW1OIJ2oDTnTHbc3nxYXurfM2DNakGW6xs0aHgPTvTziZj7XN
xu5AMMmigaqwbODLgtyy8aPOeDbwKRJCm9o/V1XZ+Cj8tTE6B/I2A+UA0eIit7ue
iNNbZjYiUavPJlrbqpwsm5wlDygGIM1K838HLd8EJtgay95A2UQET9ZYLVztNuUx
Ar6ppxDV/pSJo7IFd+012pC5RZUWFslDhATXTI+MEIE+qQRzjk5jDOVUEoKmY+0f
VNK6o/6wPbzmbb540RahmdW86PKcFcx2Qk+b0qK2QL9eHbrAo8QfukVOQOfSMGzw
etnXVP0ugYxcs76CmjjuGB0dXn+5NAeOAj4RbmXw5ImsH5jCWrqvNgirMs86PAiS
QZt2N27LocNkzvVMfRp8NQnr/u+K2ieVUzxyhVZh0pVQhaghcxJFPTy0QHjM8+Rx
6dCXcpA2jmxiLFecYhs3FbwvmDxIKd5vW30fVHgwBObyl0/8udd7xjledNoZ6U7N
GAbbrLAeeqDOTaFH4cGtLpG3i4A2aNF1Y/6BMFcRiCjd2i7IKSx7hfUmELAHCdkO
lY3ziuqG8d68Qi8Cs8tDQNWFGlzzCNGtg/GVz69C86walkQQhdW/g4jTaPyh0yca
wcrBUY3kl8s0/g7x
=uxUj
-----END PGP SIGNATURE-----
```

ပုံမှန်အားဖြင့်တော့ Linux user တစ်ယောက်အနေနဲ့ curl လို command မျိုးနဲ့ Internet ပေါ်မှာတွေ့ကရာ link ကနေရတဲ့ ဘယ်လို script မျိုးကို မဆို sudo နဲ့ တွဲပြီးတော့ execute မလုပ်သင့်ပါဘူး။ (စာရေးသူက VPS အသစ်နှစ်ခုကို လတ်လတ်ဆက်ဆက် deploy လုပ်ပြီးတော့ အလွယ်သဘောမျိုးနဲ့ root account ပဲသုံးထားတဲ့အတွက် sudo မပါလည်း သက်ရောက်မူက အတူတူပါပဲ။) ကိုယ် download လုပ်မယ့် script ရဲ့ content ကို အနည်းငယ်လေ့လာပြီးတော့၊ သုံးသပ်ပြီးတော့မှ အခုလိုမျိုး curl ကို sudo bash နဲ့ တွဲပြီးတော့ အသုံးပြုသင့်ပါတယ်။ အကယ်လို့များ script ဟာ malicious code တွေဖြစ်နေရင် ကိုယ်ရဲ့ system တစ်ခုလုံးကို ဆုံးရှုံးနိုင်ပါတယ်။ အဲ့ဒီအတွက်သတိနဲ့ ကပ်ပြီးတော့ အသုံးပြုသင့်ပါတယ်။ CentOS နဲ့ Ubuntu system နှစ်ခုလုံးမှာ install လုပ်ပြီးရင်တော့ အောက်ကအတိုင်းတွေ့ရမှာဖြစ်ပါတယ်။ အပေါ်ကတစ်ခုမှာ CentOS 8 Stream ကိုတင်ထားပြီးတော့၊ အောက်ကတစ်ခုမှာတော့ Ubuntu 20.10 ကိုတင်ထားတာဖြစ်တဲ့အတွက် အခုလိုမျိုးတွေ့မြင်ရတာပဲဖြစ်ပါတယ်။

<figure><img src="https://i.imgur.com/4Q9pZeR.png" alt=""><figcaption><p>ZeroTier – Installation</p></figcaption></figure>

VPS နှစ်ခုလုံးပေါ်မှာ ZeroTier ကို install လုပ်ပြီးတဲ့နောက်မှာတော့၊ ကိုယ့်ရဲ့ network ကိုအောက်ကအတိုင်း join လိုက်ရုံပါပဲ။ ကိုယ်က root account နဲ့ run တာမဟုတ်ရင်တော့ sudo ထည့်စရာလိုပါတယ်။

```
sudo zerotier-cli join 885033839017a5c3
```

အားလုံးအဆင်ပြေရင် ကိုယ်ရဲ့ node ဘက်မှာ အောက်ကအတိုင်း တွေ့ရမှာဖြစ်ပါတယ်။

<figure><img src="https://i.imgur.com/9Na25sE.png" alt=""><figcaption><p>zerotier-cli join</p></figcaption></figure>

ZeroTier portal ဘက်မှာတော့ အောက်မှာလိုမျိုးတွေ့ရပါလိမ့်မယ်။ အပေါ်တစ်ခုက Tokyo မှာ deploy လုပ်ထားတဲ့ CentOS 8 Stream VPS (IP: 45.32.51.8) ဖြစ်ပြီးတော့၊ အောက်ကတစ်ခုကတော့ Sydney မှာ deploy လုပ်ထားတဲ့ Ubuntu 20.10 VPS (IP: 108.61.185.145) တို့ပဲဖြစ်ပါတယ်။ ကိုယ်က node တစ်ခုချင်းစီရဲ့ short name နဲ့ description ကိုထည့်ထားချင်ရင်လည်း ဒီ interface မှာထည့်လို့ ရနိုင်ပါတယ်။

<figure><img src="https://i.imgur.com/K6n9kJ8.png" alt=""><figcaption><p>ZeroTier – Members</p></figcaption></figure>

Network တစ်ခုမှာ member တွေကိုထည့်သွင်းလိုက်ရုံနဲ့ ချက်ချင်း ချိတ်ဆက်ပြီးသား မဖြစ်သေးပါဘူး။ Auth? ဆိုတဲ့ column ကို tick လုပ်လိုက်မှ နောက်ဆုံးအဆင့် authentication လုပ်တဲ့စီကိုရောက်ပါတော့တယ်။ အောက်မှာတော့ Auth? ကို tick လုပ်ပြီးသွားရင်မြင်ရတဲ့ အနေအထားကို ပြထားပေးပါတယ်။

<figure><img src="https://i.imgur.com/oMuNweU.png" alt=""><figcaption><p>After Auth? ticked</p></figcaption></figure>

<figure><img src="https://i.imgur.com/dsx9Dwy.png" alt=""><figcaption><p>ZeroTier client NIC config</p></figcaption></figure>

အခုဆိုရင်တော့… mesh network တစ်ခုရဲ့ အခြေခံကို စတင်ပြီးတော့ သုံးနိုင်နေပါပြီ။ ကိုယ်လိုချင်တဲ့ routing နဲ့ network တွေကို ချိတ်ဆက်လိုက ချိတ်ဆက်နိုင်ပါပြီ။ ဘာ VPN server တစ်ခုကို အိမ်မှာ setup လုပ်စရာမလိုပဲနဲ့ အခုလိုမျိုး mesh network တစ်ခုကို အလွယ်တကူ တည်ဆောက်ခြင်းဖြင့် ကိုယ့်အိမ်က network ဟာ double-NAT သို့မဟုတ် Carrier-Grade NAT (CGN) နောက်မှာပဲရောက်နေပါစေ၊ ရှိသမျှ NAT တွေကို အတွင်းထဲကနေပြန်ပြီးတော့ punch-back လုပ်တာဖြစ်တဲ့အတွက် ကိုယ့်အိမ်က network ကို port-forwarding လုပ်ပြီး internet ပေါ်မှာ ဘယ်လို port မျိုးကိုမှ expose လုပ်စရာမလိုတော့ပါဘူး။ မဖြစ်မနေသုံးဖို့အတွက်တော့ လုံးဝကိုအဆင်ပြေတဲ့ နည်းလမ်းတစ်ခုမို့ ပြန်လည် ဝေမျှလိုခြင်းဖြစ်ပါတယ်။ Backend မှာတော့ တော်တော်လေးကို ရှုပ်ထွေးလှတဲ့ overlay network virtualisation ကိုသုံးထားတာဖြစ်ပြီးတော့၊ အသေးစိတ်ကိုသိချင်ရင် ဒီ [link](https://www.zerotier.com/manual/) မှာသွားဖတ်လို့ရပါတယ်။ စာရေးသူ အစမှာပျိုးခဲ့သလိုမျိုးပဲ backend မှာသုံးထားတဲ့ နည်းပညာအကုန်လုံး သိစရာမလိုပဲနဲ့ mesh network တစ်ခုကို အလွယ်တကူ deploy လုပ်နိုင်တဲ့ အနေအထားမျိုးမို့၊ အချို့သော VPN နဲ့ routing အခြေခံလောက်ကိုတော့ ကိုယ်သိထားရပါလိမ့်မယ်။ Performance မှာတော့ WireGuard လောက်မကောင်းတာကို ကိုယ်တွေ့ကြုံရလို့ သတိတော့ပေးချင်ပါတယ်။ သို့သော်… Out-Of-Band (OOB) network management အတွက်ဆိုရင်တော့ Raspberry PI လိုမျိုး SoC device လေးတွေနဲ့ တွဲပြီးတော့ ZeroTier ကိုသုံးချင်ရင်တော့ လုံဝ valid ဖြစ်တဲ့ use case တစ်ခုပါ။ အခြားသော ကိုယ်သုံးချင်တဲ့ low bandwidth လိုအပ်မျိုးပဲ လိုအပ်တဲ့ project တွေအတွက်လည်း အသုံးပြုနိုင်ပါတယ်။ စိတ်ဝင်စားပြီး အသုံးတည့် မယ်လို့ မျှော်လင့်ပါတယ်။ ဒီ post ကိုဒီလောက်နဲ့ပဲ ရပ်လိုက်ပါတော့မယ်။
