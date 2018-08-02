# Firebase Remote Config export

Export and publish Firebase configurations. 

## Installation and configuration

This code depends on Python 3 and [pip](https://pip.pypa.io/en/stable/installing/).

Install dependencies with
```shell
pip3 install --user -r requirements.txt
```

Download the service file of the Firebase project you intend to use:

1. Go to your Firebase project in <https://console.firebase.google.com>.
2. Then go to Project Settings (gear icon) -> Service Accounts tab and click the "Generate new private key" button. This will start a download. Rename the downloaded file to `service-account.json` and move the file to the current directory.
3. [Enable the Google API for Firebase Remote Config](https://console.developers.google.com/apis/library/firebaseremoteconfig.googleapis.com) of your project.

## Usage

Run
```
./firebase-remote-config get
```
to download the latest configuration of the stored service account file. To use an alternative service account file, use
the `-s` option, to use an alternative output file, use the -f option:
```
./firebase-remote-config get -f output.json -s ~/Downloads/my-long-service-file.json
```

The get command will print a so-called ETag. To publish a new version of the configuration, that ETag needs to be supplied to avoid version conflicts:
```
./firebase-remote-config publish -f output.json etag-123345-32
```

## License

This code is published under the Apache License version 2.0. It is based on [firebase/quickstart-python](https://github.com/firebase/quickstart-python/tree/master/config).
