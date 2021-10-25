Vagrant.configure("2") do |config|
  config.vm.provision "ansible", type: "shell",
    inline: "echo Provisioning..."

  config.vm.define "centos7" do |machine|
    machine.vm.box = "generic/centos7"
  end
  config.vm.define "centos8" do |machine|
    machine.vm.box = "generic/centos8"
  end
  config.vm.define "fedora33" do |machine|
    machine.vm.box = "bento/fedora-33"
  end
  config.vm.define "fedora34" do |machine|
    machine.vm.box = "bento/fedora-34"
  end
  config.vm.define "ubuntu1804" do |machine|
    machine.vm.box = "bento/ubuntu-18.04"
  end
  config.vm.define "ubuntu2004" do |machine|
    machine.vm.box = "bento/ubuntu-20.04"
  end
  config.vm.define "ubuntu2110" do |machine|
    machine.vm.box = "ubuntu/impish64"
  end
  config.vm.define "debian10" do |machine|
    machine.vm.box = "bento/debian-10"
  end
  config.vm.define "debian11" do |machine|
    machine.vm.box = "bento/debian-11"
  end
  config.vm.define "opensuse15" do |machine|
    machine.vm.box = "generic/opensuse15"
  end
  config.vm.define "opensusetumbleweed" do |machine|
    machine.vm.box = "opensuse/Tumbleweed.x86_64"
  end
  config.vm.define "arch" do |machine|
    machine.vm.box = "generic/arch"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo pacman -Syu --noconfirm && sudo pacman -Sy archlinux-keyring python --noconfirm"
  end
  config.vm.define "alpine312" do |machine|
    machine.vm.box = "generic/alpine312"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo apk add python3"
  end
  config.vm.define "alpine313" do |machine|
    machine.vm.box = "generic/alpine313"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo apk add python3"
  end
  config.vm.define "alpine314" do |machine|
    machine.vm.box = "generic/alpine314"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo apk add python3"
  end
  config.vm.define "freebsd12" do |machine|
    machine.vm.box = "generic/freebsd12"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo pkg install -y python3"
  end
  config.vm.define "freebsd13" do |machine|
    machine.vm.box = "generic/freebsd13"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo pkg install -y python3"
  end
  config.vm.define "openbsd" do |machine|
    machine.vm.box = "generic/openbsd6"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo pkg_add -v python-3.9.7"
  end
  config.vm.define "netbsd8" do |machine|
    machine.vm.box = "generic/netbsd8"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo pkgin -y update && pkgin -y install python38 mozilla-rootcerts && if [ ! -f /usr/pkg/etc/openssl/certs/ca-certificates.crt ]; then mozilla-rootcerts install ; fi"
  end
  config.vm.define "netbsd9" do |machine|
    machine.vm.box = "generic/netbsd9"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Installing python...' && sudo pkgin -y update && pkgin -y install python38 mozilla-rootcerts && if [ ! -f /etc/openssl/certs/ca-certificates.crt ]; then mozilla-rootcerts install ; fi"
  end
  config.vm.define "dragonflybsd" do |machine|
    machine.vm.box = "generic/dragonflybsd6"
    machine.vm.provision "ansible", type: "shell",
      preserve_order: true,
      inline: "echo 'Cleaning up...' && sudo hammer prune-everything / && echo 'PKG_ENV { SSL_NO_VERIFY_PEER=1 }' | sudo tee -a /usr/local/etc/pkg.conf && sudo pkg remove -y git-lite"
  end
  config.vm.define "openindiana" do |machine|
    machine.vm.box = "openindiana/hipster"
  end
  config.vm.define "omniosce" do |machine|
    machine.vm.box = "storvix/omniosce-r151038"
    machine.vm.synced_folder ".", "/vagrant", disabled: true
    machine.ssh.username = 'admin'
    machine.ssh.password = 'admin'
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbooks/playbook.yml"
    ansible.compatibility_mode = "2.0"
    ansible.verbose = '-vvv'
    ansible.host_vars = {
      "freebsd12" => { "ansible_python_interpreter" => "/usr/local/bin/python3" },
      "freebsd13" => { "ansible_python_interpreter" => "/usr/local/bin/python3" },
      "openbsd" => { "ansible_python_interpreter" => "/usr/local/bin/python3.9" },
      "netbsd8" => { "ansible_python_interpreter" => "/usr/pkg/bin/python3.8" },
      "netbsd9" => { "ansible_python_interpreter" => "/usr/pkg/bin/python3.8" }
    }
  end

end
