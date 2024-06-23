# Some tricky questions
1) Does spring boot support using both properties and yml files at the same time?

   Yes you can use both at same time in same project. When you use both YML and properties at same time, say for example **application.yml** and **application.properties** at same time in same project, first application.yml will be loaded, later overrided by application.properties.
