# Java Auto Updater



Downloads information of latest version and compares it to its own version.

Then the latest is newer, then it downloads the file and verifies its signature.

The public key of the publisher is hard coded.

## Run

``````
java -jar JavaAutoUpdater.jar
``````

Checks for update and downloads the file.

## Prepare

Release has to be signed before update can be successful.

When there is an invalid signature the update will fail and the file will deleted.