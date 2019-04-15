# Set Git Server On Raspberry Pi

Add your local machine's public key in `~/.ssh/id_rsa.pub` to Raspberry Pi file `~/.ssh/authorized_keys`

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
