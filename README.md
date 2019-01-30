# iChen&reg; System 4 Server Distribution for .NET Core

Binary distributions of the iChen&reg; System Server.

O/S: Linux, Windows  
.NET Core: 2.1 and up

How to Run
----------

~~~
dotnet iChenServerCore.dll
~~~

Sample Configuration File
-------------------------

[iChenServer-sample.config](https://github.com/chenhsong/iChen-Server-Core/blob/master/iChenServer-sample.config) contains a sample configuration file for a single-instance, stand-alone server.  To modify the configuration of the system, overwrite the existing `iChenServer.config` file with this copy, the modify the settings as per (this document)[https://github.com/chenhsong/iChen-Server-Core/blob/master/iChen-Server-Config-Reference.md].

Run in Docker Container
-----------------------

Pre-built Docker images are available from [Chen Hsong Global Docker Images Repository](https://hub.docker.com/r/chenhsong/ichen-server).
