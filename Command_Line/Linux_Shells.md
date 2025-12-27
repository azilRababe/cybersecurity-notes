## 🐧 Linux Shell Basics

- `echo $SHELL`
  Displays the current shell you are using.

- `cat /etc/shells`
  Lists all available shells installed on your system.

---

## 🔄 Switching and Managing Shells

- To switch shells temporarily, type the shell name and press Enter.
  Example:

  ```
  zsh
  ```

- `chsh -s /usr/bin/zsh`
  Changes your default login shell.

  Note: You must log out and log back in for the change to take effect.

---

## 📜 Command History

- `history`
  Displays previously executed commands.

---

## 🧩 Bash Scripting Basics

- Bash scripts should start with a shebang:

  ```
  #!/bin/bash
  ```

- Bash scripts typically use the `.sh` extension.

- `chmod +x <script.sh>`
  Grants execute permission to the script.
