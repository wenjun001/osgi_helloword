# osgi_helloword

Let go to start OSGI leaning.

Same as leaning other technology let us tart hello word for OSGI

Firsly download latest OSGI container you can download karaf4.X
http://karaf.apache.org/download.html

Then creat project with Maven 

mvn archetype:generate \
>     -DarchetypeGroupId=org.apache.karaf.archetypes \
>     -DarchetypeArtifactId=karaf-bundle-archetype \
>     -DarchetypeVersion=4.0.0 \
>     -DgroupId=osgi_leaning \
>     -DartifactId=helloworld_osgi \
>     -Dversion=1.0-SNAPSHOT \
>     -Dpackage=com.helloworld.osgi
[INFO] Scanning for projects...
[INFO]                                                                         
[INFO] ------------------------------------------------------------------------
[INFO] Building Maven Stub Project (No POM) 1
[INFO] ------------------------------------------------------------------------
[INFO] 
[INFO] >>> maven-archetype-plugin:2.4:generate (default-cli) > generate-sources @ standalone-pom >>>
[INFO] 
[INFO] <<< maven-archetype-plugin:2.4:generate (default-cli) < generate-sources @ standalone-pom <<<
[INFO] 
[INFO] --- maven-archetype-plugin:2.4:generate (default-cli) @ standalone-pom ---
[INFO] Generating project in Interactive mode
[INFO] Archetype repository not defined. Using the one from [org.apache.karaf.archetypes:karaf-bundle-archetype:4.0.7] found in catalog remote
[INFO] Using property: groupId = osgi_leaning
[INFO] Using property: artifactId = helloworld_osgi
[INFO] Using property: version = 1.0-SNAPSHOT
[INFO] Using property: package = com.helloworld.osgi
Confirm properties configuration:
groupId: osgi_leaning
artifactId: helloworld_osgi
version: 1.0-SNAPSHOT
package: com.helloworld.osgi
 Y: : 
[INFO] ----------------------------------------------------------------------------
[INFO] Using following parameters for creating project from Archetype: karaf-bundle-archetype:4.0.0
[INFO] ----------------------------------------------------------------------------
[INFO] Parameter: groupId, Value: osgi_leaning
[INFO] Parameter: artifactId, Value: helloworld_osgi
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] Parameter: package, Value: com.helloworld.osgi
[INFO] Parameter: packageInPathFormat, Value: com/helloworld/osgi
[INFO] Parameter: version, Value: 1.0-SNAPSHOT
[INFO] Parameter: package, Value: com.helloworld.osgi
[INFO] Parameter: groupId, Value: osgi_leaning
[INFO] Parameter: artifactId, Value: helloworld_osgi
[INFO] project created from Archetype in dir: /home/onos10/research/helloworld_osgi
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 8.907 s
[INFO] Finished at: 2016-11-08T16:36:47-08:00
[INFO] Final Memory: 18M/318M
[INFO] ------------------------------------------------------------------------

Install bundle to your resposity

helloworld_osgi$ mvn install
[INFO] Scanning for projects...
 .....................................
 ...................................... 	
[INFO] --- maven-install-plugin:2.5.2:install (default-install) @ helloworld_osgi ---
[INFO] Installing /home/onos10/research/helloworld_osgi/target/helloworld_osgi-1.0-SNAPSHOT.jar to /home/onos10/.m2/repository/osgi_leaning/helloworld_osgi/1.0-SNAPSHOT/helloworld_osgi-1.0-SNAPSHOT.jar
[INFO] Installing /home/onos10/research/helloworld_osgi/pom.xml to /home/onos10/.m2/repository/osgi_leaning/helloworld_osgi/1.0-SNAPSHOT/helloworld_osgi-1.0-SNAPSHOT.pom
[INFO] 
[INFO] <<< maven-bundle-plugin:2.5.4:install (default-install) < install @ helloworld_osgi <<<
[INFO] 
[INFO] --- maven-bundle-plugin:2.5.4:install (default-install) @ helloworld_osgi ---
[INFO] Installing osgi_leaning/helloworld_osgi/1.0-SNAPSHOT/helloworld_osgi-1.0-SNAPSHOT.jar
[INFO] Writing OBR metadata
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 11.925 s
[INFO] Finished at: 2016-11-08T16:37:10-08:00
[INFO] Final Memory: 27M/494M
[INFO] ------------------------------------------------------------------------


Start Karaf

apache-karaf-4.0.7/bin$./karaf 
        __ __                  ____      
       / //_/____ __________ _/ __/      
      / ,<  / __ `/ ___/ __ `/ /_        
     / /| |/ /_/ / /  / /_/ / __/        
    /_/ |_|\__,_/_/   \__,_/_/         

  Apache Karaf (4.0.7)

Hit '<tab>' for a list of available commands
and '[cmd] --help' for help on a specific command.
Hit '<ctrl-d>' or type 'system:shutdown' or 'logout' to shutdown Karaf.

you can see there is not any bundle in karaf now

karaf@root()> list
START LEVEL 100 , List Threshold: 50
ID | State | Lvl | Version | Name


Deloy our hello word bundle to karaf 

karaf@root()>  bundle:install mvn:osgi_leaning/helloworld_osgi/1.0-SNAPSHOT
Bundle ID: 52
karaf@root()> list
START LEVEL 100 , List Threshold: 50
ID | State     | Lvl | Version        | Name
--------------------------------------------------------------
52 | Installed |  80 | 1.0.0.SNAPSHOT | helloworld_osgi Bundle


start and stop our hello world budle

karaf@root()> start 52
Starting the bundle
karaf@root()> stop 52
Stopping the bundle

That it enjoy it!.





