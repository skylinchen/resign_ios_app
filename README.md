# iOS App的重签名

对iOS App进行重签名的脚本命令，包括Xcode Build后的App、Archive包、IPA包以及从AppStore下载的IPA包等。

## Requirement

Xcode command line tool

## Usage


### 1.Xcode Build的App重签名

脚本文件: ios_resign_with_app

Usage:
```
$ ios_resign_with_app $source_app_file $Developer_code_sign $mobileprovision $target_app_related_path
```

Example:
```
$ ios_resign_with_app Testerhome.app "iPhone Developer: XXX XXXX (XXXXXXX)" embedded.mobileprovision Testerhome-resigned.app
```

### 2.Xcode Archive的Archive包重签名

脚本文件: ios_resign_with_archive

Usage:
```
$ ./ios_resign_with_archive $source_archive_file $Developer_code_sign $mobileprovision $target_archive
```

Example:
```
$ ./ios_resign_with_archive demo.xcarchive "iPhone Developer: XXX XXXX (XXXXXXX)" embedded.mobileprovision demo-resigned.xcarchive
```


### 3.Xcode 导出的IPA包的重签名

脚本文件: ios_resign_with_ipa

Usage:
```
$ ios_resign_with_ipa $source_ipa_file $Developer_code_sign $mobileprovision $target_app_related_path
```

Example:
```
$ ios_resign_with_ipa Testerhome.ipa "iPhone Developer: hengjie chen (XXXXXXXX)" embedded.mobileprovision Testerhome-resigned.ipa
```

### 4.AppStore下载的IPA包的重签名

脚本文件: ios_resign_from_app_to_ipa

Assume folder app-extracted is the folder that created by running `unzip app.ipa -d app-extracted`
```
$ ls app-extracted
META-INF             Payload              iTunesArtwork        iTunesMetadata.plist
```

Then it should be use like below:
```
$ ios_resign_from_app_to_ipa app-extracted $Developer_code_sign $mobileprovision $target_ipa_related_path
```

example:
```
$ ios_resign_from_app_to_ipa app-extracted "iPhone Developer: hengjie chen (XXXXXXXX)" embedded.mobileprovision Testerhome-resigned.ipa
```