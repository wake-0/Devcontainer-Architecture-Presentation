FROM mcr.microsoft.com/devcontainers/java:1-21-bullseye


RUN apt update
# Install graphviz
RUN apt install -y graphviz
# Download plantuml
RUN rm -rf .tools
RUN mkdir .tools
RUN wget -O /usr/local/bin/plantuml.jar https://github.com/plantuml/plantuml/releases/download/v1.2025.2/plantuml-1.2025.2.jar
ENV PLANTUML_JAR_PATH=/usr/local/bin/plantuml.jar
ENV GRAPHVIZ_DOT_EXECUTABLE=/usr/bin/dot

# Install ruby, asciidoctor, etc. for creating a presentation
RUN apt install -y ruby-full nodejs npm entr && \
    gem install asciidoctor asciidoctor-revealjs asciidoctor-diagram && \
    npm install -g http-server


