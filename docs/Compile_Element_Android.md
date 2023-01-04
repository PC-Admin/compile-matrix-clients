
# Compile Element Android

1) Install prerequisite packages for ansible on the controller:

`$ ansible-galaxy collection install community.digitalocean`

2) Install the prerequisite Linux package on the controller:

`sudo apt install rename`

3) For application signing generate a signing key: https://developer.android.com/studio/build/building-cmdline#sign_manually

4) Update all the variables in ./inventory/host_vars/hostname/vars.yml.

5A) Run compile script for Android with the following tags (also generating a DigitalOcean droplet):

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,save-ips,setup-server,compile-element-android" compile_element_android.yml`

OR

B) Run compile script for Android with the following tags (on your own hardware):

`$ ansible-playbook -v -i ./inventory/hosts -t "save-ips,setup-server,compile-element-android" compile_element_android.yml`

6) Add the droplet IP to `server_ip_final` in vars.yml to skip re-creating the droplet:

`$ ansible-playbook -v -i ./inventory/hosts -t "compile-element-android" compile_element_android.yml`

7) After be sure to re-run the playbook with the 'delete-droplet' tag to cleanup:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,delete-droplet" compile_element_android.yml`

8) To upload the release files to a webserver use:

`$ ansible-playbook -v -i ./inventory/hosts -t "upload-fdroid-release" compile_element_android.yml`