## Help Within Genvisis

Help for specific Genvisis steps can be found by running:


```
    java -jar genvisis.jar org.genvisis.cnv.filesys.[stepName] -h 
    # or
    java -jar genvisis.jar org.genvisis.cnv.filesys.[stepName]
```


To view what commands Genvisis can use from the command line, run:


```
    java -jar genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow
```


This command yields:


```
    1)  java -jar ~/genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow [CONFIG FILE]
    2)  java -jar ~/genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow check [CONFIG FILE]
    3)  java -jar ~/genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow targets [PROJECT PROPERTIES FILE]
    4)  java -jar ~/genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow create [PROJECT PROPERTIES FILE] [TARGET ID ... ]
    5)  java -jar ~`/genvisis.jar org.genvisis.cnv.workflow.GenvisisWorkflow [TARGET ID] [PROJECT PROPERTIES FILE]

    Option 1) Run Genvisis Workflow using the given config file
    Option 2) Check if a given workflow file can be run
    Option 3) List which targets are available for a given project
    Option 4) Create a config file for the given project and include default arguments for any specified targets
    Option 5) Print out the target key and default arguments, which can be customized and added to a config file
```


[CONFIG FILE] is a .toml file.
