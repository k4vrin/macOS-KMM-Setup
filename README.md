# Prepare Your Mac For Kotlin Multiplatform Mobile

The first step is to install Homebrew on your mac. Homebrew is a package manager for macOS and Linux. For more information visit [brew.sh](brew.sh)

![Pasted image 20230824142011.png](/assets/Pasted%20image%2020230824142011.png)

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Next, Homebrew will suggest running these two commands to put Homebrew in the environment path.

![Pasted image 20230824142104.png](/assets/Pasted%20image%2020230824142104.png)

Replace `<user>` with yours

```
(echo; echo 'eval' "$(/usr/local/bin/brew shellenv)"') >> /Users/<user>/.zprofile
```

```
eval "$(/usr/local/bin/brew shellenv)"
```

The next step is to install [KDoctor](https://github.com/Kotlin/kdoctor). KDoctor is a command-line tool that helps to set up the environment for Kotlin Multiplatform Mobile app development.

```
brew install kdoctor
```

Then run kdoctor to see the requirements:

![Pasted image 20230824142416.png](/assets/Pasted%20image%2020230824142416.png)

Let’s provide these requirement step by step

### **Java**

To download java JDK visit this address: [https://www.oracle.com/java/technologies/downloads/](https://www.oracle.com/java/technologies/downloads/)

Make sure to download the version that is compatible with your CPU Architecture.

Apple silicon machines should use arm64 versions. Intel machines need x64

### **Xcode**

Download Xcode from the mac App Store. It’s free and after download, it gets installed automatically.

### **Cocoapods**

Before installing cocoapods, you must install the compatible version of ruby with KMM.

```
brew install ruby@2.7
```

After installation, brew will suggest the command you need to make this version of ruby your machine's default version. Because there is already a version of ruby is installed on all macOS machines.

![Pasted image 20230824142628.png](/assets/Pasted%20image%2020230824142628.png)

![Pasted image 20230824142638.png](/assets/Pasted%20image%2020230824142638.png)

You can update the terminal current session to see the changes:

```
source ~./zshrc
```

Then for installing cocoapods just write this command

```
brew install cocoapods
```

### **Android Studio**

For downloading android studio you can visit [https://developer.android.com/studio](https://developer.android.com/studio)

Or you can use Jetbrains Toolbox: [https://www.jetbrains.com/toolbox-app/](https://www.jetbrains.com/toolbox-app/)

After download and install Android Studio make sure to install KMM Plugin

![Pasted image 20230824142759.png](assets/Pasted%20image%2020230824142759.png)

Run kdoctor to see is everything ok. You should see something like this:

![Pasted image 20230824142819.png](/assets/Pasted%20image%2020230824142819.png)

**Some Common Errors**

1. BUILD FAILED in 8s 1 actionable task: 1 executed Command PhaseScriptExecution failed with a nonzero exit code. Check the Xcode log by using ⌘(command) + 9 if you see: `gradlew permission denied` , Write this command in terminal in your project root.

```
chmod +x gradlew
```

2. BUILD FAILED shared module not found or Greeting not available in scope when using cocoapods as framework instead of regular framework. until now (1 feb 2023) compatible ruby version for KMM is 2.7 and cocoapods 1.11.3. Refer to the ruby installation in this document and install compatible ruby version

### **Additional Resources**

[Install Ruby on Your Mac: Everything You Need to Get Going](https://stackify.com/install-ruby-on-your-mac-everything-you-need-to-get-going/)

[Android Studio setup STILL tricky on M1 Pro?](https://www.youtube.com/watch?v=QHfd2CEMOoY)

[Get started with Kotlin/Native](https://kotlinlang.org/docs/native-get-started.html)
