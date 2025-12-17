Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"
  config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 512
    vb.cpus = 1
    vb.linked_clone = true
  end

  # Trigger seguro para remover DHCP do VirtualBox
  config.trigger.before :up do |trigger|
    trigger.name = "Desabilitar DHCP do VirtualBox"
    trigger.run = {
      inline: "bash -c 'VBoxManage dhcpserver remove --netname HostInterfaceNetworking-vboxnet0 || true'"
    }
  end

  # ===================== ARQ =====================
  config.vm.define "arq" do |arq|
    arq.vm.hostname = "arq.tyrone.victor.devops"
    arq.vm.network "private_network",
      ip: "192.168.56.123",
      mac: "080027AA0123"

    arq.vm.provider "virtualbox" do |vb|
      vb.customize ["createhd", "--filename", "arq-disk1.vdi", "--size", 10240]
      vb.customize ["createhd", "--filename", "arq-disk2.vdi", "--size", 10240]
      vb.customize ["storageattach", :id, "--storagectl", "SATA Controller",
                     "--port", 1, "--device", 0, "--type", "hdd",
                     "--medium", "arq-disk1.vdi"]
      vb.customize ["storageattach", :id, "--storagectl", "SATA Controller",
                     "--port", 2, "--device", 0, "--type", "hdd",
                     "--medium", "arq-disk2.vdi"]
    end
  end

  # ===================== DB =====================
  config.vm.define "db" do |db|
    db.vm.hostname = "db.tyrone.victor.devops"
    db.vm.network "private_network",
      type: "dhcp",
      mac: "080027DB0102"
  end

  # ===================== APP1 =====================
  config.vm.define "app1" do |app|
    app.vm.hostname = "app1.tyrone.victor.devops"
    app.vm.network "private_network",
      type: "dhcp",
      mac: "080027BB0103"
  end

  # ===================== CLI =====================
  config.vm.define "cli" do |cli|
    cli.vm.hostname = "cli.tyrone.victor.devops"
    cli.vm.network "private_network",
      type: "dhcp",
      mac: "080027CC0104"
  end

  # ===================== ANSIBLE =====================
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/site.yml"
  end
end

