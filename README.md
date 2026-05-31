# pentest-tools

Утилиты для AD пентеста и OSCP.

## Инструменты

### check-access
Проверяет ВСЕ методы удалённого доступа для заданных credentials. Поддерживает пароль и pass-the-hash.

```bash
check-access <IP> -u <user> -p <pass> [-d <domain>] [-H <nthash>]
```

Проверяет: SMB, WinRM, RDP, MSSQL, SSH, WMI (nxc), PSExec, SMBExec, WMIExec, DCOMExec, AtExec (impacket), Evil-WinRM, xfreerdp.

### setup-krb
Настройка Kerberos (`/etc/krb5.conf` + `/etc/hosts`) перед работой с AD тачкой. Форсирует TCP (UDP часто блокирован).

```bash
sudo setup-krb <domain> <dc-ip> [dc-hostname]
sudo setup-krb hokkaido-aerospace.com 192.168.109.40 dc
```

### nxc-sweep
Sweep всех протоколов nxc по одному хосту. Fork [nxc-sweep](https://github.com/corey-farley/nxc-sweep) с добавлением LDAP, SSH, WMI, VNC, NFS.

```bash
nxc-sweep <IP> -u <user> -p <pass>
```

Протоколы: SMB (--shares), WinRM, RDP, MSSQL, FTP (--ls), LDAP (--users), SSH, WMI, VNC, NFS (--shares).

## Установка

```bash
chmod +x check-access setup-krb nxc-sweep
cp check-access setup-krb ~/.local/bin/
sudo cp nxc-sweep /usr/local/bin/
```
