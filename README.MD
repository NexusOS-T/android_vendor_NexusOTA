
# NexusOS OTA repo  
In order for a device to be officially supported by NexusOS, OTA information needs to be added.  
Please refer to the following "Readme" to get started:

## 1. Introduction ##
In order for a device to be OTA compliant, there are a few things to know.

### 1.1 JSON structure ###
```
{
  "response": [
    {
      "timestamp": 0000000000,
      "filename": "NexusOS-20.0-<date>-<device codename>-v<version>.zip",
      "md5": "abcdefg123456",
      "size": 123456789,
      "download": "https://sourceforge.net/projects/nexusos/files/<device codename>/<version>/NexusOS-20.0-<date>-<device codename>-v<version>.zip/download",
      "version": "<version>"
    }
  ]
}

```

### 1.2 changelog.txt structure ###
```
Highlights & Device Specific Changes:
Device: Device name (<device codename>)  
Device maintainer: Name (nickname)  
Required firmware: add if any else remove this line

===== <date> =====
- change 1
- change 2
- change 3
```

## 2 Guidelines ##
* Check if manufacturer is already existing  
* Check if published link is official  
* Check if JSON is intact with help of online validator tools like https://jsonformatter.org  
* Check if no extra / missing spaces  

### 3 Update build ###
```bash
git clone https://github.com/NexusOTA/android_vendor_NexusOTA -b 20.0
cd android_vendor_NexusOTA
git fetch --all
git pull
```

Then:

1. Copy *codename*.json file from OUT dir over to this repo  
2. Make changes to changelog_*codename*.txt  
3. Now with the files updated, commit your update to this repo  
```bash
git add .
git commit #(this opens your preferred text editor, so write a nice description like "<device codename>: update build")
git push #you may be prompted for your GitHub username and password
```
