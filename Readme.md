# Template para guias Usach en Quarto
Un simple template que agrega información en el header del archivo pdf generado usando el formato quarto `.qmd`

## Requisitos
Se necesita tener instalado localmente [quarto](https://quarto.org/) y [miktex](https://miktex.org/). Opcionalmente se recomienda tener instalado el complemento para [vscode](https://code.visualstudio.com/) para [archivos quarto](https://marketplace.visualstudio.com/items?itemName=quarto.quarto)

## Uso
- En el directorio del documento `.qmd`, copiar la carpeta `template` del repositorio
- En el header del documento quarto agregar el header:

```yaml
---
title: "Template para guias Usach en Quarto"
author: "Author"
date: 2024-05-29
fecha_entrega: 2024-06-01
universidad: 
    - Universidad de Santiago de Chile
    - Departamento - Carrera
curso: Curso
laboratorio:
    - Laboratorio XY.
    - Prueba
logo: "template/logo_usach.eps"
latex-tinytex: false
format:
  pdf:
    toc: false
    colorlinks: true
    number-sections: true
    papersize: letter
    pdf-engine: pdflatex
    documentclass: scrartcl
    template-partials:
        - ./template/before-title.tex
        - ./template/before-body.tex
        - ./template/after-body.tex
---
```

Donde las variables agregadas (opcionales) son:

- **fecha_entrega**: Agrega una última sección con la fecha de entrega. El texto agregado puede ser editado en la carpeta `template`, en el archivo `after_body.tex` dentro del condicional `if`.
- **universidad**: Multilinea. Permite agregar la información de la universidad, factultad, carrera, etc. La información aparece en la parte central superior del header.
- **curso**: Nombre del curso. Aparecerá en la primera linea central de la información del header
- **laboratorio**: Multilinea. Agrega un texto al costado superior derecho. Pensado para agregar la información de los laboratorios o de las pruebas. 
- **logo**: Logo en formato `eps` que será agregado en la esquina superior izquierda del header.

# Ejemplo
Ver el archivo [test.qmd](test.qmd) como un ejemplo completo:

![Ejemplo de pdf generado con el template](test.png)

# TODO
- [ ] Agregar variable para cambiar el color de las lineas de separación del header/footer.
- [ ] Agregar el mensaje final en un archivo separado, que no dependa del `if` utilizado por `pandoc`.
- [ ] Agregar el template de forma global para los archivos quarto.
