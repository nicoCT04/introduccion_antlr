# Laboratorio 1: Introducción a ANTLR

**Curso:** Construcción de Compiladores 2
**Autor:** Nicolás Concuá
**Modalidad:** Individual

Este repositorio contiene mi entrega del Laboratorio 1, donde se trabaja con **ANTLR**
(generador de analizadores léxicos y sintácticos) sobre la gramática de ejemplo `MiniLang`.

---

## 📂 Contenido

| Archivo / carpeta        | Descripción                                                        |
| ------------------------ | ------------------------------------------------------------------ |
| `program/MiniLang.g4`    | Gramática de ANTLR (lexer + parser).                               |
| `program/Driver.py`      | Punto de entrada: lee un archivo y lo analiza con lexer y parser.  |
| `program/program_test.txt` | Archivo de prueba de entrada.                                    |
| `Analisis_Lab1.docx`     | **Entregable 1:** análisis de la gramática y del Driver.          |
| `Dockerfile`             | Entorno reproducible con ANTLR + Python.                          |
| `antlr-4.13.1-complete.jar` | Binario de ANTLR usado para generar lexer/parser.             |

---

## Video (Entregable 2)

**Link:** https://youtu.be/rrDNdrvi66g

En el video se muestra:
- Un caso donde el programa **compila correctamente** (sin salida).
- Un caso donde **falla la compilación** (error de sintaxis de ANTLR).
- Comentarios sobre el funcionamiento de la gramática y el Driver.

---

## Cómo ejecutar

### Opción A — con Docker

```bash
docker build --rm . -t lab1-image && docker run --rm -ti -v "$(pwd)/program":/program lab1-image
```

Dentro del contenedor:

```bash
antlr -Dlanguage=Python3 MiniLang.g4     # genera MiniLangLexer.py y MiniLangParser.py
python3 Driver.py program_test.txt        # analiza el archivo de prueba
```

### Opción B — ANTLR local

```bash
cd program
java -jar ../antlr-4.13.1-complete.jar -Dlanguage=Python3 MiniLang.g4
pip install antlr4-python3-runtime
python3 Driver.py program_test.txt
```

### Interpretación del resultado

- ✅ Sin salida  → el archivo es **sintácticamente correcto**.
- ❌ Con salida (`line X:Y ...`) → hay un **error de sintaxis**.

---

##  Análisis

El análisis completo de la gramática ANTLR y del `Driver.py` está en
**[`Analisis_Lab1.docx`](./Analisis_Lab1.docx)**.
