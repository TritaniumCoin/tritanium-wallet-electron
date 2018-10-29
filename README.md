![WalletShell](docs/walletshell.png)  
WalletShell is a GUI wallet for TritaniumCoin.

### Features:
This wallet contains the basic functions required to manage your TritaniumCoin assets:

* Wallet creation
  * Create new wallet
  * Import from private keys
  * Import from mnemonic seed
* Basic wallet operation
  * Open an existing  wallet
  * Display wallet address & balance
  * Display private keys/seed
  * Export private keys/seed
  * Transactions listing/sorting/searching
  * Display transaction detail
  * Export incoming, outgoing, or all transactions to csv file.
  * Incoming Transaction notification
  * Send TurtleCoin to single recipient address, allow to set payment id and custom fee. Provides address lookup from addressbook.
  * Perform wallet optimization by creating fusion transactions 
  * Provides utility to generate payment id and integrated address
* Address book
  * Add/Edit/Delete address entry (label/name, address and payment id)
  * Listing/sorting/searching existing entries
  * Allow to store same wallet address with different payment id
  * Autosave address after sending to new/unknown recipient
* Misc
  * Provides setting to set local or public node address
  * Option to use system tray (on closing/minimizing wallet)
  * Provides list of public nodes, fetch/updated daily from turtlecoin-nodes-json repo.
  * Custom node address that is not on the list will be added/remembered for future use
  * Theme: Dark & Light Mode
  * [Keyboard shortcuts](docs/shortcut.md)


### Notes

WalletShell relies on `tritanium-service` to manage wallet container &amp; rpc communication.

Release installer & packaged archived includes a ready to use `tritanium-service` binary, which is unmodified copy TritaniumCoin release archive.

On first launch, WalletShell will try to detect location/path of bundled `tritanium-service` binary, but if it's failed, you can manually set path to the `tritanium-service` binary on the Settings screen.

If you don't trust the bundled `tritanium-service` file, you can compare the checksum (sha256sum) against one from the official release, or simply download and use the binary from official TritaniumCoin release, which is available here: https://github.com/TritaniumCoin/TritaniumCoin/releases. Then,  make sure to update your `tritanium-service` path setting.

### Download &amp; Run WalletShell

#### Windows:
1. Download the latest installer here: https://github.com/TritaniumCoin/TritaniumCoin/releases
2. Run the installer (`TriWallet-v0.0.1-win-setup`) and follow the installation wizard.
3. Launch WalletShell via start menu or desktop shortcut.

#### GNU/Linux (AppImage):
1. Download latest AppImage bundle here: https://github.com/tritaniumcoin/tritanium-wallet-electron/releases
2. Make it executable, either via GUI file manager or command line, e.g. `chmod +x walletshell-<version>-linux.AppImage`
3. Run/execute the file, double click in file manager, or run via shell/command line. 

See: https://docs.appimage.org/user-guide/run-appimages.html

#### GNU/Linux (tar.bz2 archive)
1. Download latest archive here: https://github.com/tritaniumcoin/tritanium-wallet-electron/releases
2. Extract with file/archive manager of your choice.
3. Run the executable binary (`walletshell-<version>/walletshell`)

#### macOS (TBD/Untested)
1. Download latest archive here: https://github.com/tritaniumcoin/tritanium-wallet-electron/releases
2. Extract downloaded tar archived
3. Run the executable binary (`WalletShell.app/Contents/MacOs/WalletShell`) ??

### Build
You need to have `Node.js` and `npm` installed, go to https://nodejs.org and find out how to get it installed on your platform.

Once you have Node+npm installed:
```
# first, download turtle-service binary for each platform
# from TritaniumCoin official repo
# https://github.com/TritaniumCoin/TritaniumCoin/releases
# extract the turtle-service executable somewhere

# clone the repo
$ git clone https://github.com/tritaniumcoin/tritanium-wallet-electron
$ cd tritanium-wallet-electron

# install dependencies
$ npm install

# create build+dist directory
$ mkdir -p ./build && mkdir -p ./dist

# copy/symlink icons from assets, required for packaging
$ cp ./src/assets/icon.* ./build/

# build GNU/Linux package
$ mkdir -p ./bin/lin
$ cp /path/to/linux-version-of/tritanium-service ./bin/lin/
$ npm run dist-lin

# build Windows package
$ mkdir -p ./bin/win
$ cp /path/to/win-version-of/tritanium-service.exe ./bin/win/
$ npm run dist-lin

# build OSX package
$ mkdir -p ./bin/osx
$ cp /path/to/osx-version-of/tritanium-service ./bin/osx/
$ npm run dist-mac
```

Resulting packages or installer can be found inside `dist/` directory.
