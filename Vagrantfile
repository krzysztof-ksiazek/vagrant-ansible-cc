Vagrant.configure(2) do |config|

    config.ssh.insert_key = false

    config.vm.define "anscmon" do |anscmon|
        anscmon.vm.box = "hashicorp/precise64"
        anscmon.vm.network "public_network", ip: "10.0.0.200", bridge: 'en1: Wi-Fi 2 (AirPort)'
        anscmon.vm.provider "virtualbox" do |vb|
            vb.memory = "1536"
        end
    end

    config.vm.define "ansnode1" do |ansnode1|
        ansnode1.vm.box = "hashicorp/precise64"
        ansnode1.vm.network "public_network", ip: "10.0.0.201", bridge: 'en1: Wi-Fi 2 (AirPort)'
        ansnode1.vm.provider "virtualbox" do |vb|
            vb.memory = "1536"
        end
    end

    config.vm.define "ansnode2" do |ansnode2|
        ansnode2.vm.box = "hashicorp/precise64"
        ansnode2.vm.network "public_network", ip: "10.0.0.202", bridge: 'en1: Wi-Fi 2 (AirPort)'
        ansnode2.vm.provider "virtualbox" do |vb|
            vb.memory = "1536"
        end
    end

    config.vm.define "ansnode3" do |ansnode3|
        ansnode3.vm.box = "hashicorp/precise64"
        ansnode3.vm.network "public_network", ip: "10.0.0.203", bridge: 'en1: Wi-Fi 2 (AirPort)'
        ansnode3.vm.provider "virtualbox" do |vb|
            vb.memory = "1536"
        end
        ansnode3.vm.provision "ansible" do |ansible|
            ansible.playbook="galera-cc.yml"
            ansible.groups = {
                "cmon" => ["anscmon"],
                "galera" => ["ansnode1", "ansnode2", "ansnode3"],
                "all_groups:all" => ["cmon", "galera"]
            }
            ansible.limit = 'all'
        end
    end

end


