---
ID: 11085
post_title: 'Setting up Chef <Work in Progress>'
author: Dennis
post_date: 2014-11-08 11:09:19
post_excerpt: ""
layout: post
permalink: http://dennisseidel.de/setting-up-chef/
published: true
slide_template:
  - default
mfn-post-hide-content:
  - "0"
mfn-post-sidebar:
  - "0"
mfn-post-slider:
  - "0"
mfn-post-love:
  - "0"
dsq_thread_id:
  - "3428675194"
---
<h4>1. First you need to install <a href="http://git-scm.com/">git</a> as your version control system.[TERMINAL]</h4>
OSX: In OSX can install this with xcode .

<code>xcode-select --install</code>
<h4>2. Install wget to download the chef-repo template from the Opscode page[TERMINAL]</h4>
OSX:

<code>cd ~/Downloads
curl -O http://ftp.gnu.org/gnu/wget/wget-1.15.tar.gz
tar -zxvf wget-1.15.tar.gz
cd wget-1.15/
./configure --with-ssl=openssl
make
sudo make install
rm -rf ~/Downloads/wget*</code>
<h4>3. Set up up Github to store and manage your chef-repo and share it with others[TERMINAL]</h4>
<code>ssh-keygen -t rsa -C "den.seidel@gmail.com" #press just enter and when ask give type you passphrase
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
pbcopy &lt; ~/.ssh/id_rsa.pub #copies the key to your clipboard go to github.com and set the key up there
ssh -T git@github.com #test it</code>
<h4>4. Set up chef-repo, download template from Obscode and upload it to github[TERMINAL]</h4>
<code>cd ~/ #go to home directory
wget http://github.com/opscode/chef-repo/tarball/master
tar zvf master -x
mv opscode-chef-repo-f9d4b0c/ chef-repo
cd chef-repo/
git init .
git remote add origin git@github.com:den53/chef-repo.git
git add .
git commit -m "initial commit"
git push -u origin master
</code>

For a deep introduction to git and github I suggest <a href="https://www.udacity.com/course/ud775">https://www.udacity.com/course/ud775</a>
<h4>￼5. Install Chef on your terminal/workstation[TERMINAL]</h4>
This will download Ruby and all the required Ruby gems into /opt/chef/ embedded. By adding the /opt/chef/embedded/bin directory to your .bash_profile, the Chef command-line tools will be available in your shell.
<code>cd ~/chef-repo/
curl -L https://www.opscode.com/chef/install.sh | sudo bash
echo 'export PATH="/opt/chef/embedded/bin:$PATH"'&gt;&gt; ~/.bash_profile &amp;&amp; source ~/.bash_profile</code>
<h4>￼6. Setup a Chef Server on Obscode (alternatively you can set up your private hosted Chef server)[SERVER]</h4>
Go to Hosted Chef (https://www.getchef.com/chef/choose-your-version/) and sign up. After registering your account, it is time to prepare your organization to be used with <a href="https://github.com/den53/chef-repo">your chef-repo</a> repository.

Go to http://manage.opscode.com/organizations login and download the validation key and configuration file. Now regenerate the validation key for your organization and save it as &lt;your- organization-short-name&gt;.pem in the .chef directory inside your chef-repo repository. Also regenerate your user pulic key and save it in the .chef directory.
<h4>￼7. Create your cookbook[TERMINAL]</h4>
<code>knife cookbook create my_cookbook</code>
<h4>￼8. Upload your new cookbook to the Chef Server[TERMINAL]</h4>
<code>knife cookbook upload my_cookbook</code>

You can set up a node[NODE] via Vagrant here my example Vegrantfile:
<code>Vagrant.configure("2") do |config|
config.vm.box = "opscode-centos-7.0"
config.vm.box_url = "http://opscode-vm-bento.s3.amazonaws.com/vagrant/virtualbox/opscode_centos-7.0_chef-provisionerless.box"
config.omnibus.chef_version = :latest
config.vm.provision :chef_client do |chef|
chef.provisioning_path = "/etc/chef"
chef.chef_server_url = "https://api.opscode.com/organizations/dennisseidel"
chef.validation_key_path = "~/chef-repo/.chef/dennisseidel-validator.pem"
chef.validation_client_name = "dennisseidel-validator"
chef.node_name = "server"
end
end</code>
<h4>￼9. Add the cookbook to your node's (here: server1) run list[TERMINAL]:</h4>
<code>knife node run_list add server1 recipe[my_cookbook]</code>
<h4>10. Run Chef Client on your node [NODE]</h4>
<code>sudo chef-client</code>
<h4>11. Install a community cookbook (iptables) [TERMINAL]</h4>
<code>cd ~/chef-repo/
knife cookbook site install iptables</code>
<h4>11. Upload cookbooks to chef server [TERMINAL]</h4>
<code>knife cookbook upload --all</code>

<h4>12. Manage cookbook dependencies with Berkshelf</h4>
<code>cd ~/chef-repo/
vim Gemfile
bundle install</code>
Gemfile:
<code>source 'https://rubygems.org'
gem 'berkshelf'</code>

Edit your cookbook's metadata:
<code>vim ~/chef-repo/cookbooks/my_cookbook/metadata.rb</code>
<code>...
depends 'chef-client'
depends 'yam'
depends 'ntp'</code>

Edit your cookbook's default recipe:
<code>vim ~/chef-repo/cookbooks/my_cookbook/recipes/default.rb</code>
<code>include_recipe "chef-client"
include_recipe "yam"
include_recipe "ntp"</code>

Create your Berksfile:
<code>cd ~/chef-repo/
vim Berksfile</code>
<code>site :opscode

metadata</code>