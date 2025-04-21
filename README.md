# Devcontainer Architecture Presentation

## Description
The following repository can be used to create a presentation based on asciidoc, plantuml, svgs and jpgs (inside a devcontainer). For the presentation itself `revealjs` is used and it can be directly shared via devcontainer in the web. It exports the port 8080 and creates a forwarded address automatically.

## Running the application on a webserver

1. Generate the `index.html`

Whenever an *.adoc file changes or a new svg was added the presentation is updated respectively the svg is copied to the `public` folder. Just use the following command in the terminal:

```
ls slides/*.adoc slides/diagrams/svg/* slides/diagrams/jpg/* | entr sh -c 'asciidoctor-revealjs -r asciidoctor-diagram slides/slides.adoc -o public/index.html && mkdir -p public/diagrams/svg public/diagrams/jpg && cp -r slides/diagrams/svg/* public/diagrams/svg/ && cp -r slides/diagrams/jpg/* public/diagrams/jpg/'
```

2. Run the webserver by the following command in the terminal:

```
http-server public -p 8080
```

## Formatting Content

### SVG Diagrams

For perfect diagram resolutions build the images as svgs and put it inside the `diagrams/svg` folder.

### PlantUML Diagrams

For using plantuml in the slides directly use the following snippet:

```
[plantuml, example, svg, width=120%]
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

