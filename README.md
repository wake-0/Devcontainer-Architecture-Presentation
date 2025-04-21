# Howto

### SVG Diagrams

For perfect diagram resolutions build the images as svgs and put it inside the `diagrams/svg` folder.

### PlantUML Diagrams

For using plantuml in the slides directly use the following snippet:

```
[plantuml, project-structure, svg, width=120%]
....
@startuml
Controller --> Service
Service --> Repository
@enduml
....
```

When the plantuml is placed inside a file in the folder `diagrams/puml` use the following include snippet:

```
[plantuml, mindmap-example, svg]
....
include::diagrams/plantuml/agenda-full.puml[]
....
```

### Chapters

For different chapters in the presentation use different sub documents and include them inside the slides.adoc.

### Running the application on a webserver

1. Generate the `index.html`

Whenever an *.adoc file changes or a new svg was added the presentation is updated respectively the svg is copied to the `public` folder.

```
ls slides/*.adoc slides/diagrams/svg/* slides/diagrams/jpg/* | entr sh -c 'asciidoctor-revealjs -r asciidoctor-diagram slides/slides.adoc -o public/index.html && mkdir -p public/diagrams/svg public/diagrams/jpg && cp -r slides/diagrams/svg/* public/diagrams/svg/ && cp -r slides/diagrams/jpg/* public/diagrams/jpg/'
```

2. Run the webserver 

```
http-server public -p 8080
```