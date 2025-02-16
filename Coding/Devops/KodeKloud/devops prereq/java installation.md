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
