# အနားမသပ်နိုင် သေးတဲ့ Infrastructure as Code (IaC) - အပိုင်း(၄)

ဒီအပိုင်းကို တော်တော်နဲ့ ဆက်မရေးဖြစ်ပဲနဲ့ အခုမှတခါ Ansible နဲ့ Infrastructure as Code (IaC) ကိုဘယ်မျိုးလုပ်ရင်ကောင်းမယ်ဆိုတဲ့ idea တစ်ခုရတာနဲ့ ပြန်ပြီးဆက်ရေးဖြစ်ပြန်တယ်။ စာရေးသူ ပြီးခဲ့တဲ့ နှစ်သစ်မကူးခင်ကာလက ရှိပြီးသား WireGuard VPN server တစ်လုံးကို ဖျက်စီးပြီးတော့ အသစ်ကနေပြန်စပြီး setup လုပ်ဖို့ဖြစ်လာပြန်ပါတယ်။ ပုံမှန်အားဖြင့်... WireGuard VPN server တစ်လုံးတည်ဆောက်ဖို့နဲ့ လိုအပ်တဲ့ peer configuration ထုတ်ဖို့ဆိုတာ မခက်ခဲပေမယ့် လက်ဝင်တယ်၊ အချိန်ကုန်တယ်လို့ စိတ်ထဲမှာထင်လာလို့ automation လုပ်ဖို့အတွက် အနည်းငယ်အားစိုက်ထုတ် ရပါတော့တယ်။ VPS တစ်လုံးကို Linode ပေါ်မှာတည်ဆောက်တာကစလို့ လိုအပ်တဲ့ system configuration နဲ့ wireguard configuration တွေအကုန်လုံး ကို စာရေးသူ Ansible နဲ့ ရအောင်လုပ်ဖို့ ကြိုးပမ်းပါတော့တယ်။ ပြီးတော့ တဆက်တည်းမှာပဲ peer configuration တွေကိုလည်း တပါတည်း Ansible နဲ့ လုပ်နိုင်ရင် ကောင်းမယ် စဉ်းစားမိတာနဲ့ အရင်က bash နဲ့ automation လုပ်ထားတဲ့ workflow ကိုပါ integrate လုပ်ချင်လာပြန်ပါတယ်။ ဒီတော့... end-to-end automation ကိုမြင်ယောင်ပြီးတော့ တစချင်းစီ play တွေတည်ဆောက်ပါခဲ့ပါတယ်။ အားလုံး အလုပ်လုပ်ပြီဆိုတာနဲ့ ကိုယ်လည်း နှစ်သစ်မှာ အပြင်မှာလည်ပတ်ပြီးတော့မေ့သွားမှာ စိုးရိမ်လို့ အင်္ဂလိပ်လိုပဲ ခပ်သွက်သွက်လေး self-note ပုံစံမျိုး ချရေးထားလိုက်ပါတယ်။ အနည်းဆုံးတော့ ကိုယ့်အတွက် documentation တစ်ခုကျန်အောင်လို့ပါ။ ဒါနဲ့ အဲ့ဒီ အင်္ဂလိပ်လို ရေးထားတဲ့ အတိုင်းပဲ share ပေးထားလိုက်ပါတယ်။ နောက်မှ... IaC အပိုင်း(၄) အတွက် ဒီ use case လေးနဲ့တော့ အဆင်ပြေတယ်ဆိုပြီး အခုဆက်ရေးဖြစ်သွားတယ်။ ဒီ article မှာတော့ စာရေးသူ အဲ့ဒီ playbook မှာပါဝင် အစိတ်အပိုင်းလေးတွေကို အချိန်ရသလောက် နည်းနည်းချင်းစီ ရှင်းပြသွားချင်ပါတယ်။&#x20;

### Ansible workflow အတွေးလုပ်ငန်းစဉ်

ပထမဆုံး အနေနဲ့ စာရေးသူ အတွေးလုပ်ငန်းစဉ်ကို အရင်ချပြချင်ပါတယ်။ Linode မှာဘယ်လိုမျိုး VPS တစ်လုံးကို Ansible နဲ့ တည်ဆောက်သလဲဆိုတာကို ရှာဖို့အတွက်က Linode မှာ documentation တွေအများကြီးရှိပါတယ်။ ဒီအတွက်... VPS တစ်လုံးဖြစ်အောင် Ansible နဲ့လုပ်ဖို့ဆိုတာတော့ သိပ်မခက်ဘူးဆိုတာတွေးမိပါတယ်။ ပြဿနာက ကိုယ်တစ်ယောက်တည်း သုံးလို့ရအောင် လုပ်ဖို့ထပ် ကိုယ်အားလုံးပြီးသွားလို့ ပြန် share တဲ့အခါမှာ အခြားသူအတွက် နားလည်လွယ်ဖို့အတွက် ထပ်ကာထပ်ကာပြန်သုံးနိုင်ဖို့အတွက် variable တွေကို အသုံးပြုနိုင်ဖို့ ဆုံးဖြတ်လိုက်ပါတယ်။ ဒီတော့... နောက်အသုံးပြုချင်တဲ့သူက var folder ထဲမှာရှိတဲ့ variable တွေကိုလိုသလို ပြောင်းလဲသုံးနိုင်ဖို့အတွက် မခက်ခဲတော့ဘူးလို့ မြင်ပါတယ်။ နောက်တစ်ခုက... လိုအပ်တဲ့ content input တွေကို သင့်တော်သလို Jinja2 template နဲ့လုပ်ဖို့လည်း စိ်တ်ကူးမိပါတယ်။ sshdconfig လိုမျိုး static file ကိုတော့ files ဆိုတဲ့ folder မှာပဲထားပြီး ဒီအတိုင်းထည့်ဖို့ စဉ်းစားခဲ့ပါတယ်။ sed တို့ awk တို့ကို သုံးပြီး sshdconfig file ကို Ansible ကနေ edit လုပ်နိုင်သော်လည်း immutable workflow အတွက် static file ကပိုအလုပ်ဖြစ်မယ်လို့ ထင်ပါတယ်။ ဒီအတွက် build process တိုင်းမှာ sshd\_config ဟာ desired state မှာအမြဲရှိဖို့ အတွက်လည်း ရည်ရွယ်ပါတယ်။&#x20;

လုပ်ရင်းကိုင်ရင်းနဲ့ စာရေးသူအတွက် အခက်အခဲတစ်ခုက Linode မှာတည်ဆောက်လိုက် VPS တစ်လုံးကို on-the-fly inventory တစ်ခုတည်ဆောက်ဖို့လိုပါတယ်။ အဲ့ဒီအတွက် in-memory inventory တစ်ခုကို Ansible ရဲ့ add\_host module ကိုသုံးထားပါတယ်။ ဒီလိုလုပ်လိုက်ခြင်းဖြင့် inventory file ကိုသပ်သပ် ဖန်းတီးစရာမလိုတော့တဲ့အပြင်၊ workflow ဟာလည်း ပိုပြီးတော့ fluid ဖြစ်လာတယ်၊ dynamic ပိုဖြစ်လာတယ်လို့ မြင်မိပါတယ်။ Ansible playbook မှာတော့ stanza တစ်ခုတည်းပါ၊ ကိုယ်လုပ်ချင်တဲ့ပုံစံဖြစ်ဖို့အတွက် ဘယ် module ကိုအသုံးချရမလဲဆိုတာ သိဖို့ကတော့ အချိန်အများကြီးပေးပြီးတော့ ရှာလိုက်ရပါတယ်။​&#x20;

နောက်တစ်ခုက... စာရေးသူလုပ်ချင်တဲ့ဟာတွေကို Ansible playbook တစ်ခုတည်းမှာပဲ အပိုင်းလေးတွေခွဲပြီးတော့ လုပ်ချင်ပါတယ်။ အဲ့ဒီအတွက် Ansible မှာရှိတဲ့ block ဆိုတဲ့ concept ကိုအသုံးပြုပါတယ်။ ပြီးတော့ testing အတွက်လည်း လိုအပ်တဲ့ block တွေကိုတစ်ခုချင်းစီ ပြန်ပြီးခေါ်လို့ရနိုင်အောင်လို့ tags ကိုသုံးထားပါတယ်။ Testing အတွက်မပါလည်းရပါတယ်၊ စာရေးသူ build process ပြီးရင် VPS ထဲဝင်ဝင် စစ်ရလို့ စိတ်မရှည်တော့လို့ testing block ကိုထပ်ပြီးတော့ implement လုပ်ဖြစ်သွားတာပါ။ Block တွေတစ်ခုပြီးတစ်ခုရေးရင်နဲ့ သတိထားမိလာတာ စာရေးသူ ရဲ့ Line တွေအများကြီးဖြစ်လာပါတယ်၊ ဒီ့အပြင် VPN user တွေအတွက် QRcode တွေကိုအများကြီးရိုက်ထုတ်တဲ့အခါ loop တစ်ခုလိုအပ်တဲ့အတွက် wguser.yml ဆိုတဲ့ playbook ကို သီးသန့်ခွဲထုတ်ဖို့ ဖြစ်လာပြန်တယ်။ ဒီလိုခွဲထုတ်လိုက်ခြင်းအားဖြင့် readability လည်း တက်လာသလို၊ code ရဲ့ workflow ကပိုပြီးတော့ ပြေပြစ်သွားပါတယ်။ နောက်ဆုံးတစ်ခုကတော့... teardown အတွက် wg\_PURGE.yml playbook တစ်ခုကို ထပ်မံတည်ဆောက်ဖို့ ဖြစ်လာပြန်ပါတယ်။&#x20;

### လက်တွေ့အသုံးချပုံ

စာရေးသူရဲ့ Ansible playbook နဲ့ အခြား folder တွေအကုန်လုံးကို အောက်မှာပါတဲ့ link သွားပြီးတော့ download ဆွဲလို့ရပါတယ်။&#x20;

{% embed url="https://github.com/tylalin/linode-ansible-wireguard" %}
Linode Ansible WireGuard
{% endembed %}

ပထမဆုံး Linode ရဲ့ API python library ကို အောက်မှာပြထားတဲ့ အတိုင်း pip နဲ့အရင်ဆုံး install လုပ်ရပါ့မယ်။&#x20;

```
sudo pip install linode_api4
```

ဒါဆိုရင်တော့... Linode ရဲ့ API ကိုအသုံးပြုပြီးတော့ Ansible မှာ VPS တစ်လုံးတည်ဆောက်ဖို့ အဆင်သင့်ဖြစ်ပါပြီ။ ဒီတော့ wg\_build.yml စပြီးတော့ကြည့်လိုက်ရအောင်ဗျ။&#x20;

```
# First play is used to create a new linode with your Linode portal API Token as below play
- name: CREATE A NEW LINODE
  hosts: localhost
  tags: [ always, infra ] # those tags can be used for easy access to a particular play of the whole playbook
  vars_files:
    - ../vars/linode_wg.yml

  tasks:
    - name: Create a new Linode.
      linode_v4:
        label: "{{ hostname }}"
        access_token: "{{ token }}"
        type: "{{ type }}"
        region: "{{ region }}"
        image: "{{ image }}"
        root_pass: "{{ password }}"
        authorized_keys: "{{ ssh_keys }}"
        group: "{{ gt }}"
        tags: "{{ gt }}"
        state: present
      register: tyla

    - name: Display info about my Linode instance # this task is used for the new Linode verificaiton
      debug:
        msg: "{{ hostname }} | {{ tyla.instance.id }} | {{ tyla.instance.ipv4[0] }}"

    - name: Add new host to in-memory inventory # this task is used to add the Linode public IP to Ansible in-memory inventory along with its group name
      add_host:
        name: "{{ tyla.instance.ipv4[0] }}"
        groups: linode_wg
      changed_when: false

    - name: Wait for Linode to listen on port 22 # ensure that the new Linode is running and ready to move on with the next play
      wait_for:
        state: started
        host: "{{ tyla.instance.ipv4[0] }}"
        port: 22
```

ဒီအပို်င်းမှာတော့ ဘာမှထွေထွေထူးထူး မရှိပါဘူး။ Linode ရဲ့ API ကိုအသုံးပြုပြီးတော့ VPS တစ်လုံးတည်ဆောက်တယ်၊ ပြီးရင် in-memory inventoy တည်ဆောက်တယ်၊ နောက်တော့ port 22 က Linode ချပေးတဲ့ public IP မှာ ready ဖြစ်ပြီလာဆိုတာကို စစ်ကြည့်တယ်။ VPS ကအားလုံး ready ဆိုတော့မှ နောက်အဆင့်ကို ထပ်ပြီးတော့သွားဖို့ အဆင့်သင့်ဖြစ်ပါတော့တယ်။ လိုအပ်တဲ့ variable တွေကိုတော့ vars folder အောက်က linode\_wg.yml မှာအောက်ကအတိုင်းတွေ့ရမှာပါ။&#x20;

```
ssh_keys: > ['<< Your SSH Public Key Here! >>', '~/.ssh/id_rsa.pub']

hostname: tyla-linode-wg01 # change the hostname as required

type: g6-nanode-1 # change Linode Plan as required. Here it uses the Linode's Shared CPU Nanode (RAM: 1 GB, CPUs: 1 & Storage: 25 GB) as my node

region: ap-south # change the region as required. Here it uses Singapore as my region

image: linode/ubuntu20.04 # change the image as required. Here it uses the Linode's Ubuntu20.04 as my base image

gt: tyla-linode-wg # it uses for group and tag names

wg_ip: '192.168.69.254' # wireguard server wg0 virtual interface IP

my_ip: '1.2.3.4' # your public IP for SSH remote access restriction

password: << Your "ansible-vault encrypt_string 'YourSecretHere' --name 'password'" Output Here! >> # root password used for the new Linode which is encrypted with ansible-vault for security

token: << Your "ansible-vault encrypt_string 'YourLinodeAPITokenHere' --name 'token'" Output Here! >> # Linode API Token created on your Linode portal which is encrypted with ansible-vault for securityဒုတိယအပိုင်းမှာတော့... ရလာတဲ့ VPS ကို လိုအပ်တဲ့ basic security configuration အတွက် အသုံးချထားပါတယ်။ code block ကို တချက်လောက်ကြည့်လိုက်ရအောင်။ 
```

ဒုတိယအပိုင်းမှာတော့ ရလာတဲ့ VPS ကို လိုအပ်တဲ့ basic security configuration တွေအတွက် အောက်ကအတိုင်း ဆက်ပြီးတော့ Ansible ကိုအသုံးပြုပြီးတော့ configure လုပ်ပါတယ်။&#x20;

```
# Second play is used for a standard initial configuration required on Ubuntu 20.04 Linux box
- name: INITIAL CONFIGURATION ON THE NEW LINODE
  tags: init
  hosts: linode_wg
  user: root
  vars_files:
    - ../vars/linode_wg.yml

  tasks:
    - name: Initial Linode Configuration
      tags: conf
      block: # block is used here for controlling which set of tasks in each I want to execute. e.g., here I tag 'conf'
        - name: Set hostname
          hostname: name="{{ hostname }}"

        - name: Update apt repo and cache
          apt: update_cache=yes force_apt_get=yes cache_valid_time=3600

        - name: Upgrade all apt packages
          apt: upgrade=dist force_apt_get=yes

        - name: Check if a reboot is needed after apt upgrade
          register: reboot
          stat: path=/var/run/reboot-required get_md5=no

        - name: Reboot the Ubuntu Linode
          reboot:
            msg: "Reboot initiated by Ansible due to kernel updates"
            connect_timeout: 5
            reboot_timeout: 300
            pre_reboot_delay: 0
            post_reboot_delay: 30
            test_command: uptime
          when: reboot.stat.exists

        - name: Enable packet forwarding for IPv4 # this task is important for WireGuard to work correctly by allowing IP forwarding thru the node
          sysctl:
            name: net.ipv4.ip_forward
            value: '1'
            sysctl_set: true
            state: present
            reload: true

        - name: Configure SSH key authentication only # desired state of /etc/ssh/sshd_config is used to restrict ssh remote access
          copy: src=../files/sshd_config dest=/etc/ssh/sshd_config
          notify: Restart SSH

        - name: Allow SSH in UFW
          ufw:
            rule: limit
            port: ssh
            proto: tcp
            src: {{ my_ip }}
            dest: 0.0.0.0/0

        - name: Allow WireGuard in UFW
          ufw:
            rule: allow
            port: '51820'
            proto: udp
            dest: 0.0.0.0/0

        - name: Deny everything and enable UFW
          ufw:
            state: enabled
            policy: deny
            log: true

    - name: Unit testing on initial configuration # unit testing to verify the system configured and tags are used to run specific block
      tags: [ never, tests, conf_test ]
      block: 
        - name: Get the output of /etc/sysctl.conf file
          command: tail -1 /etc/sysctl.conf
          register: sysctl
          changed_when: false

        - name: Test if /etc/sysctl.conf is configured correctly
          assert:
            that:
              - "'net.ipv4.ip_forward=1' in sysctl.stdout_lines"
            success_msg: "[PASS] IP Forwarding is configured correctly."
            fail_msg: "[FAIL] IP Forwarding is not configured or misconfigred."

        - name: Get the output of /etc/ssh/sshd_config
          command: cat /etc/ssh/sshd_config
          register: ssh
          changed_when: false

        - name: Test if /etc/ssh/sshd_config is configured correctly
          assert:
            that:
              - "'PermitRootLogin prohibit-password' in ssh.stdout_lines"
              - "'PubkeyAuthentication yes' in ssh.stdout_lines"
              - "'PasswordAuthentication no' in ssh.stdout_lines"
              - "'PermitEmptyPasswords no' in ssh.stdout_lines"
            success_msg: "[PASS] SSH Daemon is configured correctly."
            fail_msg: "[FAIL] IP Forwarding is not configured or misconfigred."

  handlers:
    - name: Restart SSH
      systemd:
        state: restarted
        name: ssh
```

ဒီတပိုင်းမှာတော့... Ubuntu 20.04 LTS ကို apt update && apt upgrade လုပ်တယ်၊ လိုအပ်ရင် server ကို reboot ချပြီးတော့၊ server ပြန်တက်လာရင် ufw နဲ့ packet forwarding ကို wireguard အတွက်ပြင်ဆင်ရပါတယ်။ ဒီအဆင့်မှာပဲ... sshd\_config ကို local machine ကနေ VPS ပေါ်ကို ကူးယူပြီးတော့၊ handler နဲ့ ssh daemon ကို restart ချပါတယ်။ လိုအပ်ရင် သုံးလို့ရအောင်လို့ unit testing ပုံစံမျိုး code block တစ်ခုကိုလည်း ပြထားတဲ့ အတိုင်းထပ်ပေါင်းထည့်ထားပါတယ်။ Testing အတွက်တကူးတက VPS ထဲဝင်ပြီး ssh နဲ့ sysctl configuration တွေကိုတစ်ခုချင်းစီ စစ်ဆေးစရာမလိုတော့ပါဘူး။ အဲ့ဒီအတွက်... Ansible ရဲ့  assert module ကိုအသုံးပြုထားပါတယ်။&#x20;

&#x20;
