# Cloud-Uploader

## Cloud-Protocols

- SFTP / (SCP)
- WebDav
- S3
- CRUD / REST

## Features

- Store cloud accounts
- upload data
- download data
- list cloud data
- encrypt any uploaded data
- decrypt any downloaded data


## Commandline

### Add account

````
cloud.jar -add-account -name <account-name> -url <url> -username <username> -password <password>
cloud.jar -add-account -name <account-name> -protocol <protocol> -host <server-host> -port <port> -username <username> -password <password>
````

### Create master secret key for account

````
cloud.jar -add-msk -account <account-name>
````

### Upload a file or folder

````
cloud.jar -upload <source-file> -dest <destination> [-account <account-name>]

cat <input-file> | cloud.jar -upload -dest <destination> [-account <account-name>]
````

### Download a file or folder

````
cloud.jar -download <source-file> -dest <destination> [-account <account-name>]
cloud.jar -download <source-file> [-account <account-name>] > <output-file>
````



## Glosar

| Short | Long |
| ----- | ---- |
| CRYSTALS | Cryptographic Suite for Algebraic Lattices |
