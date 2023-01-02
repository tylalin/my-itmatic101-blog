---
cover: ../.gitbook/assets/pexels-photo-171198.jpeg
coverY: 0
---

# Bash နဲ့ Network Configuration Management system တစ်ခုတည်ဆောက်ပုံ – အပိုင်း(၂)

အရှေ့မှာတော့ bash programming ကိုအသုံးပြုပြီးတော့ ကိုယ် backup လုပ်ထားတဲ့ network configuration files တွေ up-to-date ဖြစ်မဖြစ် စစ်ကြည့်ဖို့အတွက် ညတိုင်း crontab နဲ့ run လို့ရတဲ့ bash script တစ်ခုကိုတည်ဆောက်ပြထားပါတယ်။ ပထမဆုံး မျက်လုံးထဲမြင်အောင် script ကို serial / sequential ပုံစံမျိုးနဲ့ ရေးထားပြီးတော့၊ ဒုတိယတခုမှာတော့ compact ဖြစ်အောင် ဘယ်လိုလုပ်လို့ရသလဲဆိုတာကို function သုံးပြီးတော့ တူတဲ့ code တွေကို ထပ်ခါထပ်ခါ loop နဲ့ပတ်ပြီးတော့ အကြိမ်ကြိမ် run လို့ရအောင် optimise လုပ်ကြည့်ပါတယ်။ အမြင်အားဖြင့် line အရေအတွက် နည်းသွားတဲ့အပြင် runtime မှာလည်း ပိုပြီးတော့ တွင်ကျယ်လာတာကို တွေ့နိုင်မှာပါ။ ဒီ post မှာတော့ အရှေ့မှာပြောထားတဲအတိုင်း configuration change management ပုံစံတစ်ခုရအောင်လို့ bash ကိုပဲအသုံးပြုပြီးတော့ ဘယ်နေ့မှာဘယ်သူက ဘယ် network device ပေါ်မှာ configuration သွားပြောင်းသလဲဆိုတာသိနိုင်အောင်လို့ bash နဲ့ ညတိုင်းသွားကြည့်ပြီး ကိုယ့်ကို email ကနေတဆင့် အသိပေးနိုင်အောင်ဖို့အတွက်လုပ်တဲ့ workflow တစ်ခုပါ။ ထို email နဲ့အတူ ကိုယ့်ရဲ့ configuration file ကို before နဲ့ after ပြောင်းလဲသွားတဲ့ပုံစံကိုကြည့်ဖို့အတွက် config file ကိုပါ attachment အနေနဲ့ တွဲပြီးတော့ ထည့်ပေးလိုပါတယ်။ ပြဿနာက email ဟာ သူ့တစ်ခုတည်းအသုံးပြုရင် plaintext နဲ့ message ရော၊ attachment files တွေကို အရှိအတိုင်းပဲပို့ပါတယ်။ ကိုယ့်ရဲ့ network config file မှာအရေးကြီးတဲ့ အချက်အလက်တွေ ပါဝင်တာမို့ ဒီအတိုင်း ပို့မယ်ဆို မလုံခြုံနိုင်ပါ။ ဒီ့အတွက် စာရေးသူ public key encryption ဖြစ်တဲ့ GPG ကိုအသုံးပြုထားပါတယ်။ GPG key ကိုတော့ကိုယ်ကြိုက်သလို management လုပ်နိုင်ပြီးတော့၊ key management system တစ်ခုကိုအသုံးပြုပြီးတော့ အခြားသောကိုယ့်ရဲ့ team နဲ့ key ကို distribute လုပ်နိုင်ပါတယ်။ ကိုယ်သတိထားရမှာက ဘယ် private key ကိုမှ email တို့ messaging တို့ကနေ မ share ရပါ။ ဒီ private / public keys တွေကို management လုပ်တဲ့ topic ဟာ အခြားသော ဆွေးနွေးနိုင်တဲ့ subject တစ်ခုဖြစ်တဲ့အတွက် နောက်မှရေးဖို့အတွက် ချန်ထားလိုက်ပါတော့မယ်။ ဒီ post မှာ GPG key pair ကို issue လုပ်တဲ့ပုံစံ၊ public key ကို import / export လုပ်တဲ့ပုံစံ နဲ့ gpg ရဲ့ CLI commands အချို့ကဖော်ပြပေးသွားပါ့မယ်။ အရင်ဆုံးအနေနဲ့ bash script ကိုကြည့်လိုက်အောင်။

```
#!/bin/bash

td=$(date +%Y%m%d) 
chg="false"

# diff report function to repeat the same task for device type
diff_report() 
{
    vendor=$1
    cd /config/$vendor
    while d= read -r line
    do
        last=$(ls -t1 | grep $line | head -1)
        if [ -f "$last" ]; then
            if [ $vendor == huawei ]; then
                unzip -q $last -d /scripts/temp
                mv /scripts/temp/vrpcfg.cfg /scripts/temp/$line
            else
                cp $last /scripts/temp/$line
            fi

            if [ ! -f /scripts/baseline/$line ]; then
                cp /scripts/temp/$line /scripts/baseline/$line
            else
                if [ $vendor == mikrotik ]; then
                    diff -u <(tail -n +2 /scripts/baseline/$line) <(tail -n +2 $last) 1>/dev/null
                else
                    diff -u /scripts/baseline/$line /scripts/temp/$line 1>/dev/null
                fi     
                
                if [ ! $? == "0" ]; then
                    cp /scripts/baseline/$line /scripts/temp/$line-$td-before
                    cd /scripts/temp/
                    gpg --yes --always-trust -e -r "itmatic101" $line-$td-before
                    zip -q /diff_reports/changelog_$td.zip $line-$td-before.gpg; cd - 1> /dev/null;
                    echo -e "\n$line changelog:" &>> /diff_reports/changelog_$td.log
                    echo "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" &>> /diff_reports/changelog_$td.log
                    
                    if [ $vendor == mikrotik ]; then
                        diff -u <(tail -n +2 /scripts/baseline/$line) <(tail -n +2 $last) &>> /diff_reports/changelog_$td.log
                    else    
                        diff -u /scripts/baseline/$line /scripts/temp/$line &>> /diff_reports/changelog_$td.log
                    fi
                    
                    echo -e "\n###############################################################" &>> /scripts/diff_reports/changelog_$td.log
                    cp /scripts/temp/$line /scripts/baseline/$line
                    cp /scripts/baseline/$line /scripts/temp/$line-$td-after
                    cd /scripts/temp/
                    gpg --yes --always-trust -e -r "itmatic101" $line-$td-after
                    zip -q /diff_reports/changelog_$td.zip $line-$td-after.gpg; cd - 1> /dev/null;
                    chg="true"
                fi
            fi
        fi
    done < /scripts/inventory/$vendor
}

for arg in cisco hpe fortigate huawei mikrotik
do
    diff_report $arg
done

if [ "$chg" == true ]; then
    cd /diff_reports/
    gpg --yes --always-trust -e -r "itmatic101" changelog_$td.log
    zip -q changelog_$td.zip changelog_$td.log.gpg
    echo "Config Changelog for $td" | mailx -s "Config Changelog Report $td" -a "/diff_reports/changelog_$td.zip" tyla@itmatic101.com

    # replicate the baseline to latest in config
    rsync -azh /scripts/baseline/ /config/latest/

    # git auto version control on /config/latest/
    cd /config/latest/
    git add *
    git commit -am "auto commit for $td"
    git push origin master
fi      

# cleanup unnecessary files 
rm /scripts/temp/* 2> /dev/null
rm /diff_reports/*.zip 2> /dev/null
rm /diff_reports/*.gpg 2> /dev/null
```

ဒီ script မှာတော့ function ကို အသုံးပြုပြီးတော့ argument ကိုတစ်ခုပြီးတော့ တစ်ခုထည့်ပြီးတော့ loop ထဲမှာပတ်ပြီးတော့ automate လုပ်တဲ့ပုံစံမျိုးနဲ့ပဲ တိုက်ရိုက်ရှင်းလိုက်ပါတော့မယ်။ တပိုင်းပြီး တပိုင်းသွားလိုက်ရအောင်။ ပထမဆုံး အပိုင်းဖြစ်တဲ့ variable နှစ်ခုကို ထိပ်မှာအရင်ဆုံး ဖန်တီးလိုက်ပါတယ်။ ပထမဆုံး တစ်ခုက td ဆိုတဲ့ လက်ရှိနေ့စွဲကို စာရေးသူ နှစ်သက်တဲ့ format နဲ့ ပြောင်းပြီးတော့ ယူလိုက်တာဖြစ်ပြီးတော့။ ဒုတိယတစ်ခုက chg ဆိုတဲ့ boolean ကို false နဲ့ စလိုက်ပါတယ်။ change ရှိလား မရှိဘူးလားကို သိနိုင်အောင်လို့ chg ဆိုတဲ့ boolean flag ကိုအသုံးပြုလိုက်ခြင်းဖြစ်ပါတယ်။

```
td=$(date +%Y%m%d) 
chg="false"
```

ပြီးတာနဲ့ diff\_report() ဆိုတဲ့ function တစ်ခုကို စတင်တည်ဆောက်လိုက်ပါတယ်။ အဲ့ဒီ function ရဲ့ စစချင်းမှာပဲ vendor ဆိုတဲ့ variable ကိုစလိုက်ပြီးတော့ $1 ဆိုတဲ့ syntax ကတော့ ကိုယ် for loop ကနေ pass လုပ်လိုက်တဲ့ argument value ကို ချက်ချင်း assign လုပ်လိုက်ပါတယ်။ ပြီးရင် “cd /config/$vendor” ဆိုပြီးတော့ vendor တစ်ခုချင်းစီရဲ့ folder တွေစီကို သွားလိုက်တယ်။ ဒီနေရာမှာ vendor ဆိုတဲ့ variable ကို မသုံးပဲနဲ့ $1 ကိုပဲ တိုက်ရိုက် function ထဲမှာအသုံးပြုလို့ရပါတယ်။ စာရေးသူကတော့ readability အတွက် vendor ဆိုတဲ့ variable ကိုအပိုထည့်ပြီးတော့ သုံးထားတာဖြစ်ပါတယ်။ အောက်မှာ code တွေထပ်တိုးလာတဲ့အခါမှာ vendor ဆိုတဲ့ variable ကို ရှင်းရှင်းလင်းလင်း မြင်နိုင်တာမို့ နောက်တချိန်ပြန် ကြည့်တဲ့အခါ နားလည်ရပိုလွယ်မယ်လို့ထင်ပါတယ်။

```
vendor=$1
cd /config/$vendor
```

နောက်တစ်ခုက while loop နဲ့ folder တစ်ခုချင်းစီမှာရှိတဲ့ file နာမည်တွေကို တစ်ခုပြီးတစ်ခု လိုက်ဖတ်လိုက်ပါတယ်။ သူ့ရဲ့ syntax ကတော့ အောက်မှာပြထားတဲ့ အတိုင်းဖြစ်ပါတယ်။ နာမည်ကို match လုပ်ဖို့အတွက် “/scripts/inventory/$vendor” ဆိုတဲ့ inventory နာမည်စာရင်းဖြစ်တဲ့ flat file တစ်ခုကို input အနေနဲ့ထည့်ပြီးတော့ ရှာကြည့်လိုက်ပါတယ်။

```
while d= read -r line
    do
         // Block of codes // 
    done < /scripts/inventory/$vendor
```

ဒီနေရာမှာ ပြဿနာတစ်ခုက vendor တစ်ခုနဲ့တစ်ခု ကနေထွက်လာတဲ့ configuration file ရဲ့ output format ကမတူကြပါဘူး။ ဥပမာ…. Huawei ရဲ့ config file ရဲ့ output ဟာ vrpcfg.cfg ဆိုတဲ့ file ကို device name နဲ့ zip လုပ်ထားတဲ့အတွက် အနည်းငယ် housekeeping လုပ်ဖို့လိုပြန်ပါတယ်။ ဒီအတွက် vendor ဟာ Huawei ဟုတ်သလား မဟုတ်ဘူးလားကို if else နဲ့ စစ်ကြည့်ပါတယ်။ အကယ်လို့ ဟုတ်ခဲ့ရင် unzip လုပ်ရမယ်၊ file name ကိုပြောင်းမယ်ဆိုပြီးတော့ ပြောလိုက်ပါတယ်။ မဟုတ်ဘူးဆိုရင်တော့… file ကို ဒီအတိုင်း copy လုပ်ပြီးတော့ destination path မှာနာမည်ပြောင်းမယ်လို့ ပြောလိုက်ခြင်းပဲဖြစ်ပါတယ်။ ဒါ့အပြင် အပေါ်ဆုံး line ကတော့ folder ထဲမှာရှိတဲ့ file name နဲ့ inventory ထဲက ကိုယ့်ရဲ့ device name ကို ls command နဲ့ grep လုပ်လိုက်တာပါ။ ပြီးတာနဲ့ နောက်ဆုံး update လုပ်ထားတဲ့ file ကို ရှာပြီးယူလိုက်တာပါ။ ရှင်းပါတယ်။ အရမ်းနားလည်ရ မခက်ပါဘူး။

```
last=$(ls -t1 | grep $line | head -1)
if [ -f "$last" ]; then
    if [ $vendor == huawei ]; then
         unzip -q $last -d /scripts/temp
         mv /scripts/temp/vrpcfg.cfg /scripts/temp/$line
    else
         cp $last /scripts/temp/$line
    fi
```

နောက်တပိုင်းက baseline ရှိပြီးသား ဆိုရင် အဲ့ဒီ baseline ကိုလက်ရှိဖတ်ယူထားတဲ့ file နဲ့ အစားထိုးလိုက်မယ်လို့ ဆိုထားပြီးတော့၊ မရှိသေးရင်တော့ baseline အသစ်တစ်ခုဖန်တီး မယ်လို့ ပြောထားပါတယ်။ နောက်တစ်ခု သတိထားရမှာက baseline မရှိသေးလို့ baseline အသစ်ဖန်တီးတဲ့အခါမှာ baseline comparison လုပ်စရာမလိုတဲ့အတွက် change တစ်ခုအနေနဲ့ မသတ်မှတ်ပါဘူး။ Baseline ကပြောင်းသွားမှသာ သတ်မှတ်လိုခြင်း ဖြစ်တဲ့အတွက် အခုလိုမျိုး တကူးတက code ကို နေရာချထားခြင်းဖြစ်ပါတယ်။ ပြီးတော့… နောက်အခက်အခဲတစ်ခုက MikroTik တွေရဲ့ backup config မှာ ပထမဆုံးတစ်ကြောင်းမှာ နေ့စွဲ ပါတာမို့၊ အဲ့ဒီတစ်ကြောင်းကို ကျော်သွားဖို့ကို ထပ်ပြီးတော့ စီစဉ်ကပါတယ်။ အခုဆိုရင် baseline နဲ့ ကိုယ်နောက်ဆုံး ဆွဲယူလာတဲ့ file နှစ်ခုကို diff -u နဲ့ အလွယ်တကူ နှိုင်းယှဉ်နိုင်ပါပြီ။

```
if [ ! -f /scripts/baseline/$line ]; then
    cp /scripts/temp/$line /scripts/baseline/$line
else
    if [ $vendor == mikrotik ]; then
        diff -u <(tail -n +2 /scripts/baseline/$line) <(tail -n +2 $last) 1>/dev/null
    else
        diff -u /scripts/baseline/$line /scripts/temp/$line 1>/dev/null
    fi    
```

အခုလိုမျိုး file နှစ်ခုကို နှိုင်းယှဉ်တဲ့ အခါမှာ တူလားမတူဘူးလားဆိုတာကို အရင်သိဖို့လိုပါတယ်။ “diff -u /scripts/baseline/$line /scripts/temp/$line 1>/dev/null” ရဲ့ std output ကို “0” လား “1” ဆိုပြီးတော့ စစ်လိုက်ပါတယ်။ “0” ဆိုရင် နှစ်ခုကတူညီပြီးတော့ အပြောင်းအလဲမရှိပါဘူး။ ဒါဆိုရင် ဘာမှဆက်ပြီးတော့ လုပ်စရာမလိုတော့ပါဘူး။ ဒါမှမဟုတ်ဘူး “1” ဖြစ်ခဲ့ရင်တော့ ဒီ file နှစ်ခုဟာ မတူဘူးလို့ သိနိုင်ပါတယ်။ ဒါဆိုရင် ဘယ်နေရာမှာ မတူဘူးဆိုတာကို သိဖို့လိုပါပြီ၊ အဲ့ဒီအတွက် အောက်ကအတိုင်း သိချင်တဲ့ဟာကို ရှာထုတ်လိုက်ပြီးတော့ လက်ရှိ baseline ကို before the change လို့မှတ်လိုက်ပြီးတော့ temp folder ထဲမှာသွားသိမ်းလိုက်ပါတယ်။ ပြီးတော့ gpg နဲ့ encrypt လုပ်လိုက်ပါတယ်။ နောက်ပြီးတော့ zip လုပ်ပြီးတော့ သွားသိမ်းလိုက်ပါတယ်။

```
if [ ! $? == "0" ]; then
    cp /scripts/baseline/$line /scripts/temp/$line-$td-before
    cd /scripts/temp/
    gpg --yes --always-trust -e -r "itmatic101" $line-$td-before
    zip -q /diff_reports/changelog_$td.zip $line-$td-before.gpg; cd - 1> /dev/null;
```

နောက်တဆင့်ဖြစ်တဲ့ diff ရဲ့ output ကိုလည်း စာရေးသူက changelog ဆိုတဲ့ log file မှာသွားတော့ တစ်ခုချင်းစီ သွားထည့်လိုက်ချင်ပါတယ်။ အဲ့ဒီအတွက် diff -u ကို နောက်တစ်ခါထပ်ပြီးတော့ run ရပြန်ပါတယ်။

```
echo -e "\n$line changelog:" &>> /diff_reports/changelog_$td.log
echo "~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~" &>> /diff_reports/changelog_$td.log
if [ $vendor == mikrotik ]; then
     diff -u <(tail -n +2 /scripts/baseline/$line) <(tail -n +2 $last) &>> /diff_reports/changelog_$td.log
else    
     diff -u /scripts/baseline/$line /scripts/temp/$line &>> /diff_reports/changelog_$td.log
fi
echo -e "\n###############################################################" &>> /scripts/diff_reports/changelog_$td.log
```

နောက်တခါ… after the change ဆိုပြီးတော့ ပြောင်းလဲသွားပြီးတဲ့အခါမှာ ဘယ်လိုမျိုး config ဖြစ်သွားသလဲဆိုတာကိုလည်း သိချင်တဲ့အတွက် အောက်အတိုင်း နောက်တစ်ခါ copy လုပ်၊ overwrite လုပ်ပြီးသား file ကိုထပ်တခါရှာလိုက်ပြီးတော့ gpg နဲ့ encrypt လုပ်ပါတယ်၊ နောက်ပြီး zip file ထဲကို ထပ်တခါပေါင်းထည့်လိုက်ပြန်ပါတယ်။ နောက်ဆုံးမှာတော့ change ဖြစ်သွားကြောင်း ကိုသိဖို့အတွက် အသုံးပြုထားတဲ့ chg ကို “true” ဆိုပြီးတော့ assign လုပ်လိုက်ပါတယ်။ ဒီမှာတင် diff\_report() ရဲ့ function ကိစ္စကပြီးသွားပါတယ်။

```
cp /scripts/temp/$line /scripts/baseline/$line
cp /scripts/baseline/$line /scripts/temp/$line-$td-after
cd /scripts/temp/
gpg --yes --always-trust -e -r "itmatic101" $line-$td-after
zip -q /diff_reports/changelog_$td.zip $line-$td-after.gpg; cd - 1> /dev/null;
chg="true"
```

အခုဆိုရင်အဆင်သင့် အသုံးပြုဖို့အတွက် diff\_report() ကရပါပြီ၊ သူ့ကို for loop ထဲထည့်ပြီးတော့ argument ကို တစ်ခုချင်းစီ ဘယ်လိုလုပ်သလဲဆိုတာကြည့်လိုက်ရအောင်။ ရိုးရှင်းသလောက် အမြင်ရှင်းတဲ့ reusable code ကို အောက်ကအတိုင်းမြင်တွေ့နိုင်မှာဖြစ်ပါတယ်။

```
for arg in cisco hpe fortigate huawei mikrotik
do
    diff_report $arg
done
```

အားလုံးအဆင်သင့်ဖြစ်တဲ့နောက်မှာတော့… ထုပ်ပိုးပြီးတော့ email နဲ့ပို့ဖို့အတွက်အောက်ကအတိုင်း code block တစ်ခုကို ထပ်ပြီးတော့ ပေါင်းထည့်လိုက်ပါတယ်။ GPG ကိုဘယ်လို အသုံးပြုသလဲဆိုတာကို သိချင်တော့ ဒီ [link](https://tutes.itmatic101.com/linux/gpg) မှာသွားပြီးတော့ quick snippet မှာသွားကြည့်နိုင်ပါတယ်။ အသေးစိတ်မဟုတ်ပေမယ့် နားလည်ရလွယ်မယ်လို့ ထင်ပါတယ်။ ဒါ့အပြင် အသုံးပြုထားတဲ့ script တွေကို တစ်စုတည်းကြည့်ချင်ရင်တော့ GitHub ရဲ့ ဒီ [link](https://github.com/tylalin/ITmatic101/tree/master/network\_config\_mgmt) မှာသွားပြီးတော့ကြည့်လို့ရပါတယ်။ ဒါ့အပြင် စာရေးသူ တကိုယ်ရေး အသုံးပြုဖို့အတွက် docker နဲ့ self-hosted လုပ်ထားတဲ့ Gitea server ပေါ်မှာလည်း သီးသန့် version control လုပ်ချင်တဲ့အတွက် အောက်ကအတိုင်း code ကိုထပ်ဖြည့်လိုက်ပါတယ်။ Bash programming/script ကို အသုံးပြုခြင်းအားဖြင့် terminal မှာကိုယ်သုံးနေကြ native commands တွေကိုအခုလိုမျိုး ပစ်ထည့်ပြီးတော့ အသုံးပြုနိုင်တာကိုလည်း သတိထားမိစေချင်ပါတယ်။

```
if [ "$chg" == true ]; then
    cd /diff_reports/
    gpg --yes --always-trust -e -r "itmatic101" changelog_$td.log
    zip -q changelog_$td.zip changelog_$td.log.gpg
    echo "Config Changelog for $td" | mailx -s "Config Changelog Report $td" -a "/diff_reports/changelog_$td.zip" tyla@itmatic101.com

    # replicate the baseline to latest in config
    rsync -azh /scripts/baseline/ /config/latest/

    # git auto version control on /config/latest/
    cd /config/latest/
    git add *
    git commit -am "auto commit for $td"
    git push origin master
fi  
```

နောက်ဆုံးမှာ… file တွေမလိုပဲနဲ့ storage မကုန်ရလေအောင်လို့ cleanup ကို အခုလိုလုပ် လိုက်ပါတယ်။ ရိုးရှင်းပြီးလွယ်ကူလှတဲ့ bash နဲ့ network automation ကိုထည့်ပြီးတော့ use case တစ်ခုတည်ဆောက်ပြခြင်းဖြစ်ပါတယ်။

```
# cleanup unnecessary files 
rm /scripts/temp/* 2> /dev/null
rm /diff_reports/*.zip 2> /dev/null
rm /diff_reports/*.gpg 2> /dev/null
```

အထက်မှာမြင်တဲ့အတိုင်း… bash ကိုအသုံးပြုပြီးတော့ network automation တစ်ခုကို တင်ပြသွားပါတယ်။ Python လောက် ခပ်သွက်သွက် script တစ်ခုမတည်နိုင်သော်လည်း bash ဟာ automation အတွက် ကိုယ့် network မှာ use case ရှိနိုင်တယ်ဆိုတာ သိစေလိုပါတယ်။ ဒီလိုမှမဟုတ်ဘူး… ကိုယ့်အလုပ်မှာ Cisco တစ်မျိုးပဲသုံးတယ်ဆိုတဲ့သူ တွေအတွက်တော့ Ansible လို network automation ဟာ ပိုပြီးတော့ ထိရောက်နိုင်ပါတယ်။ သို့သော်… အဲ့ဒီလို environment မျိုးက ခပ်ရှားရှားဖြစ်ဖို့များတဲ့ အတွက် ထဲထဲဝင်ဝင်တိုးဝေ့ပြီးတော့ လိုအပ်တဲ့ဟာ ကိုလိုအပ်သလို အသုံးပြုနိုင်ဖို့အတွက် bash ဟာလည်း သူ့နေရာနဲ့သူ အစွမ်းထက်လှ့ပါတယ်။ နောက်ပိုင်းမှာတော့… စာရေးသူ စိတ်ကြိုက်တွေ့လှတဲ့ Python နဲ့ Ansible တွေကို အသုံးပြုတဲ့ network automation workflow တွေအကြောင်းကို ဆက်ရေးပါ့မယ်။ ဒီ post ကိုတော့ ဒီမှာတင်ပဲရပ်လိုက်ပါတော့မယ်။
