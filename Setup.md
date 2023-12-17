# Settingup Flutter

1. Set [Flutter SDK](https://docs.flutter.dev/get-started/install) - For setting up Flutter UI framework + Collection of tools

For setting the PATH

Enter ``` echo $SHELL ```

If it is zShell, then 

``` touch ~/.zshrc ```

Open the file

``` open ~/.zshrc ```

In the file 

``` 
export PATH="$PATH:[PATH_OF_FLUTTER_GIT_DIRECTORY]/bin"
```

![Path file](https://github.com/PriyathamVarma/Learn-Flutter/blob/main/Images/Screenshot%202023-12-17%20at%2000.02.59.png)

``` Ctrl + s ```

Close the terminal

Open it again

``` which flutter ```

You should see the path of the file for Flutter 

2. Git
3. Android Studio - Used by Flutter SDK - Android
    X Code        - Used for IOS apps

Follow the instructions in downloading

In the terminal 

```
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

Then 

```
sudo xcodebuild -license

```

4. Virtual Devices 
