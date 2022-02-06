
~~ Compile FluffyChat Android ~~

Install prerequisite packages for ansible on the controller:

`$ ansible-galaxy collection install community.digitalocean`

Create an upload keystore:
```
$ sudo apt install android-sdk
$ keytool -genkey -v -keystore ~/upload-keystore.jks -keyalg RSA -keysize 2048 -validity 10000 -alias upload
```

Update all the variables in vars.yml.

Run compile script for Android with the following tags:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,save_ips,setup-server,compile-fluffychat-android" compile_fluffychat_android.yml`

After be sure to re-run the playbook with the 'delete-droplet' tag to cleanup:

`$ ansible-playbook -v -i ./inventory/hosts -t "spawn-droplet,delete-droplet" compile_fluffychat_android.yml`