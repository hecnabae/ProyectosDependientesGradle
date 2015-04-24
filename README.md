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
  compile project(':Dependencia')
}
```
#### 2. Existen dos proyectos independientes y uno de ellos depende del otro
En este caso la estructura variará, el proyecto principal ya no contiene al proyecto del que depende. La siguiente estructura es un posible ejemplo:
```
Proyecto
  |--build.gradle
  |--settings.gradle
Dependencia
  |--build.gradle
  |--settings.gradle
```
En primer lugar, indicamos a gradle que incluya la dependencia y, además dónde se encuentra la dependencia. *Proyecto > settings.gradle*:
```
include ':Dependencia'
project(':Dependencia').projectDir = new File(settingsDir, '../Dependencia')
```
E indicamos a gradle que debe compilar dicha dependencia *Proyecto > build.gradle*:
```
dependencies {
  compile project(':Dependencia')
}
```
