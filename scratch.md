# §9: Some precautions

Before doing anything with the command line, here are some safety measures
that you should keep in mind.

---

## Be careful

- Shell doesn't forgive your mistakes:
  * `rm *.tmp` : remove all `*.tmp` files,
  * `rm * .tmp` : remove all files in the current directory

- If you accidentally delete or overwrite a file, there is no reliable way to
  get it back.

- Be careful and make backups.

---

## Don't run things as root

- Never login as `root` for doing routine work.

- Login as your own user (`user` in our setup).

- Use `sudo` when needed.

---

## Shell scripts

- Be extra careful when writing shell scripts.
- Tricky Bash syntax and rules.
- Wrong assumptions:
  * file names will never contain spaces,
  * script will be always run from `/foo/bar`,
  * ...

- **[Shell check](https://www.shellcheck.net/)** linter.
  Integrates in VS Code.

---

## Scripts from the Internet

- Some new cool projects encourage you to run things like
```
curl -s "https://get.sdkman.io" | bash
```

- Works assuming there is `curl`.

- Grabs a script from the Internet and sends its contents to Bash.

- **Never do that** unless you trust the website.
