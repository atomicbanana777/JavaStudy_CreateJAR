# JavaStudy_CreateJAR
Create a sample executable .jar file

To compile and create a JAR file, you need
## 1. install JAVA JDK so that you can run java command e.g. javac, jar, java
## 2. clone the repository

`git clone https://github.com/atomicbanana777/JavaStudy_CreateJAR.git`

`ls -R`

```
.:
JavaStudy_CreateJAR

./JavaStudy_CreateJAR:
MANIFEST.mf  README.md  src

./JavaStudy_CreateJAR/src:
main

./JavaStudy_CreateJAR/src/main:
CreateJAR.java
```

## 3. run java compile command in the same directory of step 2
   `javac -d bin src/main/*.java`

   The above command will compile .java into .class and put it in a folder "bin"
   - javac = java compile
   - -d bin = create directory named "bin"
   
## 4. run jar command to create jar file
   below are linux command
   
   `cd bin ; jar cvfe ../CreateJAR.jar main.CreateJAR main/*.class ; cd ..`
   
   or
   
   `cd bin ; jar cvfm ../CreateJAR.jar ../MANIFEST.mf main/*.class ; cd ..`

   - cd bin = You change directory to "bin"
   - jar = run jar command
   - c = create
   - v = verbose
   - f = file
   - m = manifest file
   - e = entry point

    The first command is to create .jar file by providing entry point so that you don't need MANIFEST.mf file
    It will auto create a MANIFEST.mf file for you with main class = main.CreateJAR

   e.g.

    `cd bin ; jar cvfe ../CreateJAR.jar main.CreateJAR main/*.class ; cd ..`

    The second command is to create .jar file by providing MANIFEST.mf

    e.g.

    `cd bin ; jar cvfm ../CreateJAR.jar ../MANIFEST.mf main/*.class ; cd ..`

    You cannot run the create jar command anywhere you like that why we need "cd bin"
    The directory that you run is very important otherwise the JAR cannot execute
    You have to run it in the correct directory

    For example:
   
    you have /bin/main/CreateJAR.class where package is main
    1. you go to the default package which is bin

   `cd bin`

    2. run the command with m or e 
    
    `jar cvfm ../CreateJAR.jar ../MANIFEST.mf main/*.class`

    `jar cvfe ../CreateJAR.jar main.CreateJAR main/*.class`

     And your jar file will look something like this

    `jar -tvf CreateJAR.jar`
   ```
        0 Sun Feb 02 18:36:40 HKT 2025 META-INF/
       82 Sun Feb 02 18:36:40 HKT 2025 META-INF/MANIFEST.MF
      429 Sun Feb 02 18:03:10 HKT 2025 main/CreateJAR.class
   ```
    
    The main point is you have to maintain the structure of main/CreateJAR.class inside the JAR
    even though your folder structure is bin/main/CreateJAR.class
    otherwise, the JAR cannot find your class file
   
## 5. execute .jar file

   e.g.
   
    `java -jar CreateJAR.jar`

   it will output "Hello World!"
