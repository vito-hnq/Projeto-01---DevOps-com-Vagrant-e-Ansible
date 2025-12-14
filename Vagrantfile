Vagrant.configure("2") do |config|
  config.vm.box = "debian/bookworm64"

  # ===================== ARQ =====================
  config.vm.define "arq" do |arq|
    arq.vm.hostname = "arq.tyrone.victor.devops"
    arq.vm.network "private_network", ip: "192.168.56.123"
  end

  # ===================== DB =====================
  config.vm.define "db" do |db|
    db.vm.hostname = "db.tyrone.victor.devops"
    db.vm.network "private_network", ip: "192.168.56.102"
  end

  # ===================== APP1 =====================
  config.vm.define "app1" do |app1|
    app1.vm.hostname = "app1.tyrone.victor.devops"
    app1.vm.network "private_network", ip: "192.168.56.101"
  end

  # ===================== APP2 =====================
  config.vm.define "app2" do |app2|
    app2.vm.hostname = "app2.tyrone.victor.devops"
    app2.vm.network "private_network", ip: "192.168.56.103"
  end

  # ===================== CLI =====================
  config.vm.define "cli" do |cli|
    cli.vm.hostname = "cli.tyrone.victor.devops"
    cli.vm.network "private_network", ip: "192.168.56.104"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.inventory_path = "inventory.ini"
    ansible.playbook = "playbooks/site.yml"
  end
end
