# OS X Preferences

Most of these require logout/restart to take effect

```bash
# Disable window animations ("new window" scale effect)
defaults write NSGlobalDomain NSAutomaticWindowAnimationsEnabled -bool false

# System - Disable cursor magnification
defaults write NSGlobalDomain CGDisableCursorLocationMagnification -bool YES

# System - Locale
defaults write NSGlobalDomain AppleMetricUnits -bool YES
defaults write NSGlobalDomain AppleMeasurementUnits -string "Centimeters"
defaults write NSGlobalDomain AppleLocale -string "fr_US@currency=EUR"

# System - Set decimal delimiter as dot instead of comma
defaults write NSGlobalDomain AppleICUNumberSymbols '{"0" = "."; "10" = "."; }'

# System - Monday is the first day of the week
defaults write NSGlobalDomain AppleFirstWeekday -dict 'gregorian' 2

# System - Disable hibernation (speeds up entering sleep mode)
sudo pmset -a hibernatemode 0

# System - Allow 'locate' command
sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist > /dev/null 2>&1

# Turn on dashboard-as-space
defaults write com.apple.dashboard enabled-state 2

# Use plain text mode for new TextEdit documents
defaults write com.apple.TextEdit RichText -int 0

# Make bottom-left hotspot start screensaver
defaults write com.apple.dock wvous-bl-corner -int 5 && \
defaults write com.apple.dock wvous-bl-modifier -int 0

# Set default Finder location to home folder (~/)
defaults write com.apple.finder NewWindowTarget -string "PfLo" && \
defaults write com.apple.finder NewWindowTargetPath -string "file://${HOME}"

# Expand save panel by default
defaults write NSGlobalDomain NSNavPanelExpandedStateForSaveMode -bool true

# Disable file extension change warning
defaults write com.apple.finder FXEnableExtensionChangeWarning -bool false

# Use current directory as default search scope in Finder
defaults write com.apple.finder FXDefaultSearchScope -string "SCcf"

# Show Path bar in Finder
defaults write com.apple.finder ShowPathbar -bool true

# Show Status bar in Finder
defaults write com.apple.finder ShowStatusBar -bool true

# Avoid creating .DS_Store files on network and USB volumes
defaults write com.apple.desktopservices DSDontWriteNetworkStores -bool true
defaults write com.apple.desktopservices DSDontWriteUSBStores -bool true

# Disable disk image verification
defaults write com.apple.frameworks.diskimages skip-verify -bool true && \
defaults write com.apple.frameworks.diskimages skip-verify-locked -bool true && \
defaults write com.apple.frameworks.diskimages skip-verify-remote -bool true

# Enable the Develop menu and the Web Inspector in Safari
defaults write com.apple.Safari IncludeInternalDebugMenu -bool true && \
defaults write com.apple.Safari IncludeDevelopMenu -bool true && \
defaults write com.apple.Safari WebKitDeveloperExtrasEnabledPreferenceKey -bool true && \
defaults write com.apple.Safari com.apple.Safari.ContentPageGroupIdentifier.WebKit2DeveloperExtrasEnabled -bool true && \
defaults write NSGlobalDomain WebKitDeveloperExtras -bool true

# Show the all files and folders
defaults write com.apple.finder AppleShowAllFiles TRUE

# Show absolute path in finder's title bar. 
defaults write com.apple.finder _FXShowPosixPathInTitle -bool YES

# Switch to dark menu bar
defaults write NSGlobalDomain AppleInterfaceStyle Dark; killall Dock

# Sets default save target to be a local disk, not iCloud.
defaults write NSGlobalDomain NSDocumentSaveNewDocumentsToCloud -bool false

# Screensaver Lock with Password within 5 seconds
defaults write com.apple.screensaver askForPassword -int 1
defaults write com.apple.screensaver askForPasswordDelay -int 5

# Disable AirDrop
defaults write com.apple.NetworkBrowser DisableAirDrop -bool YES

# Login Window preferences
# Enable secure guest access
sudo defaults write /Library/Preferences/com.apple.loginwindow GuestEnabled 1

# Show language input menu
sudo defaults write /Library/Preferences/com.apple.loginwindow showInputMenu 1

# Prevent user list with picture to show up, display login and password field instead
sudo defaults write /Library/Preferences/com.apple.loginwindow SHOWFULLNAME 1

# System - Reveal IP address, hostname, OS version, etc. when clicking the login window clock
sudo defaults write /Library/Preferences/com.apple.loginwindow AdminHostInfo HostName

# System - Disable software updates
sudo softwareupdate --schedule off

# Dock - Automatically hide and show
defaults write com.apple.dock autohide -bool true

# Dock - Remove the auto-hiding delay
defaults write com.apple.Dock autohide-delay -float 0

# Dock - Don’t show Dashboard as a Space
defaults write com.apple.dock "dashboard-in-overlay" -bool true

# Finder - Use list view in all Finder windows
defaults write com.apple.finder FXPreferredViewStyle -string "Nlsv"

# Finder - Allow text selection in Quick Look
defaults write com.apple.finder QLEnableTextSelection -bool true

# iOS Simulator - Symlink the iOS Simulator application
sudo ln -sf "/Applications/Xcode.app/Contents/Applications/iPhone Simulator.app" "/Applications/iOS Simulator.app"

# Safari - Set home page to 'about:blank' for faster loading
defaults write com.apple.Safari HomePage -string "about:blank"

# Safari - Hide bookmarks bar
defaults write com.apple.Safari ShowFavoritesBar -bool false

# Safari - Use Contains instead of Starts With in search banners
defaults write com.apple.Safari FindOnPageMatchesWordStartsOnly -bool false

# Safari - Disable sending search queries to Apple.
defaults write com.apple.Safari UniversalSearchEnabled -bool false

# Chrome - Prevent native print dialog, use system dialog instead
defaults write com.google.Chrome DisablePrintPreview -boolean true

# Mail - Copy email addresses as 'foo@example.com' instead of 'Foo Bar <foo@example.com>'
defaults write com.apple.mail AddressesIncludeNameOnPasteboard -bool false

# Mail - Disable send animation
defaults write com.apple.mail DisableSendAnimations -bool true

# Mail - Disable reply animation
defaults write com.apple.mail DisableReplyAnimations -bool true

# Mail - Show Attachments as Icons
defaults write com.apple.mail DisableInlineAttachmentViewing -bool yes

# Address Book - Enable debug menu
defaults write com.apple.addressbook ABShowDebugMenu -bool true

# iCal - Setup
defaults write com.apple.iCal "IncludeDebugMenu" -bool TRUE
defaults write com.apple.iCal "showDeclinedEvents" -bool TRUE
defaults write com.apple.iCal "n days of week" -int 7
defaults write com.apple.iCal "SharedCalendarNotificationsDisabled" -bool TRUE
defaults write com.apple.iCal "TimeZone support enabled" -bool TRUE
defaults write com.apple.iCal "first day of week" -int 1
defaults write com.apple.iCal "number of hours displayed" -int 14

# Disk Utility - Enable debug menu
defaults write com.apple.DiskUtility DUDebugMenuEnabled -bool true
defaults write com.apple.DiskUtility advanced-image-options -bool true

# Printer - Expand print panel by default
defaults write NSGlobalDomain PMPrintingExpandedStateForPrint -bool true

# Printer - Automatically quit printer app once the print jobs complete
defaults write com.apple.print.PrintingPrefs "Quit When Finished" -bool true

# App Store - Enable the WebKit Developer Tools in the Mac App Store
defaults write com.apple.appstore WebKitDeveloperExtras -bool true

# App Store - Enable Debug Menu in the Mac App Store
defaults write com.apple.appstore ShowDebugMenu -bool true

# System Sound - Disable Sound Effects on Boot
sudo nvram SystemAudioVolume=" "

# System Sound - Disable the system UI sound effects
defaults write com.apple.systemsound "com.apple.sound.beep.flash" -int 0
defaults write com.apple.systemsound "com.apple.sound.beep.volume" -int 0
defaults write com.apple.systemsound "com.apple.sound.uiaudio.enabled" -int 0

# Terminal - Prevent beep
echo "set bell-style none" >> ~/.inputrc
```

# OS X Preferences that need custom input

```bash
# Set Login Window Text
sudo defaults write /Library/Preferences/com.apple.loginwindow LoginwindowText "If you found this computer, please call +33 X XX XX XX XX"

# Set HostName
sudo scutil --set HostName yourhostname.local

# List Available Timezones
sudo systemsetup -listtimezones

# Set Timezone and Set Clock Using Network Time
sudo systemsetup -settimezone Europe/Paris
sudo systemsetup setusingnetworktime on
```


# Homebrew Basics

```bash
# install package manager
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

# install homebrew packages
brew install \
autojump \
colordiff \
drush \
graphicsmagick \
imagemagick \
jpegoptim \
npm
pngcrush \
ssh-copy-id \
tree \
wget \
youtube-dl \



# Install Cask
brew tap caskroom/cask
```

# Shell

```bash
# install hyper terminal
brew cask install hyper

# enable touchID on shell
sudo nano /etc/pam.d/sudo
# on top of the file, add the following line :
auth       sufficient     pam_tid.so
```

## zsh && autojump
```bash
curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
zsh

# If not here add zsh to your shell list in /etc/shells and check this line is here :
/usr/local/bin/zsh

# Add the following line to your ~/.zshrc file
[[ -s $(brew --prefix)/etc/profile.d/autojump.sh ]] && . $(brew --prefix)/etc/profile.d/autojump.sh

# Make zsh the default shell 
nano ~/.hyper.js
# Fill the shell value with 
`shell: '/usr/local/bin/zsh',`

# Don't forget to source it :)
source ~/.zshrc
```



# Development Tools

## Create a conf folder 

- Used for all custom config files, it prevents them from being overriden by homebrew
- If the file can't be located here (for nginx for instance) at least you'll know where to find all of them with symlink

```bash
mkdir -p /usr/local/conf/nginx/{sites-enabled,sites-available,ssl}
sudo mkdir -p /var/log/{nginx,php-fpm}
sudo mkdir -p /usr/local/var/run/php-fpm
```



## Nginx

### Installation

```
brew install nginx --verbose --with-debug
```

To have launchd start nginx now and restart at login:
```
brew services start nginx
```

- `ln -s /usr/local/etc/nginx/nginx.conf /usr/local/conf/nginx`
- In  `/usr/local/etc/nginx/nginx.conf` :
  - Change the `user nobody;` by `user _www;`
  - Add the following line to store errors : `error_log  /var/log/nginx/error.log;`
  - The default nginx port is set to `listen 8080;` so that nginx can run without sudo. Replace it by `listen 80`.
  - Change `server_name localhost;` by `server_name 127.0.0.1;`
  - replace the default location nginx will load (`include /usr/local/etc/nginx/servers/`) by `include /usr/local/nginx/sites-enabled/*;`.
  
- Default document root is: /usr/local/var/www


Reload the config with :
`sudo nginx -s reload`


### Launch Nginx at login

```bash 
sudo cp -v /usr/local/opt/nginx/*.plist /Library/LaunchDaemons/
```

Then edit `/Library/LaunchDaemons/homebrew.mxcl.nginx.plist` and change the `Label` to `nginx` which will allow us to write:
```bash
launchctl start nginx```
instead of 
```bash
launchctl start homebrew.mxcl.nginx
```

Load nginx now and automatically at reboot with :
```bash
sudo launchctl load -w /Library/LaunchDaemons/homebrew.mxcl.nginx.plist
```

Run the following to unload the service so it will not start again at login:

```bash    
sudo launchctl unload -w /Library/LaunchDaemons/homebrew.mxcl.nginx.plist
```

## Installing PHP-FPM (multiple versions)

Start with taping formulas repositories:

    brew tap homebrew/dupes
    brew tap homebrew/versions
    brew tap homebrew/homebrew-php


Reinstall curl with openssl:

    brew reinstall --with-openssl curl

Then install PHPs

    brew install -v --with-fpm \
    --without-apache \
    --with-mysql \
    --with-homebrew-curl \
    --with-homebrew-openssl \
    php56

    brew install -v --with-fpm \
    --without-apache \
    --with-mysql \
    --with-homebrew-curl \
    --with-homebrew-openssl \
    php71
    
    brew install -v --with-fpm \
    --without-apache \
    --with-mysql \
    --with-homebrew-curl \
    --with-homebrew-openssl \
    php72

### Configure php-fpm.conf and php.ini

You can found basic php-fpm config file here `/usr/local/etc/php/*/php-fpm.d/www.conf`.

Check especially `listen = 127.0.0.1:9000` and rename it to `unix=/usr/local/var/run/php-fpm/php72-fpm.sock`. (In each file, replace 72 by the version you're editing)

To ensure search permissions are ok, search for `;listen.mode = 0660` and change it to `listen.mode = 0666` (don't forget to remove the semi-colon).

Everything else can be left as it is.


    
### Launch php now and automatically at login 

    sudo cp /usr/local/opt/php72/homebrew.mxcl.php56.plist ~/Library/LaunchAgents
    launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.php56.plist
    
    sudo cp /usr/local/opt/php72/homebrew.mxcl.php71.plist ~/Library/LaunchAgents
    launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.php71.plist
    
    sudo cp /usr/local/opt/php72/homebrew.mxcl.php72.plist ~/Library/LaunchAgents
    launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.php72.plist

(Just remove -w option if you don't want it to start automatically, but why would you want that ?)


Update your shell profile (`~/.zshrc`, `~/.bashrc` or so) file so that this branch new php is called before the system's one

    export PATH="/usr/local/bin:/usr/local/sbin:...

Source it :

    source ~/.zshrc


### Switching PHP cli

You can use the custom script [phpswitcher](https://raw.githubusercontent.com/gwenth/os-x-dev-clean-install/master/phpswitcher)

    mkdir ~/bin
    curl -L https://raw.githubusercontent.com/gwenth/os-x-dev-clean-install/master/phpswitcher ~/bin/
    chmod u+x ~/bin/phpswitcher
    
Add ~/bin to your `$PATH` variable in you `~/.zshrc` or `~/.bashrc`

    export PATH="~/bin:..."

Source it :

    source ~/.zshrc

This script is really simple, it unlinks the current php formula and links the new one.

Usage : 
```phpswitcher 72``` 
will enable php72 cli


### What about my websites ?

I didn't find a really good way to handle it for now.
I usually do 2 things :
- Duplicate my vhost that I append with the older version : `example56.dev` 
- In the `location ~ \.php$` section I change the `fastcgi_pass` value to match the socket I chose earlier.




# MariaDB

## Installing MariaDB && sequel

    brew cask install sequel-pro
    brew install mariadb
    mysql_install_db

## Configuring MariaDB

You can start MariaDB now:

    mysql.server start

We will now set a root password and make the installation more secure:

    mysqladmin -u root password 'new-password'
    mysql_secure_installation

Deactivate Binary Logs as we do not need replication:

    mysql -uroot -p
    SET sql_log_bin = 0;
    exit

Restart MariaDB and check if log_bin = OFF:

    mysql.server restart
    mysql -uroot -p
    SHOW VARIABLES LIKE 'log_bin';
    exit

## Launch MariaDB at login

After everything is set up, you may want to use launchctl to start mariadb at login:

    mysql.server stop
    ln -sfv /usr/local/opt/mariadb/*.plist ~/Library/LaunchAgents
    launchctl load -w ~/Library/LaunchAgents/homebrew.mxcl.mariadb.plist
    
Run the following to unload the service so it will not start again at login:

    launchctl unload -w ~/Library/LaunchAgents/homebrew.mxcl.mariadb.plist 

## Restore Sequel Pro Favorites

- Quit Sequel Pro if it’s running.
- Replace ~/Library/Application Support/Sequel Pro/Data/Favourites.plist with your backed up copy.
- Replace ~/Library/Preferences/com.sequelpro.SequelPro.plist with your backed up copy.


## Mac Apps with Homebrew Cask

```bash
# Add support for fonts
brew tap caskroom/fonts

# Add dev/beta versions
brew tap caskroom/versions

#install mac apps & fonts
brew cask install \
1password \
android-studio \
androidtool \
appdelete \
carbon-copy-cloner \
charles \
colorpicker-developer \
dupeguru \
evernote \
dropbox \
firefox \
google-chrome \
icons8 \
imageoptim \
imagealpha \
macdown \
mactracker \
moom \
opera \
omnidisksweeper \
omnigraffle \
paw \
pngyu \
sourcetree \
sketch \
skype \
slack \
spotify \
sublime-text \
transmit \
tripmode \
vlc \
vox

# Encfs
brew cask install osxfuse
brew install homebrew/fuse/encfs

# Speedtest command line interface
sudo easy_install pip
sudo pip install speedtest-cli

# Synology Apps
brew cask install \
synology-assistant \
synology-cloud-station-drive \
synology-photo-station-uploader
```

Some apps require manuel of App Store install:

- Adobe Creative Cloud
- Pocket



## Git

### Setup Github

```bash
ssh-keygen -t rsa -C "email@domain.com"

# Copy ssh key to clipboard for adding to github.com
pbcopy < ~/.ssh/id_rsa.pub

# Test connection
ssh -T git@github.com

# Set git config values
git config --global user.name "Full Name" && \
git config --global user.email "email@domain.com" && \
git config --global github.user githubusername && \
git config --global core.editor "vim" && \
git config --global color.ui true && \
git config --global push.default simple

#token
git config --global github.token your_token_here
```


## Sublime Text

### Install Soda Theme

```bash
git clone git://github.com/buymeasoda/soda-theme.git \
~/Library/Application\ Support/Sublime\ Text\ 3/Packages/Theme\ -\ Soda
```

### Install Tomorrow Night Eighties Themes

```bash
#Sublime Text
git clone git://github.com/chriskempson/textmate-tomorrow-theme.git \
~/Library/Application\ Support/Sublime\ Text\ 3/Packages/Color\ Scheme\ -\ Tomorrow

# iTerm2
wget https://raw.githubusercontent.com/mbadolato/iTerm2-Color-Schemes/master/schemes/Tomorrow%20Night%20Eighties.itermcolors \
-O ~/Downloads/Tomorrow\ Night\ Eighties.itermcolors && open ~/Downloads/Tomorrow\ Night\ Eighties.itermcolors

# Xcode
mkdir -p ~/Library/Developer/Xcode/UserData/FontAndColorThemes && \
wget https://raw.githubusercontent.com/chriskempson/tomorrow-theme/master/Xcode%204/Tomorrow%20Night%20Eighties.dvtcolortheme -O \
~/Library/Developer/Xcode/UserData/FontAndColorThemes/Tomorrow\ Night\ Eighties.dvtcolortheme
```

### Settings

```json
{
	"close_windows_when_empty": true,
	"color_scheme": "Packages/Color Scheme - Tomorrow/Tomorrow-Night-Eighties.tmTheme",
	"draw_indent_guides": false,
	"font_face": "Source Code Pro",
	"font_size": 22.0,
	"highlight_modified_tabs": true,
	"ignored_packages":
	[
		"Vintage"
	],
	"show_full_path": true,
	"show_tab_close_buttons": false,
	"spell_check": false,
	"tab_size": 2,
	"theme": "Soda Light.sublime-theme",
	"word_separators": "./\\()\"'-:,.;<>~!@#%^&*|+=[]{}`~?"
}

```

### Key Bindings


```json
[
	{ "keys": ["super+b"], "command": "expand_selection", "args": {"to": "brackets"} },
	{ "keys": ["super+f"], "command": "show_panel", "args": {"panel": "replace"} },
	{ "keys": ["super+alt+f"], "command": "show_panel", "args": {"panel": "find"} }
]
```


### Snippets

```bash
git clone git@github.com:co-b/sublime-snippets.git \
~/Library/Application\ Support/Sublime\ Text\ 3/Packages/CoB
```

## iOS

```bash
sudo gem install cocoapods
pod setup
```

## Dandelion Deployment Tool

```bash
brew install cmake
sudo gem install net-sftp dandelion
```

## Node Packages

```bash
npm install -g coffee-script bower
npm install -g gitbook-cli
```

## LaTeX

Download MacTeX.pkg (2.3 Go): http://www.tug.org/mactex/

Add Latex binary to PATH variable:

    export PATH="/usr/local/bin:/usr/local/sbin:/Library/TeX/texbin:/



## Bypass OS X System Integrity Protection

- Reboot the mac pressing CMD + R
- Open Utilities/Terminal
- Type:

```bash
csrutil disable; reboot
```

# Credits

- <https://github.com/lourou/os-x-dev-clean-install>
- <https://twitter.com/cabel/status/931292107372838912>
- <https://gist.github.com/saetia/1623487>
- <https://github.com/OzzyCzech/dotfiles/blob/master/how-to-install-mac.md>
- <http://www.tug.org/mactex/elcapitan.html>
- <http://www.math.univ-toulouse.fr/~mleroy/LaTeX/Install_MacOSX_mactex.pdf>
- <http://designsimply.com/2011/12/18/autostart-mysql-php-fpm-nginx-os-x-lion>
