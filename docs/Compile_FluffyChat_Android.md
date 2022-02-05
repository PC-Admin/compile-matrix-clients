
~~ Compile FluffyChat Android ~~

Install prerequisite packages for ansible on the controller:

`$ ansible-galaxy collection install community.digitalocean`

Update all the variables in vars.yml.

Run compile script for Android with the following tags:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,save_ips,setup-server,compile-fluffychat-android" compile_fluffychat_android.yml`

After be sure to re-run the playbook with the 'delete-droplet' tag to cleanup:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,delete-droplet" compile_fluffychat_android.yml`