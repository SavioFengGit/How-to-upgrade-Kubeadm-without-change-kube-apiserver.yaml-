# How-to-upgrade-Kubeadm-without-change-kube-apiserver.yaml

# Problem
When kubeadm performs a version upgrade, it overwrites some files within the manifest, including the kube-apiserver.yaml file. There can be many reasons why we want this file to remain unchanged. In my customer’s case, it was to keep Kubernetes audit logs enabled. <br>
Enabling these logs is performed by modifying the kube-apiserver.yaml file. So, I will explain below how you can upgrade kubeadm by re-adding the missing lines of the kube-apiserver.yaml file. 
# Solution
We will configure a .yaml configuration file to use during the update. This will allow us to add the missing lines to the kube-apiserver.yaml file during the update. It’s important to be very careful about the file format, which could be either json or yaml.  <br>
In our case, we will use a yaml type file. The file name is not arbitrary. It must follow the format: target[suffix] + patchtype.extension.  <br>
My config file's named: **kube-apiserver0+merge.yaml**

# Command to upgrade Kubeadm with patches 
 - sudo kubeadm apply latest --patches path_folder_file_yaml

<br> <br>


#Author
<b>Xiao Li Savio Feng</b>
