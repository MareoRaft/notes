Good Java Libraries:
  * things in Apache Commons
    * FileUtils (https://commons.apache.org/proper/commons-io/javadocs/api-2.5/org/apache/commons/io/FileUtils.html)

GREAT instructions on getting started w/ JAVA.  includes
  * how to install on command line
  NOTE that i had to download onto MY COMP then upload to server instead of wget straight from server
  * how to check version and resolve version conflicts
  * write a hello world
https://www3.ntu.edu.sg/home/ehchua/programming/howto/JDK_Howto.html
  * for the sudo update-alternative "java", "javac", and "javaws" stuff, ALSO DO "jar"


## Specific directions for Linux
  1. Go to oracle & download
```


jdk_dir_name="jdk1.8.0_201"
java_dir_path="/usr/local/java"
java_commands="java javac javaws jar"
for java_command in $java_commands; do
  sudo update-alternatives --install "/usr/bin/${java_command}" "${java_command}" "${java_dir_path}/${jdk_dir_name}/bin/${java_command}" 1
  sudo update-alternatives --set "${java_command}" "${java_dir_path}/${jdk_dir_name}/bin/${java_command}"
done

```

but the jar you will need to do manually, it seems.  just make a symlink.
jar

