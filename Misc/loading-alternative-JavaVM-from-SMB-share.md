# Loading alternative JavaVM from SMB share

Java.exe and javaw.exe support an undocumented-hidden command-line parameter "-XXaltjvm" and also "-J-XXaltjvm". This instructs Java to load an alternative JavaVM library (jvm.dll or libjvm.so) from the desired path.

The DLL is loaded into memory then without writing to the filesystem. This can be used to evade AV defenses, as it has no reference to malicious activity in the command line; obviously the payload of the JVM.DLL must be properly obfuscated. For use in restrictive environments where other binaries cannot be executed. 

## Tested on Windows 10 and JRE ver. 11.0.14

Reference: [https://seclists.org/bugtraq/2010/Apr/80](https://seclists.org/bugtraq/2010/Apr/80)

## PoC
![Screenshot](images/altjvm.jpg)
