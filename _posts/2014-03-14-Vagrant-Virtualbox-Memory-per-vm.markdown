---
layout: post
title:  "Vagrant Virtualbox memory per vm"
date:   2014-03-14 16:18:00
categories: vagrant virtualbox vm
---

If you want to set memory settings in Vagrant per vm separately:

{% highlight ruby %}
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "app" do |app|
    app.vm.hostname = "app.example.dev"
    app.vm.box = "precise64"
    app.vm.box_url = "http://files.vagrantup.com/precise64.box"
    app.vm.provider "virtualbox" do |v|
      v.memory = 256
    end
  end

  config.vm.define "queue" do |app|
    app.vm.hostname = "queue.example.dev"
    app.vm.box = "precise64"
    app.vm.box_url = "http://files.vagrantup.com/precise64.box"
    app.vm.provider "virtualbox" do |v|
      v.memory = 512
    end
  end

end
{% endhighlight %}