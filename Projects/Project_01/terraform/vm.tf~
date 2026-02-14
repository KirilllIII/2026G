resource "vkcs_compute_instance" "game01" {
  name = "game01"
  availability_zone = "ME1"
  flavor_name       = "STD3-1-1"
  security_groups   = ["default","ssh"]
  user_data         = file("cloud-init.yml")
  block_device {
    source_type      = "image"
    uuid             = "f5b9db9e-6867-42fd-8940-ff5d869a75db"
    destination_type = "volume"
    volume_size      = 30
    volume_type      = "ceph-ssd"
    delete_on_termination = true
  }
  network {
    port = vkcs_networking_port.game01.id
  }
}

resource "vkcs_networking_port" "game01" {
  name       = "game01"
  network_id = "a6dcfe27-58ed-41ce-9397-d679da4ef011"
  fixed_ip {
    subnet_id = "725469e1-62d9-4ecf-958d-662af9f6fa49"
    ip_address = "192.168.0.1"
  }
}


resource "vkcs_compute_instance" "game02" {
  name = "game02"
  availability_zone = "GZ1"
  flavor_name       = "STD3-1-1"
  security_groups   = ["default","ssh"]
  user_data         = file("cloud-init.yml")
  block_device {
    source_type      = "image"
    uuid             = "f5b9db9e-6867-42fd-8940-ff5d869a75db"
    destination_type = "volume"
    volume_size      = 30
    volume_type      = "ceph-ssd"
    delete_on_termination = true
  }
  network {
    port = vkcs_networking_port.game02.id
  }
}

resource "vkcs_networking_port" "game02" {
  name       = "game02"
  network_id = "a6dcfe27-58ed-41ce-9397-d679da4ef011"
  fixed_ip {
    subnet_id = "725469e1-62d9-4ecf-958d-662af9f6fa49"
    ip_address = "192.168.0.2"
  }
}




resource "vkcs_compute_instance" "game03" {
  name = "game03"
  availability_zone = "MS1"
  flavor_name       = "STD3-1-1"
  security_groups   = ["default","ssh"]
  user_data         = file("cloud-init.yml")
  block_device {
    source_type      = "image"
    uuid             = "f5b9db9e-6867-42fd-8940-ff5d869a75db"
    destination_type = "volume"
    volume_size      = 30
    volume_type      = "ceph-ssd"
    delete_on_termination = true
  }
  network {
    port = vkcs_networking_port.game03.id
  }
}

resource "vkcs_networking_port" "game03" {
  name       = "game03"
  network_id = "a6dcfe27-58ed-41ce-9397-d679da4ef011"
  fixed_ip {
    subnet_id = "725469e1-62d9-4ecf-958d-662af9f6fa49"
    ip_address = "192.168.0.3"
  }

}



resource "vkcs_compute_instance" "haproxy01" {
  name = "haproxy01"
  availability_zone = "ME1"
  flavor_name       = "STD3-1-1"
  security_groups   = ["default","ssh","web"]
  user_data         = file("cloud-init.yml")
  block_device {
    source_type      = "image"
    uuid             = "f5b9db9e-6867-42fd-8940-ff5d869a75db"
    destination_type = "volume"
    volume_size      = 30
    volume_type      = "ceph-ssd"
    delete_on_termination = true
  }
  network {
    port = vkcs_networking_port.haproxy01.id
  }
}

resource "vkcs_networking_port" "haproxy01" {
  name       = "haproxy01"
  network_id = "a6dcfe27-58ed-41ce-9397-d679da4ef011"
  fixed_ip {
    subnet_id = "725469e1-62d9-4ecf-958d-662af9f6fa49"
    ip_address = "192.168.0.4"
  }
}
resource "vkcs_networking_floatingip" "haproxy01_fip" {
  pool    = "ext-net"
  port_id = vkcs_networking_port.haproxy01.id
}
