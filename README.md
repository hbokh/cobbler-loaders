# cobbler-loaders

Cobbler loader files (predating Cobbler 3.2.x), plus `lpxelinux.0` ([natively supports HTTP and FTP transfers](https://wiki.syslinux.org/wiki/index.php?title=PXELINUX#HTTP_and_FTP)).

Additional packages that need to be installed on CentOS7:

- `grub2-pc-modules-2.02-0.87.el7.centos.6.noarch`
- `grub2-efi-x64-modules-2.02-0.87.el7.centos.6.noarch`

```console
yum install grub2-efi-x64-modules
yum install grub2-pc-modules
```

Used through symbolic links in `/var/lib/cobbler/loaders/grub`:

```txt
i386-pc -> /usr/lib/grub/i386-pc/
x86_64-efi -> /usr/lib/grub/x86_64-efi/
```

Some older files (before [18 Nov 2012](https://github.com/cobbler/cobbler/pull/358/files)) can be found here for reference or comparison: <https://dgoodwin.fedorapeople.org/loaders/>


Unpack `files/cobbler-loaders.tar.gz` in the root of the Cobbler 2.8.5 server:

```console
cd /
tar zxvf /path/to/files/cobbler-loaders.tar.gz
$ ls -alR /var/lib/cobbler/loaders/
/var/lib/cobbler/loaders/:
total 1220
drwxr-xr-x. 3 root root    231 Jun 11 18:05 .
drwxr-xr-x. 9 root root    213 Jun 11 15:10 ..
-rw-r--r--. 1 root root    631 Apr 28  2009 COPYING.elilo
-rw-r--r--. 1 root root  18007 Mar  6  2020 COPYING.syslinux
-rw-r--r--. 1 root root    626 Mar  6  2020 COPYING.yaboot
-rw-r--r--. 1 root root 356493 Apr 28  2009 elilo-ia64.efi
drwxr-xr-x. 2 root root    112 Jan 22 09:50 grub
-rw-r--r--. 1 root root 243679 Mar  6  2020 grub-x86_64.efi
-rw-r--r--. 1 root root 237224 Mar  6  2020 grub-x86.efi
-rw-r--r--. 1 root root  91550 Apr 18  2020 lpxelinux.0
-rw-r--r--. 1 root root  54964 Mar  6  2020 menu.c32
-rw-r--r--. 1 root root  16794 Mar  6  2020 pxelinux.0
-rw-r--r--. 1 root root   1054 Mar  6  2020 README
-rw-r--r--. 1 root root 198236 Mar  6  2020 yaboot

/var/lib/cobbler/loaders/grub:
total 1492
drwxr-xr-x. 2 root root     112 Jan 22 09:50 .
drwxr-xr-x. 3 root root     231 Jun 11 18:05 ..
-rw-r--r--. 1 root root  294327 Jan 22 10:02 grub.0
-rw-r--r--. 1 root root       0 Jan 22 10:02 grubaa64.efi
-rw-r--r--. 1 root root       0 Jan 22 10:02 grub.ppc64le
-rw-r--r--. 1 root root 1231360 Jan 22 10:02 grubx64.efi
lrwxrwxrwx. 1 root root      21 Jan 22 09:50 i386-pc -> /usr/lib/grub/i386-pc
lrwxrwxrwx. 1 root root      24 Jan 22 09:50 x86_64-efi -> /usr/lib/grub/x86_64-efi
```

Check after installation with `cobbler get-loaders`:

```console
$ cobbler get-loaders
task started: 2021-06-11_182913_get_loaders
task started (id=Download Bootloader Content, time=Fri Jun 11 18:29:13 2021)
path /var/lib/cobbler/loaders/README already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/COPYING.elilo already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/COPYING.yaboot already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/COPYING.syslinux already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/elilo-ia64.efi already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/yaboot already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/pxelinux.0 already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/menu.c32 already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/grub-x86.efi already exists, not overwriting existing content, use --force if you wish to update
path /var/lib/cobbler/loaders/grub-x86_64.efi already exists, not overwriting existing content, use --force if you wish to update
*** TASK COMPLETE ***
```
