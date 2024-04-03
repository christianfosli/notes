# Bash / Linux / GNU tools quick ref

## Terminal Signals :stop_sign:

* Exit `Ctrl-D`

* Cancel (kill) app/job `Ctrl-C`

* Suspend `Ctrl-Z` suspend (pause) an app/job (go back to bash)

  * Resume job `fg`  (list all with `jobs`)

## Readline :ledger:

* Go to beginning of line `Ctrl-a`

* Go to end of line `Ctrl-e`

* Delete line `Ctrl-x <Backspace>`

* Move by words `Ctrl- <Arrow-Keys>`

* Open command in $EDITOR, execute upon exit `Ctrl-x Ctrl-e` or `fc`

## Files and Directories :file_folder:

* Copy file contents to clipboard (on WSL) `cat $file | clip.exe`

* Copy file contents to clipboard (on Wayland) `cat $file | wl-copy`

* Search command history: `<C-r> startOfCommand`

* Search for "pattern" and print matching lines: `grep`. Hint: ripgrep `rg` is easier to use and super fast.

* Find files by filename: `find . -name Foo.txt`.

  * Find files case insensitive filename: `find . -iname "*foo*txt"`

  * Or use a fuzzy finder (fzf/skim/neovim telescope).

* Create symlink `ln -s actual_file_path symlink_path`

* Extract .tar.gz file `tar -xzf <filename` (remember eXtract tZe File)

## Networking :globe_with_meridians:

* List ip-address `ip addr`

* List ip addresses on same network: `ip neigh`

* nslookup

* SSH `ssh username@ip -p portnumber`

  * Start ssh service to allow log-ins (fedora) `systemctl start sshd.service`

* Copy files between local computer and remote 
  `scp $file username@ip:/home/$dir` or `scp username@ip:/home/$file $localdir`

## tmux :computer:

* list sessions `tmux ls` or `Ctrl-b s`

* attach `tmux attach #`

* rename window `Ctrl-b ,`

* new pane `Ctrl-b "` or `Ctrl-b %`

* break out pane to a new window `Ctrl-b !`

* toggle layouts `Ctrl-b <space>`

* resize pane `Ctrl-b :resize-pane -{L|R|D|U} {cellSize}`. Can also be done from the shell:
  ```bash
  $ tmux resize-pane -R 10
  ```

* resize panes `Ctrl-b alt-arrows`

* popup `tmux display-popup [-E 'python']`

## Gnome :framed_picture:

* Activities overview: `<super>`

* Move focus to menubar: `<super> <f10>`

* Move focus between window and menubar: `<control> <alt> <tab>`

* Switch between windows: `<super> <tab>`

  * Then press `` ` `` or `<down>` to switch through windows within an application

* Switch between workspaces: `<super> <alt> <arrow>`

* Snap window: `<super> <arrow-keys>`

* Move window to another screen: `<shift> <super> <arrow-keys>`

* Pop open window menu: `<alt> <space>`

* Focus on active notification: `<super> n`

* Show notification list: `<super> v`

* Send notification from terminal:
  ```bash
  $ notify-send 'Hello world' 'the command has finished'
  ```

* Lock screen: `<super> l`

* Screenshot...: `<PrintScreen>`

* Project external displays: `<super> P`

* Toggle zoom: `<alt> <super> 8`

* Emoji picker:  `<windows> <.> <keyword> <space> <space>`

  * Note: Does not work in all applications. E.g. Currently doesn't work in Chrome.

## alacritty :keyboard:

* Launch vi mode: Ctrl Shift Space

## systemctl & UEFI/BIOS :control_knobs:

* Boot into UEFI/BIOS: `sudo systemctl reboot --firmware-setup`

* See boot order `sudo efibootmgr`

* Boot next `sudo efibootmgr --bootnext XXXX`

### Configure systemd-resolved to not use azure private endpoints

* Create file /etc/systemd/resolved.conf.d/az_blob_pub.conf with the following content

  ```ini
  # Work around missconfigured peerings from on-prem networks to azure blob storage private endpoints
  # by forcing DNS to a public DNS server (in this case cloudflare DNS)
  [Resolve]
  DNS=1.1.1.1 2606:4700:4700::1111
  Domains=~blob.core.windows.net
  ```
