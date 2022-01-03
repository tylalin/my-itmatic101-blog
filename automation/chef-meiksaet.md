# Chef မိတ်ဆက် အပိုင်း(၁)

Infrastructure as Code (IaC) အကြောင်း၊ network/systems automation အကြောင်းတွေကို စာရေးသူစိတ်ဝင်စားလို့လေ့လာရင်း ရသမျှအကုန်သိမ်းကြုံပြီးတော့လေ့လာလိုက်တာဖြင့် ထိုက်သင့်သလောက် ခရီးရောက်သင့်သလောက်ရောက်တယ်လို့ဆိုရမှာပါ။ စာတွေထပ်ပြီးတော့ မရေးဖြစ်ပေမယ့်လည်း လေ့လာစရာရှိတာတွေကိုဆက်ပြီးလေ့လာဖြစ်ခဲ့ပါတယ်။ အရင် IaC အပိုင်းတွေခွဲပြီးတော့ ရေးတဲ့ article တွေမှာဆို Vagrant တို့၊ Terraform တို့ အကြောင်းကို စပြီးမိတ်ဆက်ဖြစ်ခဲ့ဖူးပါတယ်။ အဲ့ဒီတုန်းက အပိုင်း(၄) အတွက် Ansible ကိုအသုံးပြုပြီး IaC ဘယ်လိုလုပ်လို့ရသလဲ ဆိုတာဆက်ပြီးတော့ မရေးဖြစ်ခဲ့ပါဘူး။ စာရေးသူရဲ့ လုပ်ငန်းခွင်မှာကလည်း Network Automation အတွက် Ansible ကို တွင်တွင်ကျယ်ကျယ်သုံးဖြစ်ခဲ့တဲ့အတွက် system automation အတွက် context ကောင်းကောင်းဖြစ်လာမယ့် use case မရှိခဲ့တာကြောင့်လည်းဖြစ်ပါတယ်။ အခုတော့ Linode မှာ VPS တစ်ခုနဲ့ WireGuard VPN server ကိုတည်ဆောက်တာဟာ အသင့်တော်ဆုံး Ansible ရဲ့ IaC workflow တစ်ခုအနေနဲ့ ဆက်ပြီးတော့ ရေးလို့ရသွားပါပြီ။ အဲ့ဒီတော့... IaC အပိုင်း(၄) ကိုမကြာခင်မှာ ဆက်ပြီးတော့တင်ပြသွားပါ့မယ်။ ကျန်တဲ့ အပိုင်းတွေကို မဖတ်ရသေးရင်တော့ အောက်ကလင့်တွေမှာ သွားရောက်ဖတ်ရှုလို့ရပါတယ်။&#x20;

{% embed url="https://my.itmatic101.com/automation/rough-edges-iac-part1" %}

{% embed url="https://my.itmatic101.com/automation/rough-edges-iac-part2" %}

{% embed url="https://my.itmatic101.com/automation/rough-edges-iac-part3" %}

အခု ဒီ article မှာတော့ အရင်တုန်းလုံးဝ မဆွေးနွေးဘူးသေးတဲ့ Chef အကြောင်းပဲဖြစ်ပါတယ်။ Infrastructure Automation မှာ တော်တော်လေးကို mature ဖြစ်တဲ့ configuration management tool တစ်ခုဖြစ်ရုံသာမက၊ Test Kitchen နဲ့ InSpec လိုမျိုး testing engine တွေတခါတည်းပါပြီးသားဖြစ်တဲ့ အတွက်အခြားထွေထွေထူးထူး ထပ်စောင်းရေးရတဲ့ code တွေမလိုပါဘူး။ ပိုပြီးတော့ စိတ်ဝင်စားဖို့ကောင်းတာက wrapper cookbook လို့ခေါ်တဲ့ဟာကိုသုံးပြီးတော့ community မှာရှိပြီးသား  recipes တွေကို ယူသုံးလို့ရတဲ့အတွက် အရမ်းကို အဆင်ပြေပါတယ်။ System ပိုင်းနဲ့ infrastructure ပိုင်းမှာတော့ Chef ဟာ Ansible ထက်သာတဲ့ အရာတွေအများကြီးရှိပါတယ်။ သို့သော် Ansible လိုမျိုး ssh enable ဖြစ်ရုံနဲ့ စပြီးတော့အလုပ်လုပ်လို့ရနိုင်မျိုးတော့လည်း မဟုတ်ပါ။ အသေးစိတ်ကို အောက်မှာဆက်ပြီးတော့ ရှင်းပါ့မယ်။&#x20;

Chef မှာဘာတွေရှိတယ်၊ ဘာတွေလုပ်လို့ရတယ်ဆိုတာတွေကို ဆက်မသွားခင် Chef မှာသုံးတဲ့ အသုံးအနှုန်းလေးတွေကို အရင်ဆုံးမိတ်ဆက်ပေးမှ သဘာဝကြပါလိမ့်မယ်။ နောက်မို့ဆိုရင်... စာရေးသူ ပြောတဲ့  kitchen တို့၊ recipe တို့၊ cookstyle တို့ကို ဘာတွေလဲဆိုပြီးတော့ မျက်စိလည်စရာရှိပါတယ်။&#x20;

**Chef Workstation** - အရင်တုန်းကတော့ ChefDK (Chef Development Kit)ဆိုပြီးတော့ခေါ်ပါတယ်၊ အခုတော့ Chef Workstation ရယ်လို့ ပြောင်းလဲခေါ်ဆိုလာခဲ့ကြပါတယ်။ ဒီတစ်ခုကိုတော့ ကိုယ့် computer ပေါ်မှာ install လုပ်ပြီး Chef server နဲ့တွဲသုံးလို့ရပါတယ်။ Chef server မပါပဲနဲ့လည်း Chef Workstation ကိုပဲ standalone အသုံးပြုချင်လည်း ရပါတယ်။ Chef Workstation ကို install မလုပ်ပဲနဲ့ chef code တွေကို စတင်ပြီးတော့ ရေးလို့မရပါဘူး။ ဥပမာ - ansible-playbook တွေနဲ့ ansible ad-hoc commands တွေကို run ဖို့အတွက် Ansible ကို ကိုယ့်စက်ပေါ်မှာအရင်ဆုံး install လုပ်ရသလိုပဲ၊ chef ကိုသုံးဖို့ရာအတွက် Chef Workstation ကိုကိုယ့်စက်မှာ ပထမဆုံး install လုပ်ရပါတယ်။&#x20;

**Chef Server** - Chef ကိုသုံးတဲ့အခါမှာ သူ့မှာပါတဲ့ feature တွေကိုအကုန်လုံးကို အသုံးပြုနိုင်ဖို့ရာ Chef server လိုပါတယ်။ ကိုယ်တိုင် self-hosted လုပ်လို့ရနိုင်သလို၊ Chef က hosted လုပ်ပေးထားတဲ့ [manage.chef.io](https://manage.chef.io/login) ကိုသုံးမယ်ဆိုလည်းရပါတယ်။ ကိုယ့်ရဲ့ environment ပေါ်မှာမူတည်ပြီးတော့ ရွေးချယ်အသုံးပြုနိုင်ပါတယ်။ Chef Workstation မှာ develop လုပ်ထားတဲ့ Chef code တွေဟာ ဒီအတိုင်းထားလိုက်ရင် locally execute လုပ်ဖို့နဲ့ Rake လိုမျိုး tool တွေကိုသုံးပြီးတော့ target machine တွေမှာသွား run ဖို့အတွက်တော့ အဆင်ပြေပါတယ်။ သို့သော်... Chef Server ကိုသုံးခြင်းအားဖြင့် Chef-Client node တွေကို bootstrap လုပ်ပြီးတော့ Chef Server မှာ register လုပ်ထားလို့ရပါတယ်။ နောင်အခါ လိုအပ်တဲ့ configuration တွေကိုထပ်ပေါင်းထည့်ချင်ရင်လည်း ရှိပြီးတော့ machine state တွေကို Chef Server က manage လုပ်နိုင်စွမ်းရှိပါတယ်။ ဒီတစ်ခုဟာဖြင့် Ansible နဲ့ လုံးဝကို ကွဲထွက်သွားတဲ့ Chef ရဲ့ ထူးခြားချက်တစ်ခုပါ။&#x20;

**Chef-Client** - Chef-client ဆိုတာကတော့ Chef က manage လုပ်တဲ့ node တွေကိုခေါ်ဆိုခြင်းဖြစ်ပါတယ်။ အထက်မှာပြောသလိုမျိုး node အသစ်တစ်ခုကို Chef နဲ့ manage လုပ်ဖို့ရာအတွက် Chef Server နဲ့ bootstrap လုပ်ရပါတယ်။ အဲ့ဒီလိုမျိုး လုပ်တဲ့အခါမှာ agent ကို Chef-client node တွေပေါ်မှာ install လုပ်တယ်။ ဒီ့အတွက်လည်း Chef Server ဟာအဲ့ဒီ chef-client node တွေအတွက် state-aware ဖြစ်တာပါ။ ဒါ့ကြောင့် test and repair လိုမျိုး ကိစ္စတွေဟာ Chef မှာအလွယ်တကူ desired-state ကိုပြန်ရောက်အောင် လုပ်ဆောင်နိုင်တာပဲဖြစ်ပါတယ်။ အလွယ်ပြောရရင် Chef-client ဆိုတာ၊ target သို့မဟုတ် managed node လို့မှတ်ထားနိုင်ပါတယ်။&#x20;

**Cookbooks** - Cookbook ဟာ Chef မှာ အခြေခံအကျဆုံး အစိတ်အပိုင်းတစ်ခုဖြစ်ပါတယ်။ Ansible မှာဆိုရင် Playbook လို့ခေါ်သလို၊ Chef မှာတော့ Cookbook ရယ်လို့ ခေါ်ဆိုကြပါတယ်။ Cookbook name တစ်ခုချင်းစီအောက်မှာမှ recipes, resources, templates, metadata, policyfiles, libraries, spec နဲ့ test ဆိုတဲ့အစိတ်အပိုင်းတွေထပ်ပြီး ပါဝင်တယ်။ အားလုံးကို ခြုံငုံပြီးတော့ ခပ်သွက်သွက်လေးရှင်းရရင်တော့ recipe ဆိုတာက ကိုယ်လုပ်ချင်တဲ့ operation တစ်ခု သို့မဟုတ် တစ်ခုထက်ပိုတဲ့ဟာတွေကို စုပေးထားတဲ့ .rb ဖိုင်လေးတွေဖြစ်ပါတယ်။ Ruby programming ကို backend မှာသုံးထားတဲ့အတွက် recipe တွေကိုရေး တဲ့အခါမှာ Ruby code ဖိုင်လုံးလုံးလျားလျား မဟုတ်သည့်တိုင်အောင်၊ Ruby syntax တွေအများကြီးကိုတွေရမှာပါ။&#x20;

{% code title="chef-repo/cookbooks/linux_node/recipes/nodeinfo.rb" %}
```ruby
template '/tmp/node-info.txt' do
  source 'node-info.txt.erb'
end

file '/tmp/node-info.txt' do
   content node_info
   mode '00755'
end
```
{% endcode %}

Resource ဆိုတာကတော့ Chef မှာ built-in ပါလာတဲ့ resource တွေရှိသလို၊ custom resource တွေကိုလည်း ကိုယ်လိုသလို ထပ်မံထည့်သွင်းရေးလို့ရပါတယ်။ Resource ကိုအခြားနေရာတွေမှာလည်း သုံးလို့ရတဲ့ပုံစံတွေရှိပါသေးတယ်။&#x20;

{% code title="chef-repo/cookbooks/linux_node/resources/webserver.rb" %}
```ruby
property :homepage, String, default: '<h1>Hello world!</h1>'

action :create do
  folder = '/var/www/html/'
  file = 'index.html'

  if platform_family?('debian')
    apt_update
  end

  package 'Install Apache' do
    case node['platform']
    when 'redhat', 'centos'
      package_name 'httpd'
      action :upgrade
    when 'ubuntu', 'debian'
      package_name 'apache2'
      action :upgrade
    end
  end

  service 'Start Apache' do
    case node['platform']
    when 'redhat', 'centos'
      service_name 'httpd'
      action [:enable, :start]
    when 'ubuntu', 'debian'
      service_name 'apache2'
      action [:enable, :start]
    end
  end

  file "#{folder}#{file}" do
    content new_resource.homepage
  end
end

action :delete do
  package 'httpd' do
    action :delete
  end
end
```
{% endcode %}

Templates ဆိုတာကတတော့၊ Ansible မှာ template အတွက် Jinja2 ကိုအသုံးပြုသလိုမျိုးပဲ၊ Chef မှာတော့ Embedded Ruby ဆိုတဲ့ .erb file extension တွေနဲ့ template မှာအသုံးပြုပါတယ်။ Ansible နဲ့ Python မှာ Jinja2 template ကိုသုံးဖူးရင် template တွေဟာ ဘယ်လောက်ထိအရေးပါတယ်ဆိုတာကို တွေ့ရမှာပါ။&#x20;

{% code title="chef-repo/cookbooks/linux_node/templates/node-info.txt.erb" %}
```erb
### This file was automatically generated by Chef ###

Node Information:

Hostname: <%= node['hostname'] %>
FQDN: <%= node['fqdn'] %>

Operating System: <%= node['platform'] %> <%= node['platform_version'] %>
CPU: <%= node['cpu']['cores'] %> x <%= node['cpu']['0']['model_name'] %>
Memory: <%= node['memory']['total'] %> (<%= node['memory']['free'] %> available)

IP Address: <%= node['ipaddress'] %>
```
{% endcode %}

Policyfiles ဆိုတာကတော့ အရင်တုန်းက Chef  မှာ berkfiles လို့ခေါ်ခဲ့ပြီးတော့၊ အခု version အသစ်မှာတော့ policyfiles လို့ပြောင်းလဲခေါ်ဆိုလာပါတော့တယ်။ Policyfiles တွေဟာ wrapper cookbooks တွေသုံးတဲ့အခါမှာ dependencies တွေကို manage လုပ်ဖို့အတွက် အသုံးပြုတဲ့ နေရာပါ။ ဥပမာ supermarket ကို default\_source အနေနဲ့ သတ်မှတ်ပေးတဲ့ ပုံနဲ့ အခြားသော အစိတ်အပိုင်းတွေကို အောက်မှာပြထားတဲ့ ကိုယ်က သတ်မှတ်ပေးလို့ရပါတယ်။&#x20;

{% code title="chef-repo/cookbooks/linux_node/policyfiles/nodeinfo.rb" %}
```ruby
name 'linux_node'

default_source :supermarket

run_list 'linux_node::default'
run_list 'linux_node::nodeinfo'

cookbook 'linux_node', path: '..'
```
{% endcode %}

Chef မှာရှိပြီးသား Ruby class တွေအပြင်ပိုပြီးတော့ အသုံးပြုချင်တဲ့ use case ရှိရင် Libraries တွေကိုအသုံးပြုပြီးတော့ extend လုပ်လို့ရပါတယ်။ Resource ကိုအပေါ်မှာ ပြထားသလို အသုံးပြုချင်ရင်ရသလိုပဲ၊ libraries တွေကိုလည်း အောက်မှာပြထားတဲ့အတိုင်း အသုံးပြုလို့ရပါတယ်။&#x20;

{% code title="chef-repo/cookbooks/linux_node/libraries/node_info.rb" %}
```ruby
# libraries/node_info.rb
module Node
  module SystemInfo
    def node_info
      # Declare variables
      hostname = node['hostname']
      fqdn = node['fqdn']
      platform = node['platform']
      platform_version = node['platform_version']
      cpu_cores = node['cpu']['cores']
      cpu_type = node['cpu']['0']['model_name']
      memory_total = node['memory']['total']
      memory_free = node['memory']['free']
      ipaddress = node['ipaddress']

      "\n
      Hostname: #{hostname}
      FQDN: #{fqdn}\n
      Operating System: #{platform.capitalize()} #{platform_version}
      CPU: #{cpu_cores} x #{cpu_type}
      Memory: #{memory_total} (#{memory_free} available)\n
      IP Address: #{ipaddress}\n"
    end
  end
end

Chef::Recipe.include(Node::SystemInfo)
Chef::Resource.include(Node::SystemInfo)
```
{% endcode %}

Cookbook မှာနောက်ဆုံး အရေးကြီးတဲ့ spec နဲ့ test ကတော့ testing အတွက်အသုံးပြုပါတယ်။ နောက်အပိုင်းတွေရေးတဲ့ အခါကြရင် Chef ရဲ့ cookbook တွေကို အစကနေပြီးတော့ တည်ဆောာက်ပုံနဲ့ Test Kitchen နဲ့ InSpec ကိုအသုံးပြုပုံအသေးစိတ်ကို ဆက်လက်ရှင်းပါ့မယ်။ အခုဒီနေရာမှာတော့... Cookbook ရဲ့ ပါဝင်တဲ့ အစိတ်အပိုင်းအချို့နဲ့ code sample တွေကို မျက်လုံးထဲမြင်စေချင်လို့ တစ်ခုချင်းစီပြထားပေးပါတယ်။&#x20;

{% code title="chef-repo/cookbooks/linux_node/test/integration/default/nodeinfo_test.rb" %}
```ruby
# InSpec test for recipe linux_node::nodeinfo

# The InSpec reference, with examples and extensive documentation, can be
# found at https://www.inspec.io/docs/reference/resources/

filename = 'node-info.txt'
folder = '/tmp/'

describe file("#{folder}#{filename}") do
  it { should exist }
  its('type') { should cmp 'file' }
  it { should be_file }
  it { should_not be_directory }
  its('content') { should_not be nil }
  its('mode') { should cmp '00755' }
end

```
{% endcode %}

{% code title="chef-repo/cookbooks/linux_node/spec/unit/recipes/nodeinfo_spec.rb" %}
```ruby
#
# Cookbook:: linux_node
# Spec:: nodeinfo
#
# Copyright:: 2020, The Authors, All Rights Reserved.

require 'spec_helper'

describe 'linux_node::nodeinfo' do

  context 'When all attributes are default, on Ubuntu 20.04' do

    let(:chef_run) { ChefSpec::SoloRunner.new(platform: 'ubuntu', version: '20.04').converge(described_recipe) }

    it 'creates a template with the default action' do
      expect(chef_run).to create_template('/tmp/node-info.txt')
      expect(chef_run).to_not create_template('/tmp/not-node-info.txt')
    end
  
  end

  context 'When all attributes are default, on CentOS 8' do

    let(:chef_run) { ChefSpec::SoloRunner.new(platform: 'centos', version: '8').converge(described_recipe) }

    it 'creates a template with the default action' do
      expect(chef_run).to create_template('/tmp/node-info.txt')
      expect(chef_run).to_not create_template('/tmp/not-node-info.txt')
    end

  end

end

```
{% endcode %}

အခုဆိုရင် Chef ရဲ့ အရေးကြီးဆုံး Chef Architecture ဖြစ်တဲ့ Chef Workstation, Chef Server နဲ့ Chef-Client ဆိုတဲ့  အစိတ်အပိုင်းတွေရယ်။ Cookbook တစ်ခုကိုတည်ဆောက်တဲ့ အခါပါဝင်တဲ့အစိတ်အပိုင်းတွေရယ်ကို မျက်စိထဲမှာမြင်လာအောင် code sample တွေနဲ့အရင်ဆုံးပြထားပါတယ်။ ဘယ်လိုမျိုး အသုံးပြုလဲဆိုတဲ့အကြောင်းနဲ့ Cookbook တစ်ခုချင်းစီ အသုံးပြုတဲ့ပုံစံမျိုး ကိုအသေးစိတ် ဆက်ပြီးတော့ ရေးချင်ပါတယ်။&#x20;
