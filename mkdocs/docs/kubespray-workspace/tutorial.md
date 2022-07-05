
This is a brief tutorial on how to use Kubespray workspace to create kubernetes cluster with Kubespray and 
manage it with Octant, kubectl, k9s, and other tools included in the workspace.  

All of the required tools, applications and dependencies are already set up and configured inside the Workspace, so 
you don't need to make any additional configuration, apart of configuring SSH access to your servers. 

### Preparation 

Upload to the workspace SSH keys for your servers, on which you want to install K8s. For this you can use Filebrowser, 
VS-Code or paste the contains of the key in a Terminal. If you want to use terminal, open it from the Quickstart page, and execute 

```
nano ~/.ssh/id_rsa
# paste ssh key, save  and exeit(Ctrl+x) 
# change permission of your ssh key:
chmod 400 ~/.ssh/id_rsa
```

In order to make the next preparation steps, execute the following commands in the workspace terminal.  

cd to the Kubespray project folder

```
cd /home/project/kubespray
```

Update ansible config to use the ssh key you copied.  

```
nano /home/project/kubespray/ansible.cfg
```

Copy `inventory/sample` as `inventory/mycluster`

```
cp -rfp inventory/sample inventory/mycluster
```

Update Ansible inventory file with inventory builder. Set your servers IPS instead! 

```
declare -a IPS=(10.10.1.3 10.10.1.4 10.10.1.5)
CONFIG_FILE=inventory/mycluster/hosts.yaml python3 contrib/inventory_builder/inventory.py ${IPS[@]}
```

Test you can connect to all the servers

```
ansible -m ping -i inventory/mycluster/hosts.yaml all --user=root
```

### Installation 

If all the preparation steps are done properly, the installation of k8s cluster is a single step.  
Cd to the Kubespray folder and execute 

```
ansible-playbook -i inventory/mycluster/hosts.yaml --user=root  --become --become-user=root cluster.yml
```

### Post-installation 

It remains to copy kubeconfig and configure kubectl.  

SSH to k8s master node and show the entire kubeconfig 

```
cat ~/.kube/config
```

Copy the content, and change server IP from `https://127.0.0.1:6443` to your master node IP.  


Go back to the Workspace terminal, and paste this to the '~/.kube/config' file
```
mkdir -p  ~/.kube/
nano ~/.kube/config
```

Test kubectl 

```
kubectl get nodes
```

You should be able to see your kubernetes nodes. Now you can interact with your kubernetes cluster from the workspace using any of these tools 

- CLI tools
    - kubectl 
    - helm 
    - k9s
    - kube-shell

- UI tools
    - Octant


### Ansible features

Visit [this tutorial](../ansible-terraform-workspace/ansible-tools.md) to get familiar with the Ansible toolset included in the workspace.

### Terraform features

Visit [this tutorial](../ansible-terraform-workspace/terraform-tools.md) to get familiar with the Terraform toolset included in the workspace.
