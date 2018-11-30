# TEA Encryption

Encryption and Decryption with TEA using the algorithm by Arkadium.

Created these tools to facilitate the decryption of FlashVars passed into games on Arkadium.
The tools were made by painstakingly analyzing and extracting code snippets from the game "Kritter Crawler", then adding them to files and adding some wrapping to allow passing in arguments. Integrity of the original code was maintained where possible, but some select snippets were omitted to make the code run correctly outside of the original SWF.

As the code only came from one game, it may differ in other Arkadium games and as such these tools may not work for others. I will check at some point and post the results here at a later date.

## Installation

The tools require the installation of a third-party library called "as3shebang" by Corsaair.
The source code for the latter is avaliable [here](https://github.com/Corsaair/as3shebang)

Installation for Linux is as follows.

`wget https://github.com/Corsaair/as3shebang/releases/download/1.0.0/as3shebang_1.0.0_amd64.deb && sudo dpkg -i as3shebang_1.0.0_amd64.deb`

for 64bit

`wget https://github.com/Corsaair/as3shebang/releases/download/1.0.0/as3shebang_1.0.0_i386.deb && sudo dpkg -i as3shebang_1.0.0_i386.deb`

for 32bit

Now run

`git clone https://gitlab.com/mcterra/tea-encrypter && cd tea-encrypter`

(optional) if you want to run the tools without specifying the whole path, run

`sudo cp ./teaencrypt /usr/bin && sudo cp ./teadecrypt /usr/bin`

## Usage

To use the tools run either

`teaencrypt <key> <data>`

for encryption
or

`teadecrypt <key> <data>`

for decryption.