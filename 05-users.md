# §5: Users

---

- Commands are executed by **users**.
- Each user may belong to **groups**.
- `root` is the most powerful user.
- `sudo` command allows to execute other commands as `root`.
- Special users and groups may exist to run software.

---

## Who am I? 😦

```
user@cosmos:~$ whoami
user
```

```
user@cosmos:~$ id
uid=1000(user) gid=1000(user) groups=1000(user),27(sudo)

user@cosmos:~$ id root
uid=0(root) gid=0(root) groups=0(root)
```

---

- Each user has
  * numeric **User ID** (**UID**),
  * home directory, e.g. `/home/user`,
  * login shell, e.g. `/bin/bash` or `/usr/sbin/nologin` if disabled.

- `root` has UID 0.

---

- Each group has numeric **Group ID** (**GID**).

- `sudo` group: those who can run `sudo`.

---

## Managing passwords 🔑

```
user@cosmos:~$ passwd
Changing password for user.
Current password: 
New password: 
Retype new password: 
passwd: password updated successfully
```

---

## Changing root password 🗝

```
user@cosmos:~$ sudo passwd root
New password: 
Retype new password: 
passwd: password updated successfully

user@cosmos:~$ su
Password: 
root@cosmos:/home/user# exit
exit
user@cosmos:~$ 
```

---

## Managing users 🧰

| Command                                           | Action                      |
|---------------------------------------------------|-----------------------------|
| `useradd --create-home --shell /bin/bash newuser` | add user                    |
| `passwd newuser`                                  | set password                |
| `sudo usermod -aG sudo newuser`                   | add to `sudo` group         |
| `su newuser`                                      | login as `newuser`          |
| `userdel newuser`                                 | delete `newuser`            |
| `userdel --remove newuser`                        | detete with `/home/`        |

---

## Where users and passwords are?

- `/etc/passwd` : list of users.

  Can be accessed by everyone.

- `/etc/shadow` : list of users and hashes of their passwords.

  Can be accessed by `root`.

---

## Practice 💪

- Check `/etc/passwd` and `/etc/shadow`.
- Create a new user with home directory and setup their password.
- Add user to the `sudo` group.
- Check `/etc/passwd` and `/etc/shadow` again.
- Login as that user with `su`.
- Exit shell with `exit`.
- Delete the new user.
