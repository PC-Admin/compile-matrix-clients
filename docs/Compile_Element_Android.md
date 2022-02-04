
~~ Compile Element Android ~~

Install prerequisite packages for ansible on the controller:

`$ ansible-galaxy collection install community.digitalocean`

Update all the variables in vars.yml.

Run compile script for Android with the following tags:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,save_ips,setup-server,compile-android" compile_element_android.yml`

After be sure to re-run the playbook with the 'delete-droplet' tag to cleanup:

`$ ansible-playbook -v -i ./inventory/hosts -t "delete-droplet" compile_element_android.yml`