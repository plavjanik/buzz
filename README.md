# buzz
The missing package manager for z/OS UNIX. 

Buzz simplifies installation of open-source software to z/OS UNIX in a similar way how do Linux package managers like yum or Aptitude or Homebrew for Mac OS X. 

buzz install jdk7  
buzz install python27  
buzz install curl  

Buzz has no dependencies and it uses only tools that are provided by z/OS. It does not require more security privileges than the installed software itself. 

It can installed by executing single file - buzz-bootstrap.sh. This file has to be uploaded to z/OS UNIX because z/OS UNIX does not have curl or similar command that would allow download by one shell command. 

It can install software from their source using installation scripts (called bees) or prepacked binary archives (called honey). Building from source usually requires GNU toolkit that can be installed by buzz. 

Its architecture is inspired by Homebrew and it provides z/OS specific functionality. 
