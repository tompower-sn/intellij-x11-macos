### IntelliJ X11 forwarding over SSH from macOS client

Notes for using IntelliJ from linux host on macOS client.

settings.zip/.Xmodmap give macOS like IntelliJ keybindings.

#### On Debian host
```
sudo apt install -y snapd &&
sudo snap install intellij-idea-ultimate --classic &&
echo 'X11Forwarding yes' >> /etc/ssh/sshd_config &&
echo 'X11UseForwarding yes' >> /etc/ssh/sshd_config &&
service sshd restart &&
git clone https://github.com/tom-power/intellij-x11-macos &&
cp ./intellij-x11-macos/settings.zip ~/Downloads
```

#### On macOS client
```
brew cask install xquartz &&
ssh-copy-id user@host &&
git clone https://github.com/tom-power/intellij-x11-macos &&
cp ./intellij-x11-macos/.Xmodmap ~/
```
```
XQuartz -> Applications -> customise -> Add Item
Name: intellij
Command: add ssh user@host -Y '/snap/bin/intellij-idea-ultimate'
```
```
XQuartz -> Applications -> intellij # launch IntelliJ
Intellij -> File -> Manage IDE Settings -> Import Settings -> Select ~/Downloads/settings.zip -> keymaps
Intellij -> Preferences -> Keymap -> select Mac OS 10.5+ pc
```
