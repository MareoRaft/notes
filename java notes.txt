GREAT instructions on getting started w/ JAVA.  includes
  * how to install on command line
  NOTE that i had to download onto MY COMP then upload to server instead of wget straight from server
  * how to check version and resolve version conflicts
  * write a hello world
https://www3.ntu.edu.sg/home/ehchua/programming/howto/JDK_Howto.html
  * for the sudo update-alternative "java", "javac", and "javaws" stuff, ALSO DO "jar"



sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jdk1.8.0_201/bin/java" 1
javac
javaws
jar


sudo update-alternatives --set java /usr/local/java/jdk1.8.0_201/bin/java
javac
javaws
jar

