# SOCIAL OPLESK
### 
<br/>

# Implementar test en github actions CI/CD

<br/>

**El proceso a realizar se hace sobre un script en python3**

**Requisitos previos**

- Conocer de python3
- Cuenta en github.com
<br/>

### 🟢 Paso 1
- crear repositorio en github
- elaborar el flujo gitflow de ramas
```
- main
- release
- develop
```

### 🟢 Paso 2
- idear la rama feat/test_sumar
- adjuntar el script de test_sumar.py en feat/test_sumar
```
📜 archivo: test_sumar.py

from sumar import sumar

def test_suma_valida():
    resultado = sumar(8, 7)  # = 15
    assert 0 <= resultado <= 20, f"Resultado {resultado} fuera del rango válido"
```


### 🟢 Paso 3
- implementar  ./github/workflows/test_sumar.yml
- anexar el script del job en test_sumar.yml

```
📜 archivo: .github/workflows/test_sumar.yml


name: test-sumar

on: 
  pull_request:
    branches:
      - develop
      - 'feat/**'

jobs:
  testing-sumar:
    runs-on: ubuntu-24.04
    steps:
      - name: descargar app
        uses: actions/checkout@v4

      - name: instalar python3.12
        uses: actions/setup-python@v5
        with:
          python-version: '3.12'

      - name: instalar pytest
        run: pip install pytest

      - name: ejecutar test sumar
        run: pytest test_sumar.py -v
```

### 🟢 Paso 4
- clonar el repositorio en local
- ejecutar git fetch origin
- git switch --track origin/feat/test_sumar

### 🟢 Paso 5
- crear el archivo sumar.py
- adjuntar el script de sumar.py en sumar.py
```
📜 archivo: sumar.py

def sumar(a, b):
    return a + b
```

### 🟢 Paso 6
- ejecuta git push origin feat/test_sumar
- merge pull request con develop


---
<h3 align="center">SOCIAL OPLESK</h3>
