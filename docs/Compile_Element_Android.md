
# Compile Element Android

Install prerequisite packages for ansible on the controller:

`$ ansible-galaxy collection install community.digitalocean`

For application signing generate a signing key: https://developer.android.com/studio/build/building-cmdline#sign_manually

Update all the variables in vars.yml.

Run compile script for Android with the following tags:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,save_ips,setup-server,compile-element-android" compile_element_android.yml`

Add the droplet IP to `server_ip_final` in vars.yml to skip re-creating the droplet:

`$ ansible-playbook -v -i ./inventory/hosts -t "compile-element-android" compile_element_android.yml`

After be sure to re-run the playbook with the 'delete-droplet' tag to cleanup:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,delete-droplet" compile_element_android.yml`
