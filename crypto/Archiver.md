# Archiver

Java Compression Tool with Swing GUI.

## Start


Start GUI with click on jar or simple run

````
Archiver.jar
````

Select the input files or folder using drag-and-drop, the output file using a file explorer as well as a password for 7z.

For all other the password will be ignored.

Press "Compress" to start compression process.

## Information

| Compression | Chipher |
| ----------- | ------- |
| 7z          | AES     |
| zip         | none    |
| tar.xz      | none    |
| tar.gz      | none    |
| tar.lzma    | none    |

For 7z you can enter a password to encrypt the content with AES following the 7z standard.

## Release

| Version | SHA3-256                                                     |
| ------- | ------------------------------------------------------------ |
| 1.0.1   | 32fa79c0d251b10ee0bd882994ce2e8b4bd2233c0d29dc8b837ec0e8e3363bf8 |

## Idea

Encrypt compressed files with non-default cipher ChaCha20Poly1305.

Use compress-then-encrypt, even there are security issues regarding the compression rate related to the content. You may know, that data is e.g. text caused by a high compression rate or it may binary data like pictures or videos then compression rate is low. Compression on encryption is no option as the data will not compressed at all.

## License

Copyright (c) Georg Schmidt 2005-2024

All rights reserved

The text, software and all associated files are the exclusive property of the author and are provided solely for viewing purposes. Any use, copying, modification, distribution, or any other form of utilization is strictly prohibited. No rights are granted to the user, and any unauthorized use is subject to legal action.