Vagrant.configure('2') do |config|

    config.ssh.private_key_path = '/home/ena/.ssh/vagrant_rsa'
    config.vm.hostname = 'ubuntu-20.04-px'

    config.vm.provider :proxmox do |proxmox|
        # Useful for debugging unencrypted request/response with stunnel+Wireshark
        #proxmox.endpoint = 'http://localhost:8006/api2/json'
        proxmox.endpoint = 'https://192.168.0.100:8006/api2/json'
        proxmox.user_name = 'root@pve'
        proxmox.password = 'Joshuaacdc8'
        proxmox.vm_id_range = 900..910
        proxmox.vm_name_prefix = 'vagrant_'
        proxmox.openvz_os_template = 'local:vztmpl/centos-7-base_20161225_amd64.tar.xz'
        proxmox.vm_type = :lxc
        proxmox.vm_memory = 1024
        proxmox.vm_storage = 'local-lvm'
        proxmox.vm_disk_size = '50G'
    end

    config.vm.define :box, primary: true do |box|
        box.vm.box = 'dummy'
        box.vm.network :public_network, ip: '192.168.0.112', interface: 'eth0', bridge: 'vmbr0', gw: '192.168.0.1'
    end

end
