# CloudBees/Jenkins Docker Information #

## Reference ##
* [docker hub](https://hub.docker.com/u/cloudbees/)
* [github cloudbees docker](https://github.com/cloudbees/docker)
* [Install more tools](https://hub.docker.com/_/jenkins/)
* [Jenkins WAR](http://repo.jenkins-ci.org/releases/org/jenkins-ci/main/jenkins-war/)
* [Jenkins WAR - Maven Repository](https://mvnrepository.com/artifact/org.jenkins-ci.main/jenkins-war?repo=jenkins-releases)
* [Building docker image](https://github.com/cloudbees/docker/blob/cje/BUILDING.md)
* [CloudBees Plugins Download](https://jenkins-updates.cloudbees.com/download/plugins/)
* [Jenkins Plugins Download](https://updates.jenkins.io/download/plugins/)

## Command ##
* wget http://repo.jenkins-ci.org/releases/org/jenkins-ci/main/jenkins-war/2.118/jenkins-war-2.118.war

* docker build -t abechin/cje:2.118 --build-arg VERSION=2.118 --build-arg SHA=235a4243edf5cd8227d5bee8bb9c38a68b4083e9 .

* docker container run -it --name cje_2.118 --publish 8888:8080 --publish 5000:5000 --env JAVA_OPTS=${JAVA_OPTS} -v jenkins_home:/var/jenkins_home abechin/cje:2.118
  * JAVA_OPTS="-d64 -server -XX:NewRatio=3 -XX:HeapDumpPath=/var/jenkins/home/tmp -Dhudson.TcpSlaveAgentListener.hostName=cje_2118 -Dhudson.TcpSlaveAgentListener.port=38845 -Dhudson.model.ParametersAction.keepUndefinedParameters=true -Djenkins.security.ApiTokenProperty.showTokenToAdmins=true -Dhudson.slaves.WorkspaceList=_ -XX:+AlwaysPreTouch -Xms3G -Xmx8G -Xss1m -XX:MaxPermSize=728m -XX:GCTimeRatio=50 -Xloggc:/var/jenkins/home/logs/gc-%t-%p.log -XX:+PrintGCDetails -XX:+PrintGCDateStamps -XX:NumberOfGCLogFiles=2 -XX:+UseGCLogFileRotation -XX:GCLogFileSize=50m -XX:+PrintGC -XX:+PrintGCCause -XX:+PrintTenuringDistribution -XX:+PrintReferenceGC -XX:+PrintAdaptiveSizePolicy -XX:+UseG1GC -XX:+ExplicitGCInvokesConcurrent -XX:+ParallelRefProcEnabled -XX:+UseStringDeduplication -XX:+UnlockDiagnosticVMOptions -XX:G1SummarizeRSetStatsPeriod=1 -XX:MaxMetaspaceExpansion=64M -XX:+UnlockExperimentalVMOptions -XX:G1NewSizePercent=20 -Djava.awt.headless=true -Dgroovy.use.classvalue=true"