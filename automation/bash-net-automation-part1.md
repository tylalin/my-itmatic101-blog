# Bash နဲ့ Network Configuration Management system တစ်ခုတည်ဆောက်ပုံ – အပိုင်း\(၁\)

ဒီ post ကိုမဖတ်ခင်မှာ အရှေ့မှာစာရေးသူ ရေးထားတဲ့ FTP/TFTP ပေါ်မှာ network configuration files တွေကို automatic backup လုပ်တဲ့ပုံကို အပိုင်းနှစ်ခုခွဲပြီးတော့ ရေးထားတဲ့ “FTP/TFTP server ပေါ်မှာ network config တွေကို auto backup လုပ်ပုံ – အပိုင်း \(၁\)” နဲ့ “FTP/TFTP server ပေါ်မှာ network config တွေကို auto backup လုပ်ပုံ – အပိုင်း \(၂\)” ကိုအရင်သွားပြီး ဖတ်လိုက်ရင်ပိုပြီးတော့ အဆင်ပြေပါလိမ့်မယ်။ ဒါမှမဟုတ်ဘူး ကိုယ်စီမှာရှိပြီးသား network configuration files တွေကို ဒီ post ကနည်းနဲ့ standalone ပုံစံမျိုး bash programming ကို အသုံးပြုပြီးတော့ network configuration management system တစ်ခုတည်ဆောက်ချင်ရင်လည်း ဖြစ်ပါတယ်။ စာရေးသူအတွက်တော့ တစ်ခုပေါ်တစ်ခု အကြံရလိုက်ရင် ကောက်ရေးလိုက်ရင်းနဲ့ bash scripts လေးတွေထွက်လာလိုက်၊ python script လေးတွေထွက်လာလိုက်၊ ansible-playbook တွေကိုဖန်တီးလိုက်နဲ့ စိတ်ရှိတိုင်းကို automation လုပ်လို့ရတဲ့ အပိုင်းတွေကို အစပိုင်းမှာ အချိန်ပေးပြီးတော့ automate လုပ်ထားလိုက်ပါတယ်။ ဒီ့အတွက် မနက်တိုင်း ကိုယ်သောက်နေကြ ကော်ဖီကို စိတ်အေးလက်အေး သောက်နိုင်ပြီးတော့ အချိန်တန်ရင် ကိုယ်စီကို automatic csv file နဲ့ report ကို ကိုယ့်ရဲ့ mailbox ထဲရောက်လာတဲ့အတွက် တကူးတက တစ်ခုချင်းစီလိုက် စစ်နေစရာမလိုတော့ပါဘူး။ Email နဲ့ကိုယ့်ရဲ့ network configuration files တွေကိုပို့ရတာဖြစ်တဲ့အတွက် အရေးကြီးတဲ့ အချက်အလက်တွေကို encrypt လုပ်ပြီးတော့မှာ ပေးပို့မှာဖြစ်တဲ့အတွက် စိတ်ပူစရာမလိုပါ။ စာရေးသူ အရှေ့က post နှစ်ခုက ဆိုင်ရာဆိုင်ရာ network device configuration files တွေနဲ့ scripts တွေကို GitHub က ဒီ [link](https://github.com/tylalin/ITmatic101/tree/master/network_config_mgmt) မှာတင်ပေးထားပါတယ်။

[အပိုင်း\(၂\) ](https://www.itmatic101.com/2019/11/20/ftp-tftp-server-network-config-backup-part-2/)မှာ [housekeeping.sh](https://github.com/tylalin/ITmatic101/blob/master/network_config_mgmt/housekeeping.sh) နဲ့ [crontab](https://github.com/tylalin/ITmatic101/blob/master/network_config_mgmt/crontab) မှာ scheduler ဘယ်လို အလုပ်လုပ်သလဲဆိုတာနဲ့ အဆုံးသတ်ထားပါတယ်။ ဒီအပိုင်းမှာတော့ စနစ်တကျ ဆိုင်ရာ device configuration တွေကို /configs ဆိုတဲ့ directory အောက်မှာသိမ်းထားပြီးတဲ့နောက် ကိုယ်ရဲ့ FTP server ပေါ်က configuration backup file တွေ up-to-date ဖြစ်လား မဖြစ်ဘူးလားဆိုတာကို သိနိုင်ဖို့အတွက် ကိုယ်နေ့တိုင်းသွားပြီးတော့ /configs အောက်မှာစစ်ဖို့ရာအတွက် အချိန်တွေအများကြီးကုန်မှာဖြစ်သလို human-error လို့ခေါ်တဲ့ ကိုယ်တိုင် စစ်နေတုန်းမှာ ကိုယ့်ရဲ့ ပေါ့လျှော့မှုကြောင့် အချို့ဟာတွေမှာ မှားသွားနိုင်ပါတယ်။ ဒီ့အတွက် computer ရဲ့ ကျွမ်းကျင်ရာ repetition နဲ့ automation မှာ ကိုယ့်ရဲ့ ကြံဆမှုပေါ်မှာမူတည်ပြီးတော့ ကိုယ်နဲ့အဆင်ပြေဆုံးဖြစ်မယ့် programming ကိုအသုံးပြုသင့်တယ်။ ဒါမှလည်း ကိုယ့်အတွက် နေ့စဉ် ဝန်ပေါ့မှာပါ။ ဒီနေရာမှာ စာရေးသူ Linux ရဲ့ native shell ဖြစ်တဲ့ bash ကို တမင်တကာရွေးပြီးတော့ စမ်းသပ်အသုံးပြုကြည့်ပါတယ်။ Bash အလုပ်ဖြစ်မှန်းသိသော်လည်း network automation အတွက် configuration management အပိုင်းမှာ ဘယ်လောက်ထိ ကိုယ်သုံးနိုင်သလဲဆိုတာကို သိချင်တာလည်းပါတယ်။ ကြီးကျယ်ခမ်းနားအောင်လို့ configuration management လို့ဆိုသော်လည်း အရှင်းဆုံးပြောရရင် bash နဲ့ flat files တွေကိုဟိုစစ်ဒီစစ်လုပ်တာပါပဲ။ Ansible ဟာ အဲ့ဒီ configuration management အတွက်အလုပ် အရမ်းဖြစ်တဲ့ tools-chain တစ်ခုပါ။ ကိုယ်ဘယ်လောက်ဒီ Ansible platform ပေါ်မှာအလုပ်လုပ်နိုင်သလဲပေါ်မှာမူတည်ပြီးတော့ efficient ဖြစ်သလား မဖြစ်ဘူးလားဆိုတာ အဆုံးအဖြတ်ပေးနိုင်တယ်။ နောက်ပိုင်းမှာ စာရေးသူ infrastructure မှာ အသုံးပိုဝင်တဲ့ Terraform လိုမျိုး provisioning management tools-chain ကိုလည်း နည်းနည်းမျက်စိကျလာမိပါတယ်။ သိကျွမ်းတဲ့ လူတွေပြောပုံထောက်တော့ Terraform ဟာ provisioning နဲ့ deployment မှာ infrastructure အတွက် အသုံးအဝင်ဆုံးဖြစ်ပြီးတော့၊ နောက်ဆက်တွဲဖြစ်တဲ့ configuration management မှာတော့ Ansible ကိုပဲဆက်ပြီးတော့ အားကိုးနိုင်ပါတယ်။ နောက်ပိုင်း hybrid tools-chain များထပ်ပြီးတော့ ထွက်လာအုံးမလားတော့ မပြောတတ်ပါ။ မည့်သို့ပင်ဖြစ်စေ… တကယ့်ကိုမျက်စိကျစရာ automation ကမ္ဘာက tools-chain / tools-set တွေလို့ဆိုရမှာပါ။ DevOps culture ဟာအခုလိုမျိုး automation platform တွေကိုမွေးထုတ်ပေးလိုက်ပြီးတော့၊ နောက်တခါ အဲ့ဒီ automation platform တွေကပဲ DevOps culture ကိုပြန်ပြီးတော့ empower လုပ်ပေးနိုင်တဲ့ မြေသြစာ အဖြစ်တဖန် အသက်ပြန်ဝင်လာစေပါတယ်။ ပြောမယ်ဆိုရင်တော့ DevOps ရဲ့ ကြီးစိုးမူဟာ Cisco လိုမျိုး conservative ဖြစ်တဲ့ tech giant ကိုတောင် DevNet ဆိုပြီးတော့ revolutionise ဖြစ်စေခဲ့ပါတယ်။ စာရေးသူတို့ တွေးနေကြ sysadmin / network engineer mindset နဲ့အရှေ့မှာ သိပ်ပြီးတော့ မလွယ်ကူတော့ပါဘူး။ နည်းပညာလောကထဲမှာ ဒီထက်မကတဲ့ အပြောင်းအလဲတွေကိုယ့် ပတ်ဝန်းကျင်မှာ ထက်ပြီးတော့ တွေ့လာမြင်လာရအုံးမှာပါ။

![Optimise Bash Script Programming](https://i1.wp.com/www.itmatic101.com/wp-content/uploads/2020/09/Screenshot-from-2020-09-17-22-11-52-1024x806.png?resize=674%2C530&ssl=1)

အခုတော့… စာရေးသူရဲ့ bash programming နဲ့ file တွေကို ဘယ်လိုမျိုး manage လုပ်သလဲဆိုတာကို အခြေခံအဖြစ်မြင်စေချင်ပြီးတော့၊ automation လုပ်လို့ရနိုင်တဲ့ အကျိုးကျေးဇူးတွေကို မြင်နိုင်ဖို့ရာအတွက် ကြိုးစားကြည့်ရအောင်။ ဒီလို အခြေခံကျတဲ့ bash လိုမျိုးဟာနဲ့ automation တစ်ခုတည်ဆောက်နိုင်ရင် အခြားသော automation platform တွေကို အသုံးပြုပြီးတော့ leverage ပိုပြီးရနိုင်သလဲဆိုတာကို မြင်စေချင်ပါတယ်။ အရင်ဆုံး backup report အတွက်အသုံးပြုတဲ့ bash script အကြောင်းအရင်ဆုံးသွားလိုက်ရအောင်။ ဒီ script ဟာစာရေးသူ housekeeping လုပ်ပြီးတော့ Cisco, Huawei, HPE, MikroTik နဲ့ FortiGate configuration backup file တွေကို /configs directory အောက်မှာသိမ်းဆည်းပြီးတဲ့နောက် ကိုယ့်ရဲ့ file တွေ up-to-date မှဖြစ်ရဲ့လားလို့ စစ်ဖို့သိနိုင်ဖို့ အတွက် အပတ်တိုင်း crontab နဲ့ schedule လုပ်ပြီးတော့ run တဲ့ script ပါ။ ဒီ file ရဲ့နာမည်ကတော့ backup\_report.sh ပါ။ GitHub မှာတော့ ဒီ [link](https://github.com/tylalin/ITmatic101/blob/master/network_config_mgmt/backup_report.sh) မှာသွားကြည့်လို့ရပါတယ်။

```text
#!/bin/bash

td=$(date +%Y%m%d)
touch /backup_reports/backup_report_"$td".csv
echo "Network Device Name","Last Config Backup File","File Age","Status" > /backup_reports/backup_report_"$td".csv

# Cisco devices' config backup check
cd /configs/cisco
while d= read -r line
do
	last=$(ls -t1 | grep $line | head -1)
    if [ -f "$last" ]; then
        fd=$(date +%s -r $last)
        cd=$(date +%s)
        diff=`expr $cd - $fd`
        if [ "$diff" -gt 864000 ]; then 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
        else 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
        fi
    else
        echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
    fi
done < /scripts/inventory/cisco


# HPE devices' config backup check
cd /configs/hpe
while d= read -r line
do
	last=$(ls -t1 | grep $line | head -1)
    if [ -f "$last" ]; then
        fd=$(date +%s -r $last)
        cd=$(date +%s)
        diff=`expr $cd - $fd`
        if [ "$diff" -gt 864000 ]; then 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
        else 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
        fi
    else
        echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
    fi
done < /scripts/inventory/hpe


# FortiGate devices' config backup check
cd /configs/fortigate
while d= read -r line
do
	last=$(ls -t1 | grep $line | head -1)
    if [ -f "$last" ]; then
        fd=$(date +%s -r $last)
        cd=$(date +%s)
        diff=`expr $cd - $fd`
        if [ "$diff" -gt 864000 ]; then 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
        else 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
        fi
    else
        echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
    fi
done < /scripts/inventory/fortigate


# Huawei devices' config backup check
cd /configs/huawei
while d= read -r line
do
	last=$(ls -t1 | grep $line | head -1)
    if [ -f "$last" ]; then
        fd=$(date +%s -r $last)
        cd=$(date +%s)
        diff=`expr $cd - $fd`
        if [ "$diff" -gt 864000 ]; then 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
        else 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
        fi
    else
        echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
    fi
done < /scripts/inventory/huawei


# MikroTik devices' config backup check
cd /configs/mikrotik
while d= read -r line
do
	last=$(ls -t1 | grep $line | head -1)
    if [ -f "$last" ]; then
        fd=$(date +%s -r $last)
        cd=$(date +%s)
        diff=`expr $cd - $fd`
        if [ "$diff" -gt 864000 ]; then 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
        else 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
        fi
    else
        echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
    fi
done < /scripts/inventory/mikrotik

echo "Weekly Config Backup Report for $td" | mailx -s "Backup Report $td" -a "/backup_reports/backup_report_"$td".csv" tyla@itmatic101.com
```

ဒီအပေါ်က script မှာ ထက်ခါသလဲလဲ အသုံးပြုတဲ့ code တွေကို တွေ့ရပါလိမ့်မယ်။ Bash programming ကိုအသုံးပြုခြင်းဖြင့် python မှာလိုမျိုး function တွေကို အလွယ်တကူ တည်ဆောက် နိုင်ပါတယ်။ ဒီထက်ကောင်းအောင်တော့ ပြင်ဆင်ပြီးတော့ code ကိုပြန်လည်ရေးနိုင်သော်လည်း လက်ရှိအနေအထားမှာတော့ အလုပ်လုပ်တဲ့ script တစ်ခုအနေနဲ့ သတ်မှတ်လိုက်ကြရအောင်။ Bash script ကို optimise ဘယ်လိုလုပ်သလဲဆိုတာပါ မြင်နိုင်အောင်လို့ အစမှာ bash ကို linear/sequential အတိုင်း execute လုပ်ရင် အခုလိုမျိုး တစ်လိုင်းပြီးတစ်လိုင်း shell commands တွေကို run သွားတာပဲဖြစ်ပါတယ်။ အနောက်မှာ function ကို အသုံးပြုပြီးတော့ code ကို compact ဖြစ်အောင် တည်ဆောက်နိုင်သလဲဆိုတာ ဆက်လက် ဖော်ပြပေးပါ့မယ်။ ဒီတစ်ခုမှာတော့…. ပထမအပိုင်းတပိုင်းကို ဘာလုပ်ထားသလဲဆိုတာ သဘောပေါက်တာနဲ့ နောက်အပိုင်းတွေ ကိုလည်းအလွယ်တကူ သဘောပေါက်ပါပြီ။ ဒီတော့ အပေါ်ဆုံးကနေစလိုက်ရအောင်။

```text
td=$(date +%Y%m%d)
touch /backup_reports/backup_report_"$td".csv
echo "Network Device Name","Last Config Backup File","File Age","Status" > /backup_reports/backup_report_"$td".csv
```

ဒီတစ်ခုမှာ စာရေးသူ လိုအပ်တဲ့ဟာတွေကို အရင်ဆုံး setup လုပ်လိုက်တဲ့ သဘောပါ။ td ဆိုတဲ့ variable မှာ ဒီ script ကို run တဲ့နေ့စွဲကို စာရေးသူ အကြိုက်ဆုံး date format ကိုပြောင်းပြီးတော့ သိမ်းထားလိုက်တာပဲဖြစ်ပါတယ်။ ထွက်လာမယ့် date ရဲ့ format ကတော့ “20200916” ပဲဖြစ်ပါတယ်။ date ရဲ့ အနောက်က + ကတော့ output ကို format လုပ်မယ်လို့ပြောပြီးတော့ %Y%m%d ဆိုတာကတော့ year, month, day ဆိုပြီး format လေးကို output အနေနဲ့ လိုချင်တယ် ပြောထားတာပါ။ ပြီးတော့ တနေ့စာအတွက် .csv file တစ်ခုကို $td နဲ့ နေ့စွဲလေးအနောက်ကထည့်ပြီးတော့ touch နဲ့ ဖန်တီးထားလိုက်တာပါ။ ပြီးတာနဲ့ အဲ့ဒီ .csv file ရဲ့ column တစ်ခုချင်းစီမှာ header လေးတွေကို လိုက်ထည့်လိုက်ပါတယ်။ ရိုးရင်းတဲ့ setup အပိုင်းပါ။

နောက်တပိုင်းက device name တွေကို စီပြီးတော့ ထည့်ထားတဲ့ device inventory flat text file တစ်ခုလိုပါတယ်။ အဲ့ဒီ file ထဲမှာတော့ FTP server ပေါ်ကိုရောက်လာတဲ့ network configuration file name မှာပါတဲ့ device name တွေကိုထည့်ထားပေး ဖို့လိုပါလိမ့်မယ်။ ဒါမှ ကိုယ့်ရဲ့ bash script မှာ name ကို grep သုံးပြီးတော့ ရှာနိုင်မှာဖြစ်ပါတယ်။

```text
# Cisco devices' config backup check
cd /configs/cisco
while d= read -r line
do
	last=$(ls -t1 | grep $line | head -1)
    if [ -f "$last" ]; then
        fd=$(date +%s -r $last)
        cd=$(date +%s)
        diff=`expr $cd - $fd`
        if [ "$diff" -gt 864000 ]; then 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
        else 
            echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
        fi
    else
        echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
    fi
done <  /scripts/inventory/cisco
```

ပထမတစ်လိုင်းမှာတော့ cd /configs/cisco ဆိုပြီးတော့ ကိုယ်အလုပ်လုပ်မယ့် directory ထဲကိုအရင်ပြောင်းလိုက်ပါတယ်။ ပြီးတော့ while loop ကို သုံးပြီးတော့ /scripts/inventory/cisco file ထဲမှာထည့်ထားတဲ့ device name ကို တစ်လိုင်းချင်းစီ လိုက်ဖတ်လိုက်ပြီးတော့၊ အဲ့ဒီ device name နဲ့ match ဖြစ်တဲ့ file နာမည်ကို /configs/cisco directory အောက်မှာ ls -t1 \| grep $line \| head -1 ဆိုပြီးတော့ pipeline ကိုအသုံးပြုပြီးရှာလိုက်ပါတယ်။ ဒီ ls command ကတော့ နောက်ဆုံး modified လုပ်တဲ့ date ကို sort လုပ်ပြီးတော့ အပေါ်ဆုံးမှာ file ကို နောက်ဆုံးသော up-to-date ဖြစ်တဲ့ file ဆိုပြီးတော့ သတ်မှတ်လိုက်တာပါ။ နောက်ပြီးတော့ လက်ရှိအချိန်ကိုရှာပြီးတော့ နောက်ဆုံး modified လုပ်ထားတဲ့ modified date ကနေနုတ်လိုက်ရင် file ရဲ့ သတ်တမ်း ဘယ်လောက်ရှိပြီဆိုတာ သိပါပြီ။ ပြီးတာနဲ့ အဲ့ဒီ file သတ်တမ်း တစ်ပတ်ကျော်ကြာသွားပြီဆိုရင် Fail ဆိုပြီးတော့ အပေါ်မှာ အသစ်ဖန်တီးထားတဲ့ .csv file ထဲကို သင့်တော်သလို column တစ်ခုချင်းစီမှာ သွားပြီးတော့ append လုပ်လိုက်ပါတယ်။ လုပ်ငန်းစဉ်ကတော့ ဒါပါပဲ။ ရှင်းပါတယ်။ အချိန်ပေးပြီးတော့ syntax နဲ့ command usage တွေကို တစ်ခုစီမသွားလိုတော့ပါ။ အကျဉ်းချုပ်သဘောမျိုးသာ ရှင်းလိုက်ပါတယ်။ အဓိက ကတော့ concept နဲ့ workflow ကို နားလည်စေချင်တယ်။ ဒီ script နဲ့တွဲပြီးတော့ သုံးမယ့် directory structure ကိုတော့ အခုလိုမျိုးတွေ့မြင်နိုင်မှာပါ။

```text
├── backup_reports
│   └── backup_report_20200917.csv
├── configs
│   ├── cisco
│   ├── fortigate
│   ├── hpe
│   ├── huawei
│   └── mikrotik
└── scripts
    ├── backup_report.sh
    ├── housekeeping.sh
    └── inventory
```

လက်ရှိမှာ စာရေးသူတို့ bash script ဟာလိုင်းပေါင်း ၁၀၀ ကျော်လောက်ရှိပါတယ်။ ဒီတော့… bash programming မှာ function ကိုအသုံးပြုပြီးတော့ code/script ကို compact ဖြစ်အောင်၊ repetition နည်းအောင်၊ runtime ပိုမြန်လာအောင် ဘယ်လိုမျိုး optimise လုပ်လို့ ရနိုင်သလဲဆိုတာ တချက်ကြည့်လိုက်ရအောင်။ အောက်မှာတော့ compact ဖြစ်အောင် လုပ်ထားတဲ့ script ပုံစံကို ပြပေးထားပါတယ်။

```text
#!/bin/bash

td=$(date +%Y%m%d)
touch /backup_reports/backup_report_"$td".csv
echo "Network Device Name","Last Config Backup File","File Age","Status" > /backup_reports/backup_report_"$td".csv

# backup report function to repeat the same task for device type
backup_report() 
{
    vendor=$1
    cd /configs/$vendor
    while d= read -r line
    do
        last=$(ls -t1 | grep $line | head -1)
        if [ -f "$last" ]; then
            fd=$(date +%s -r $last)
            cd=$(date +%s)
            diff=`expr $cd - $fd`
            if [ "$diff" -gt 864000 ]; then 
                echo "$line","$last","$(($diff / 86400)) day(s) old","Warning"  >> /backup_reports/backup_report_"$td".csv
            else 
                echo "$line","$last","$(($diff / 86400)) day(s) old","Pass"  >> /backup_reports/backup_report_"$td".csv
            fi
        else
            echo "$line","File Not Found","Haven't run backup for this device yet","Fail"  >> /backup_reports/backup_report_"$td".csv
        fi
    done < /scripts/inventory/$vendor
}

for arg in cisco hpe fortigate huawei mikrotik
do
    backup_report $arg
done

echo "Weekly Config Backup Report for $td" | mailx -s "Backup Report $td" -a "/backup_reports/backup_report_"$td".csv" tyla@itmatic101.com
```

အခုဆိုရင်တော့ မြင်တဲ့အတိုင်း script ကတော်တော်လေးကို compact ဖြစ်သွားပါပြီ။ GitHub မှာသွားပြီးတော့ ကြည့်ချင်တယ်ဆိုရင်တော့ ဒီ [link](https://github.com/tylalin/ITmatic101/blob/master/network_config_mgmt/backup_report_compact.sh) ကနေသွားကြည့်နိုင်ပါတယ်။ လိုချင်တဲ့ outcome ထွက်ဖို့အတွက် ကိုယ်ကြိုက်တဲ့ ပုံစံမျိုးကို အသုံးပြုပြီးတော့ optimise လုပ်လို့ ရပါတယ်။ စာရေးသူအတွက်တော့… အခု script/code လောက်ရပြီဆိုရင် functional automation လောက်ဖြစ်မယ်ထင်ပါတယ်။ အခုဆိုရင်… ကိုယ် FTP server ပေါ်မှာ backup လုပ်ထားတဲ့ network configuration file တွေ up-to-date ဖြစ်လား မဖြစ်ဘူးလား အပတ်တိုင်းသိနိုင်အောင်လို့ crontab ကို အသုံးပြုပြီးတော့ weekly အတွက် schedule လုပ်ထားလိုက်ရုံပါပဲ။ Crontab ကို ဒီ [link](https://github.com/tylalin/ITmatic101/blob/master/network_config_mgmt/crontab) ကနေသွားကြည့်လို့ရပါတယ်။ ဒီအပိုင်းမှာတော့ ဒီလောက်နဲ့ပဲရပ်လိုက်ပါတော့မယ်။ နောက်အပိုင်းမှာတော့… change management အတွက် bash ကိုအသုံးပြုပြီးတော့ ပြောင်းလဲသွားတဲ့ network configuration file တွေနဲ့ ဘယ်နားမှာ ဘယ်လိုပြောင်းသွားသလဲ ဆိုတာကို track လုပ်နိုင်အောင် automate လုပ်တဲ့ပုံစံလေး တစ်ခုကို ဆက်လက်ဆွေးနွေးပြချင်ပါတယ်။ အားလုံးအတွက် စိတ်ဝင်စားစရာ တစ်ခုဖြစ်မယ်လို့လည်း မျှော်လင့်ရင်းနဲ့ ဒီအပိုင်းကို အဆုံးသတ်လိုက်ပါတော့မယ်။  


