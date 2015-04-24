# ProyectosDependientesGradle
Cómo tratar las dependencias entre proyectos con Gradle

#### 1. El proyecto principal contiene en su estructura de directorios al proyecto del que depende.
En este caso deberiamos tener una estructura similar a la siguiente:
```
Proyecto
  |--build.gradle
  |--settings.gradle
  |--Dependencia
  |   |--build.gradle
```

Para agregar la dependencia al proyecto, es necesario indicar a gradle que incluya la dependencia. Para ello, en el fichero *Proyecto > settings.gradle* hay que incluir el siguiente texto:
```
include ':Dependencia'
```
Además, hay que indicar a gradle que compile la dependencia (*Proyecto > build.gradle*):
```
dependencies {
  compile project(':Dependency')
}
```
#### 2. Existen dos proyectos independientes y uno de ellos depende del otro
