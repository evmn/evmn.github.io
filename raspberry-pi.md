# Set Git Server On Raspberry Pi

Add your local machine's public key in `~/.ssh/id_rsa.pub` to Raspberry Pi file `~/.ssh/authorized_keys`

## Read Your IP Address After Boot

```sh
#/bin/bash

ip=$(hostname -I)
for i in {1..3};
do
	echo "I P address is $ip" | festival --tts
#	sleep 0.5
done
```


## Set A Repo On Raspberry Pi

```sh
mkdir test.git
cd test.git
git init --bare
```

## Clone To Local Machine

```sh
git clone ssh://git@rpi.local:17438/home/git/test.git
git remote add pi ssh://git@rpi.local:17438/home/git/test.git
```

After editing your repo, push it to Raspberry Pi

```sh
git add --all
git commit -m "read me"
git push pi master
```

---

### Monitor Raspberry Pi Temperature

```sh
vcgencmd measure_temp
```

## Sync Folders From Raspberry Pi To Local Folder

Add two line in `~/.ssh/config` file:

```
Host rpi.local
Port 61734
```

Then, run the following command:

```sh
rsync -r git@rpi.local:/home/git/ ./
```

