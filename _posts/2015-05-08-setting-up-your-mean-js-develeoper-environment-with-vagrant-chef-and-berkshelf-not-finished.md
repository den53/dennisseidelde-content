---
ID: 11244
post_title: >
  Setting up your MEAN.js Develeoper
  Environment with Vagrant, Chef and
  Berkshelf
author: Dennis
post_date: 2015-05-08 07:22:46
post_excerpt: ""
layout: post
permalink: >
  http://dennisseidel.de/setting-up-your-mean-js-develeoper-environment-with-vagrant-chef-and-berkshelf-not-finished/
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
  - "3746502003"
---
<p>First you have to get started developing your Infrastructure Environment. An Up to Date Guide can be found at <a href="https://blog.safaribooksonline.com/2014/11/27/opscode-chef-vagrant-test-kitchen/">safaribooksonline.com</a>. The following procedure will get your local workstation configured and ready to develop cookbooks with Test Kitchen, Vagrant and Chef-zero.  Note that this is not a tutorial on how to write cookbooks.</p>

<blockquote>
<p>This is just a short discription on the progress I made and not complete. Since I switch from the MEAN.js stack to the jHistper Stack (Java (Spring) in the Backend, AngularJS and Bootstrap in the Frontend, and a variety of databases) I won&#39;t continue this. Hope this still helps someone.</p>
</blockquote>

<h2 id="the-tools">The Tools</h2>

<p><strong>Vagrant</strong> – We use Vagrant and Virtualbox to test our cookbook code and run our tests on our local workstations.  The creator of Vagrant wrote <a href="https://www.safaribooksonline.com/library/view/vagrant-up-and/9781449336103/">the definitive guide</a> for us all.</p>

<p><strong>Test Kitchen</strong> – Test Kitchen is the tool we use to manage our Vagrant configurations, configure our environment to mirror Production in a meaningful way and run our tests.</p>

<p><strong>Chef-Zero</strong> – Chef-Zero is a lightweight local Chef Server that our testing VMs use to mimic our live Chef environment.</p>

<p><strong>ChefDK</strong> – The Chef Development Kit provided by Opscode bundles various Chef tools together.  The beauty of ChefDK is that it comes with an embedded Ruby environment and the necessary Ruby Gems required by the tools.  This is a great improvement if you’ve ever had to deal with pre-ChefDK local Ruby/RVM configurations, fluctuating gem dependancies and breaking changes between tools.</p>

<h2 id="getting-vagrant-chefdk-and-tools">Getting Vagrant, ChefDK and Tools</h2>

<h3 id="chefdk-installation">ChefDK Installation</h3>

<p>First, download and install ChefDK from <a href="https://downloads.getchef.com/chef-dk">https://downloads.getchef.com/chef-dk</a>.  ChefDK comes with chef-client, Berkshelf, Test Kitchen, ChefSpec, Foodcritic and more.</p>

<h3 id="vagrant-installation-and-configuration">Vagrant Installation and Configuration</h3>

<p>Next, install Vagrant. Head over to <a href="https://www.vagrantup.com/downloads.html">https://www.vagrantup.com/downloads.html</a> and download and install the appropriate package for your system.</p>

<p>Once you have Vagrant installed you’ll run the following commands in your (bash) shell to install the supporting plug-ins that we need to integrate Vagrant and Chef.</p>

<pre><code class="lang-shell">vagrant plugin install vagrant-berkshelf
vagrant plugin install vagrant-omnibus
vagrant plugin install vagrant-chef-zero
vagrant plugin install vagrant-vbguest
</code></pre>

<p>After installing these, you should logout of your shell and relaunch it to pickup the new environment variables.</p>

<h3 id="virtualbox-installation-and-setup">Virtualbox Installation and Setup</h3>

<p>Next, download and install VirtualBox from <a href="https://www.virtualbox.org/wiki/Downloads">https://www.virtualbox.org/wiki/Downloads</a>.</p>

<p>Follow the directions for your platform but <em>skip</em> the VMWare portion and go to the <strong>Test Your Setup</strong> section below if you’ve opted to use Virtualbox.</p>

<h3 id="alternately-vmware-installation-and-setup">Alternately, VMWare installation and Setup</h3>

<p>(only do this if you use VMWare rather than Virtualbox)</p>

<p>Download and install VMWare from the web site and have your Vagrant VMWare license handy.  You need to purchase the Vagrant VMWare integration license from HashiCorp (the company that makes Vagrant).</p>

<p>Copy your Vagrant VMWare license to <code>~/.vagrant.d/vmware-license.lic</code> then follow the steps for your specific setup:</p>

<p>For <strong>VMWare Workstation</strong>, add the following to your <code>~/.bashrc</code> file ( or <code>~/.bash_profile</code> on OS X):</p>

<pre><code class="lang-shell">export VAGRANT_DEFAULT_PROVIDER=vmware_workstation
</code></pre>

<p>Then run:</p>

<pre><code class="lang-shell">vagrant plugin install vagrant-vmware-workstation
vagrant plugin license vagrant-vmware-workstation ~/.vagrant.d/vmware-license.lic
</code></pre>

<p>For <strong>VMWare Fusion</strong>, add the following to your <code>~/.bashrc</code> file ( or <code>~/.bash_profile</code> on OS X):</p>

<pre><code class="lang-shell">export VAGRANT_DEFAULT_PROVIDER=vmware_workstation
</code></pre>

<p>Then run: </p>

<pre><code class="lang-shell">vagrant plugin install vagrant-vmware-workstation
vagrant plugin license vagrant-vmware-workstation ~/.vagrant.d/vmware-license.lic
</code></pre>

<p>lly, everyone using VMWare should reboot their machine and launch VMWare for the first time, accepting the license agreement and allowing it to initialize itself once. Do this before running Vagrant. FYI: Vagrant has plans to consolidate Fusion and Workstation at some point in the near future.</p>

<p>Finally, everyone using VMWare should reboot their machine and launch VMWare for the first time, accepting the license agreement and allowing it to initialize itself once. Do this before running Vagrant. FYI: Vagrant has plans to consolidate Fusion and Workstation at some point in the near future.</p>

<h3 id="prepare-chef-tools">Prepare Chef Tools</h3>

<p>As you work more with Chef, you will eventually run into repositories that depend on Chef recipes that require your a broad range of tools to be available and configured on your workstation.  Run through the following steps now so they are available when you need them.</p>

<h3 id="configure-knife">Configure Knife</h3>

<p>(do this only if you don’t have a <code>knife</code> configuration already)
Setup Knife and accept the defaults:</p>

<pre><code class="lang-shell">knife configure
</code></pre>

<p>You must place your validation key in the following location before generating instance data with Knife:</p>

<pre><code class="lang-shell">/etc/chef-server/chef-validator.pem
</code></pre>

<h4 id="create-pem-file">Create .pem File</h4>

<p>Create a .pem for Chef Zero to use when faking Chef server for local configuration.</p>

<pre><code class="lang-shell">openssl genrsa 2048 &gt; ~/.chef/&lt;username from knife configure&gt;.pem
</code></pre>

<h3 id="test-your-new-setup">Test Your New Setup</h3>

<p>You should now create a temporary directory locally for Vagrant VMs and then test that you can create a new Vagrant project.  There are many GitHub projects with Vagrant file templates.  I recommend that you read up on Vagrant and create your own simple configuration file but if you want to test you can use the one in the next step.</p>

<p>Create an empty directory (<code>~/vagrant_vm</code>, say) for the configuration.  This location will contain a <code>Vagrantfile</code> and will eventually contain the running VM as well.</p>

<pre><code class="lang-shell">you@workstation$ mkdir ~/vagrant_vm
you@workstation$ cd ~/vagrant_vm
</code></pre>

<h3 id="preparing-your-vagrantfile">Preparing your Vagrantfile</h3>

<p>Copy a Vagrant file from a GitHub repo that suits you and put it in a new file called Vagrantfile in the ~/vagrant_vm directory. (You must name the file Vagrantfile. You cannot always leave it the same name as it is in GitHub.)  You can find some generic Vagrantfile examples and the ssh key for the images here: <a href="https://github.com/patrickdlee/vagrant-examples">https://github.com/patrickdlee/vagrant-examples</a>.</p>

<p>Or you can use the example one below:</p>

<pre><code class="lang-shell">#Quick vagrant file for testing
#
Vagrant::Config.run do |config|
  config.vm.box = &#39;precise32&#39;
  config.vm.box_url = &#39;http://files.vagrantup.com/precise32.box&#39;
end
</code></pre>

<h3 id="using-the-virtual-machine">Using the Virtual Machine</h3>

<p>Next, launch the VM from the ~/vagrant_vm directory using vagrant up:</p>

<pre><code class="lang-shell">you@workstation$ vagrant up
</code></pre>

<p>There will be lots of output and once the machine has booted you can ssh to it.</p>

<pre><code class="lang-shell">you@workstation$ vagrant ssh
</code></pre>

<p>Vagrant exports <code>~/vagrant_vm</code> from your local your local machine to the VM.  Check that you see the the Vagrantfile and .vagrant directories in the VM by running:</p>

<pre><code class="lang-shell">sbo@linux:~$ ls -la /vagrant
total 16drwxrwxr-x  1 sbo  sbo  4096 Oct 10 16:03 .
drwxr-xr-x 23 root root 4096 Oct 10 16:05 ..
drwxrwxr-x  1 sbo  sbo  4096 Oct 10 13:56 .vagrant
-rw-r--r--  1 sbo  sbo  1150 Oct 10 16:03 Vagrantfile
</code></pre>

<p>Exit from the VM</p>

<pre><code class="lang-shell">sbo@linux:~$ exit
</code></pre>

<p>Source: <a href="http://stackengine.com/devops-delight-chef-dk-chef-zero-vagrant/">http://stackengine.com/devops-delight-chef-dk-chef-zero-vagrant/</a></p>

<h3 id="authoring-a-cookbook">Authoring a Cookbook</h3>

<p>Each of the individual parts is now installed and shown to work. So lets configure a machine using chef. To do this we will:</p>

<ul>
<li>Write a cookbook to install some of our favorite packages that should be on every machine</li>
<li>Run Foodcritic</li>
</ul>

<h4 id="scaffolding-a-cookbook-with-berkshelf">Scaffolding a Cookbook with Berkshelf</h4>

<p>Berkshelf is the “package manager” for Chef cookbooks. It is also the standard way to scaffold a cookbook with ChefDK.</p>

<p>Generate a Berksfile in a pre-existing cookbook
$ cd cookbooks
$ berks init .</p>

<p><a href="https://www.youtube.com/watch?v=0sPuAb6nB2o">https://www.youtube.com/watch?v=0sPuAb6nB2o</a></p>