# E-Mail-Client

## Storage in Cloud

### Mail header and body (< 1 MiByte)

Using a database like MySQL or SQlite.

Mail is idenified using a UUID4.

### Mail appendix

Using a replicated S3 data storage.
All content is encrypted using ChaCha20-Poly1305.

Appendix is idenified by its SHA3-256 Hash or "XOR(SHA3-256, HMAC(key, SALT)) || SALT" of the plaintext.

Using SHA3-256 leaks the information, what is in the file, when the file is encrypted.
Hash of plaintext is required for deduplication (do not upload same data to the server).
Encypted Hash protects identity but allows deduplication.

Alterative store a mapping table for ciphertext-hashes and plaintext-hashes.

## Mail-Handling

1. Download mails via IMAP form the server
2. Detect appendix and convert them to encrypted files
3. Replace appendix in the mail using the new link-mime-part including metadata
4. Store the encrypted appendix to S3 server
5. Convert content of mail to UTF-8 when possible
6. Encrypt the mail and store it to the database
7. Delete message from IMAP-Server



## Link-Mime-Part

````
----==_mimepart_6704c472bd138_33642e2843c1144269b
Content-Type: S3-File-Link
Server: s3.example.com
File: 644bcc7e564373040999aac89e7622f3ca71fba1d972fd94a31c3bfbf24e3938
Size: 545644
CreateTime: 5456454645645
Filename: hello world.txt
FileContentType: text/plain;
 charset=UTF-8
----==_mimepart_6704c472bd138_33642e2843c1144269b--
````


# Appendix

## Content-Types

````
Content-Type: multipart/mixed; boundary="=--xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
````

````
Content-Type: text/html; charset=utf-8
````


````
Content-Type: text/plain; charset=UTF-8; format=flowed
````


````
Content-Type: multipart/alternative;
 boundary="--==_mimepart_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
````

````
Content-Type: multipart/related;
 boundary="------------9VHFT07FcKKGu3giiFR0uctl"
````

### Example
````
Content-Type: multipart/alternative;
 boundary="--==_mimepart_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

----==_mimepart_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Content-Type: text/plain;
 charset=UTF-8
Content-Transfer-Encoding: quoted-printable

yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy

----==_mimepart_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
Content-Type: text/html;
 charset=UTF-8
Content-Transfer-Encoding: quoted-printable

yyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyyy

----==_mimepart_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx--
````


````
Content-Type: multipart/related;
 boundary="------------9VHFT07FcKKGu3giiFR0uctl"

--------------9VHFT07FcKKGu3giiFR0uctl
Content-Type: text/html; charset=UTF-8
Content-Transfer-Encoding: 7bit

<!DOCTYPE html>
<html>
  <head>

    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
  </head>
  <body>
    <img src="cid:part1.0kxCWRJo.hvJNrlF4@example.com"
      moz-do-not-send="false">
  </body>
</html>
--------------9VHFT07FcKKGu3giiFR0uctl
Content-Type: image/png; name="example300.png"
Content-Disposition: inline; filename="example300.png"
Content-Id: <part1.0kxCWRJo.hvJNrlF4@example.com>
Content-Transfer-Encoding: base64
````


## Content-Transfer-Encoding

````
Content-Transfer-Encoding: quoted-printable
````

````
Content-Transfer-Encoding: base64
````

````
Content-Transfer-Encoding: 7bit
````

## files

````
Content-Type: image/png; name="Insta30x30.png"
Content-Transfer-Encoding: base64
Content-Disposition: inline; filename="Insta30x30.png"
Content-ID: <Insta30x30.png>
````

````
Content-Type: application/pdf; name="AGB.pdf"
Content-Transfer-Encoding: base64
Content-Disposition: attachment; filename="AGB.pdf"
````

````
Content-Type: application/pdf;
 name="Rechnung-R-DE-xxxxx.pdf"
Content-Disposition: attachment;
 filename="Rechnung-R-DE-xxxxx.pdf"
Content-Transfer-Encoding: base64
````

## MIME-Parts

````
Content-Type: multipart/mixed; boundary="------------zWprjefz0ZQsaHGzgzzOA09U"
````


````
Content-Type: multipart/related; boundary="------------zWprjefz0ZQsaHGzgzzOA09U"
````


## Min-Mail

````
Date: Sun, 1 Sep 2024 09:00:00 +0200
From: "Tom Jones" <tom.jones@example.com>
To: oerkan@example.com
Message-ID: <0000000_1111111111@example.com>
Subject: Hello World
Mime-Version: 1.0
Content-Type: multipart/mixed; boundary="==_mimepart_A1"
Content-Transfer-Encoding: 7bit

--==_mimepart_A1
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

Hallo Örkan!

--==_mimepart_A1
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

wie geht es dir?

Grüße

Tom

--==_mimepart_A1--
````

## Thunderbird


### opens last block
````
Date: Sun, 1 Sep 2024 09:00:00 +0200
From: "Tom Jones" <tom.jones@example.com>
To: oerkan@example.com
Message-ID: <0000000_1111111111@example.com>
Subject: Hello World
Mime-Version: 1.0
Content-Type: multipart/alternative; boundary="==_mimepart_A1"
Content-Transfer-Encoding: 7bit

--==_mimepart_A1
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

Hallo Örkan!

--==_mimepart_A1
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

wie geht es dir?

Grüße

Tom

--==_mimepart_A1--
````

### html when enabled else plaintext

````
Date: Sun, 1 Sep 2024 09:00:00 +0200
From: "Tom Jones" <tom.jones@example.com>
To: oerkan@example.com
Message-ID: <0000000_1111111111@example.com>
Subject: Hello World
Mime-Version: 1.0
Content-Type: multipart/alternative; boundary="==_mimepart_A1"
Content-Transfer-Encoding: 7bit

--==_mimepart_A1
Content-Type: text/html; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

Hallo Örkan!

--==_mimepart_A1
Content-Type: text/plain; charset=UTF-8
Content-Transfer-Encoding: quoted-printable

wie geht es dir?

Grüße

Tom

--==_mimepart_A1--
````


## Pic

````
--------------9VHFT07FcKKGu3giiFR0uctl
Content-Type: text/html; charset=UTF-8
Content-Transfer-Encoding: 7bit

<!DOCTYPE html>
<html>
  <head>

    <meta http-equiv="content-type" content="text/html; charset=UTF-8">
  </head>
  <body>
    <img src="cid:part1.0kxCWRJo.hvJNrlF4@example.com"
      moz-do-not-send="false">
  </body>
</html>
--------------9VHFT07FcKKGu3giiFR0uctl
Content-Type: image/png; name="example300.png"
Content-Disposition: inline; filename="example300.png"
Content-Id: <part1.0kxCWRJo.hvJNrlF4@example.com>
Content-Transfer-Encoding: base64
````

### Content

````
Content-Type: image/png; name="example.png"
Content-Disposition: attachment; filename="example.png"
Content-Transfer-Encoding: base64

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
````
