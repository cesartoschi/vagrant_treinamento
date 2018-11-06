Vagrant.configure("2") do |config|

  config.vm.provision "shell", inline: <<-SHELL
    mkdir -p /root/.ssh
    echo "127.0.0.1 localhost
192.168.60.10 devops devops.dexter.com.br
192.168.60.11 docker docker.dexter.com.br
192.168.60.12 default default.dexter.com.br
192.168.60.13 automation automation.dexter.com.br" > /etc/hosts
    echo "-----BEGIN RSA PRIVATE KEY-----
MIIEowIBAAKCAQEAxe0u3mstnpAF86PBA7MWS7JkwH2fu+VliWpdmxqkMC8bsEQP
bgIHqMMNAhaGOKj5UcTCMR3by+78pbWXjTh8eR8pDK0g3Ro3yexO0N/NrOsHyCpg
8VOcAsG8pkp9HdIhDUlLpGNtQfc8i0pFtOweJhDdA0OePcnK/MUz0QHT8bQartq0
kH728P3DCWYg6MWjYrM8wGWOBUOnZRjCgB/PFfKi/I+WCCVtEyFtvoyLFIXDEATW
v07Pg9a1PMQJnCNicmsVMc79AGQ6fIUfBHTNbcbsXPHnVIRyoJ/WzYM1mZnMncWF
67qsCW1GZmilsG5GDosdpAjDTPgzupv8Ag9dcwIDAQABAoIBAHZ3IkhqKiHv3kAX
0V0fgcbI/djg2AyknwOCsIg3h/J3H8F+2yVi/aabKFwJk0iyipfQhtLTJk2Hu5yL
dixGlOoCJpW5wiPUn3OyhvIqInbPLhc2llObUZOs1fdKOlzw+mtzZVz9TdXf31MX
n2VMtjbefQqJHFurPl3QwtTknTDbKBrpvTF7bAePT/8jx1mU3ScB6eZ8OEy3ByuQ
vByzPENDPKZOoNaAe7nXfJtna++0eFYJ1awaN0MCTcxYKO/DRs68L95HI8QA8U80
stXD2tyHIMWhpun9qcfE2awyWIJEEFDJ/6uwq68oDIPIqR6XZFfZNmyiog9berjP
WRfHgsECgYEA7IPTqHpQD7h3zmfFm1FhQ7ZKxXFhtDXINrqmQzeoz2nUDInEEiht
fBCyneMBKkK0EGz6ASKAXNw0isGob6hxkA+422zkryHgJyTwG3rHth7ApeaMOUVj
v7NT69H18/Tg9lnMoDGSUU6J7ZPJHhJRR9u9wA6gKgd/qjBNQ04e7XECgYEA1juD
kWkg1fIik4RuDrMgnPFsT4WWSE6yZ7vmLyg0AbSOAUYK3WTinzGi1if651T+qeNq
nbVzTlJPyTIk7PQmaqt1MBt10qHogalUjAMtkDmk/GkKqSqtjPlJqdfuY5bUkeP+
ozNFKl8T+6Q9Xlms4Nx5tbqF77Sd0JwO/Ieb1yMCgYAOHjBcNjDhP1mncHpTMyBj
MlZ0QrhaUXuKCMoz6PaiquaFeRPDIbanWTfQROSk6SZmdJrXxn9zC5H3Vmf/gkaF
Gusl7fIYoiUHMSVD/qg9LsjBHmnwYTv7DXFM+lN8JHnpOqMETPE2+UEydUfkC6Pe
bjd9Z2IYICp2tjtmcRtXgQKBgFgir+QYzgt2zEbISsb9ZsNqh1bH7KXeyoLmyLJJ
5et1rp5ThJDEun8n2ogkdpLJYuPdzbUIO2HTd0Ocv5hEcbGczF94TKbVOWRul3vq
qsoVDQ1S4bHq/u9qd6XKUibinJ1QoSffJetipkP2s9CnL/pqeiALlqKhOfPi4D+A
QtrlAoGBAOB9HYZP7Y6CPhgCcp0g+IeIP4gzBIvpE5FXFWELcz172rEYSsbG4+Er
fSwJV/0M2c/U6jn62AVQkgVF7lbaqA04dbSDcJ738mYbr963G+ekzMWDs+9KRXqg
FXid6lWlGcrt/ddLSuYvSB5hFZ2EIBtZzH3EzvU5Ay3gsMfCdmnx
-----END RSA PRIVATE KEY-----" > /root/.ssh/id_rsa
    echo "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDF7S7eay2ekAXzo8EDsxZLsmTAfZ+75WWJal2bGqQwLxuwRA9uAgeoww0CFoY4qPlRxMIxHdvL7vyltZeNOHx5HykMrSDdGjfJ7E7Q382s6wfIKmDxU5wCwbymSn0d0iENSUukY21B9zyLSkW07B4mEN0DQ549ycr8xTPRAdPxtBqu2rSQfvbw/cMJZiDoxaNiszzAZY4FQ6dlGMKAH88V8qL8j5YIJW0TIW2+jIsUhcMQBNa/Ts+D1rU8xAmcI2JyaxUxzv0AZDp8hR8EdM1txuxc8edUhHKgn9bNgzWZmcydxYXruqwJbUZmaKWwbkYOix2kCMNM+DO6m/wCD11z" > /root/.ssh/authorized_keys 
    chmod 600 /root/.ssh/id_rsa
  SHELL

#DEFAULT
  config.vm.define "default" do |default|
    default.vm.hostname = "default"
    default.vm.box = "centos/7"
    default.vm.network "private_network", ip: "192.168.60.12", dns: "8.8.8.8"
    default.vm.synced_folder '.', '/vagrant', disabled: true
 
  default.vm.provision "shell", inline: <<-SHELL
    yum install ansible -y
  SHELL
  end

#DEVOPS
  config.vm.define "devops" do |devops|
    devops.vm.hostname = "devops"
    devops.vm.box = "centos/7"
    devops.vm.network "private_network", ip: "192.168.60.10", dns: "8.8.8.8"
    devops.vm.synced_folder '.', '/vagrant', disabled: true
  end

#DOCKER
  config.vm.define "docker" do |docker|
    docker.vm.hostname = "docker"
    docker.vm.box = "centos/7"
    docker.vm.network "private_network", ip: "192.168.60.11", dns: "8.8.8.8"
    docker.vm.synced_folder '.', '/vagrant', disabled: true
  end

#AUTOMATION
  config.vm.define "automation" do |automation|
    automation.vm.hostname = "automation"
    automation.vm.box = "ubuntu/xenial64"
    automation.vm.network "private_network", ip: "192.168.60.13", dns: "8.8.8.8"
    automation.vm.synced_folder '.', '/vagrant', disabled: true
  
  automation.vm.provision "shell", inline: <<-SHELL
    apt install python -y
  SHELL

  config.vm.provider "virtualbox" do |automation|
    automation.memory = "3072"
  end

  end 
end
