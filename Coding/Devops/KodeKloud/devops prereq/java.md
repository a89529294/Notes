- go to java download page for specific version
- check os(`cat /etc/*release*`) and architecture (`uname -m`)

## option 1 direct download

- `wget https://download.oracle.com/java/20/archive/jdk-20.0.2_linux-x64_bin.tar.gz`
- `sudo tar -xzf jdk-20.0.2_linux-x64_bin.tar.gz -C /opt`
- in bashrc or similar file, add ```
```
export JAVA_HOME=/opt/jdk-20.0.2
export PATH=$JAVA_HOME/bin:$PATH
```
- `source ~/.bashrc`
- check if installed correctly, `java -version`

## option 2 using yum
- `sudo yum install https://download.oracle.com/java/20/archive/jdk-20.0.2_linux-x64_bin.rpm`
- check `java --version`, if error add env variables like below
```
export JAVA_HOME=/usr/java/jdk-20.0.2
export PATH=$JAVA_HOME/bin:$PATH

# remember to check if java is installed in /usr/java
```

## javac, java, javadoc
- `javac` for compiling .java files into .class files
- `java` for running .class files, but specify class names, `java MyClass`, MyClass is the class name.
- `javadoc` for generating docs, `javadoc -d doc MyClass.java`, doc is the destination dir.

## jar vs war 
 Key Differences:

| Feature        | JAR                           | WAR                                                                    |
| -------------- | ----------------------------- | ---------------------------------------------------------------------- |
| **Purpose**    | General-purpose Java archive  | Web application archive                                                |
| **Contents**   | Java classes, resources, etc. | Web resources (HTML, JSP, etc.), servlets, and web configuration files |
| **Deployment** | Libraries or standalone apps  | Web servers (e.g., Tomcat)                                             |
- `jar cf myJar.jar input-file(s)`
- `jar cf myWar.war input-file(s)`