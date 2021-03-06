## PS>Attack Build Tool [![Build status](https://ci.appveyor.com/api/projects/status/c5v1nxo38a7nec3b?svg=true)](https://ci.appveyor.com/project/jaredhaight/psattack)

A tool that makes it easy to compile a custom version of [PS>Attack](https://github.com/jaredhaight/psattack), a portable powershell attack environment. 

#### What does the PS>Attack Build Tool do?
The build tool downloads the latest version of [PS>Attack](https://www.github.com/jaredhaight/psattack/) and the latest versions of tools that is uses (PowerSploit, Powercat, Inveigh, etc), obfuscates them with @danielbohannon's [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation) and then encrypts them with a custom key. 

It then replaces certain identifable strings within the PS>Attack source code with random strings and then compiles everything, producing a custom version of PS>Attack that's up to date and consists of unique file signatures, making it very difficult for Antivirus and Incident Response teams to find.

#### PS>Attack
PS>Attack is a self contained custom PowerShell console that comes with a lot of the latest and greatest offensive PowerShell tools. It's designed to make it very easy for Pentesters to incorporate PowerShell into their workflow. It's suitable to be used on live engagements as it's capable of evading Antivirus and Incident Response teams with the following tricks.

1. It doesn't rely on powershell.exe. Instead it calls powershell directly through the .NET framework.
2. The modules that are bundled with the exe are encrypted. When PS>Attack starts, they are decrypted into memory. The unencrypted payloads never touch disk, making it difficult for most antivirus engines to find them.
3. When generated by the PS>Attack Build Tool, the payloads are encrypted with a unique key. This means that the generated executable's signature changes each time it's created. 

You can find more information about PS>Attack at its [github page](https://github.com/jaredhaight/psattack)

#### Using the Build Tool
You can download precompiled binaries of the build tool from the [releases tab](https://github.com/jaredhaight/PSAttackBuildTool/releases) or if you'd like, clone the repo and compile it from source. To compile it, you can use the Community Edition of [Visual Studio](https://www.visualstudio.com/en-us/products/visual-studio-community-vs.aspx).

You also need full versions of .NET 4.6.1 and .NET 3.5. 4.6.1 is used to run the PS>Attack Build Tool, 3.5 is used to build PS>Attack. By using 3.5 for PS>Attack we end up with an executable that work on anything from a fresh Windows 7 install on up. You can find .NET versions [here](http://blogs.msdn.com/b/dotnet/p/dotnet_sdks.aspx)

#### Contact
If you have any questions or suggestions for PS>Attack or its Build Tool, feel free to submit an issue or reachout on [twitter](https://www.twitter.com/jaredhaight) or via email: jh `[at]` psattack.com

#### Greetz
PS>Attack was inspired by and benefits from a lot of incredible people in the PowerShell community. Particularly [mattifiestation](https://twitter.com/mattifestation) of PowerSploit and [sixdub](https://twitter.com/sixdub), [engima0x3](https://twitter.com/enigma0x3) and [harmj0y](https://twitter.com/HarmJ0y) of Empire. Besides writing the modules and commands that give PS>Attack it's punch, their various projects have inspired alot of my approach to this project as well as my decision to try and contirbute something back to the community.

A huge thank you to [Ben0xA](https://twitter.com/ben0xa), who's [PoshSecFramework](https://github.com/PoshSec/PoshSecFramework) was used to figure out a lot of things about how to build a powershell console.

Thanks to [danielbohannon](https://twitter.com/danielbohannon) for writing the masterpiece that is [Invoke-Obfuscation](https://github.com/danielbohannon/Invoke-Obfuscation). I'm glad someone is crazy enough to do the research in obfuscating PowerShell.