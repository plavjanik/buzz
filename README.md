# buzz
The missing package manager for [z/OS UNIX](http://www-03.ibm.com/systems/z/os/zos/features/unix/). 

Buzz simplifies installation of open-source software to z/OS UNIX in a similar way how do Linux package managers like [yum](http://yum.baseurl.org) or [Apt](https://wiki.debian.org/Apt) or [Homebrew](http://brew.sh) for Mac OS X. 

`buzz install curl`  
`buzz install python`  
`buzz install jdk7_64`  

Buzz has no dependencies and it uses only tools that are provided by z/OS. It does not require more security privileges than the installed software itself. 

It can installed by executing single file - `buzz-bootstrap.sh`. This file has to be uploaded to z/OS UNIX because z/OS UNIX does not have curl or similar command that would allow download by one shell command. 

It can install software from their source code using installation scripts (called Bees) or prepacked binary archives (called Honey). Building from the source usually requires GNU toolkit that can be installed by Buzz as well. Archives from with the source code can be downloaded directly from thier websites or mirrors in the local networks. The definitons of Bees are located in main repository (Apiary) and other repositories can be used (e.g. company's repository).

Its architecture is inspired by [Homebrew](http://brew.sh) and it provides z/OS specific functionality to install software to z/OS UNIX (like program controlled attribute). Binary packages (called Honey) can be also created using Bees and then quickly installed without building them. Bees are able install any kind of package, for example IBM z/OS Java SDK if you provide path to IBM PAX file.  

All files are installed inside its own directory (e.g. `/usr/local/Hive`) and then symlinks are created into runtime prefix (e.g. `/usr/local`). Both paths can be configured by user and they can be located in directory that is writable by the user (e.g. `$HOME/buzz`). Users can easily set up their environment just by adding command `buzz env /usr/local` to `$HOME/.profile` file.

Since majority of open-source packages does not maintain configure scripts for z/OS or does not accept changes to support z/OS and EBCDIIC, patches have to be applied during the build process that is done by Bees. These patches are stored at the Apiary.
