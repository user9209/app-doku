# Backup Recovery Cha20Pol1305

Create encrypted copy of a folder. Hide content but not its metadata (filename, timestamps) or identity (hash of plaintext).

## Help


Backup: Read source folder and copy the files encrypted to destination folder

````
BackupRecoveryCha20Pol1305.jar bk <password> <src-folder> <backup-target-folder>
````

Recovery: Read source folder (backup) and copy the files decrypted to destination folder.

````
BackupRecoveryCha20Pol1305.jar rec <password> <backup-src-folder> <recovery-target-folder>
````

Cleanup: Remove old data: Drops any old versions! `rm -r **/*.cha20.s*`

````
BackupRecoveryCha20Pol1305.jar cleanup <backup-folder>
````

Help: Show help

````
BackupRecoveryCha20Pol1305.jar help 1
````

## Information

File names are leaked as filename will not encrypted and only the extension `.cha20` will added!

Modified files will not overwritten. Existing Backup files will be renamed to the timestamp of the new backup, e.g. `readme.md.cha20.s202401220000`.

The logfile will contain the hash of the plaintext as well as the hash of the encrypted file.
This leads to the case that anyone with access can check, which files are encrypted.
On the other hand you can check which plaintext file is in the encrypted data and which encrypted data are redundand.

## Release

| Version | SHA3-256                                                     |
| ------- | ------------------------------------------------------------ |
| 1.0.1   | 81237d4cb8f6b02eeb08e59dabb85f4515aed0a386d836d90072f6dcff17144c |



## License

Copyright (c) Georg Schmidt 2005-2024

All rights reserved

The text, software and all associated files are the exclusive property of the author and are provided solely for viewing purposes. Any use, copying, modification, distribution, or any other form of utilization is strictly prohibited. No rights are granted to the user, and any unauthorized use is subject to legal action.