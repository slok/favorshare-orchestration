# Vagrantfile

VAGRANTFILE_API_VERSION = "2"

box = 'ubuntu/trusty64'
hostname = 'sandbox.favorshare'

machines = [
  {
    "hostname"=> "1.web." + hostname,
    "ip"=> "192.168.100.41",
    "box"=> box,
    "mem"=> 512,
    "cpu"=> 2,
    "ports"=> [
      [80, 10080], # Nginx
      [8000, 18000], # Uwsgi
    ]
  },
  {
    "hostname"=> "2.web." + hostname,
    "ip"=> "192.168.100.42",
    "box"=> box,
    "mem"=> 512,
    "cpu"=> 2,
    "ports"=> [
      [80, 20080], # Nginx
      [8000, 28000], # Uwsgi
    ]
  },
  {
    "hostname"=> "1.lb." + hostname,
    "ip"=> "192.168.100.43",
    "box"=> box,
    "mem"=> 512,
    "cpu"=> 2,
    "ports"=> [
      [80, 30080], # LB entrance!
    ]
  },
  {
    "hostname"=> "1.db.master." + hostname,
    "ip"=> "192.168.100.44",
    "box"=> box,
    "mem"=> 512,
    "cpu"=> 2,
    "ports"=> [
      [5432, 45432], # database
    ]
  }
]

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  machines.each do |i|
    config.vm.define i["hostname"] do |machine|
      machine.vm.box = i["box"]
      machine.vm.host_name = i["hostname"]
      machine.vm.network :private_network, ip: i["ip"]

      i["ports"].each do |port|
        machine.vm.network :forwarded_port, guest: port[0], host: port[1]
      end

      machine.vm.provider :virtualbox do |vb|
        vb.customize [
          "modifyvm", :id,
          "--memory", i["mem"],
          "--cpus", i["cpu"],
          "--ioapic", "on",
        ]
      end
    end
  end
end