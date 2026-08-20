# Taller MBA UC — sistema de agentes

Esto es el piso del taller. **No hay ningun sistema hecho aca**: hay los datos que
no vas a poder conseguir en cuatro horas, el marco para saber que estas
construyendo, y una skill que te ayuda a decidir el diseno antes de escribir codigo.

| Archivo | Que es |
|---|---|
| `marco-de-agentes.md` | Que es un agente y que es un sistema de agentes. Trae una plantilla para completar por cada agente y un ejemplo de como se ve completada. |
| `supuestos.yaml` | Tarifa y ocupacion por tipologia con estacionalidad de 12 meses, gastos comunes, costos de operacion, equipamiento y parametros del credito. Son un **piso**, no una verdad. |
| `skills/entrevistador-de-diseno/` | Una skill que entrevista con insistencia hasta que el diseno queda cerrado. |

---

## 1. Abri la terminal

| | Como |
|---|---|
| **Mac** | `Cmd + Espacio`, escribi **Terminal**, Enter |
| **Windows** | Tecla Windows, escribi **PowerShell**, Enter |

## 2. Verifica que tenes lo necesario

| | Mac | Windows |
|---|---|---|
| Git | `git --version` | `git --version` |
| Python | `python3 --version` | `python --version` |

Los dos tienen que responder con un numero de version. Si alguno dice *command not
found* o *no se reconoce*, instalalo antes de seguir: Git en
[git-scm.com](https://git-scm.com), Python en [python.org](https://python.org).

> **Windows:** al instalar Python, marca la casilla **"Add Python to PATH"** en la
> primera pantalla del instalador. Si no la marcas, `python` no va a responder y vas
> a tener que reinstalar.

## 3. Baja los archivos

Igual en los dos sistemas. Parate en la carpeta donde quieras trabajar y corre:

```
git clone https://github.com/bnavoni/taller-mba-uc.git
cd taller-mba-uc
```

## 4. Instala la skill

Aca **si** cambia segun el sistema. La skill es una carpeta que tiene que quedar
dentro de `.claude/skills/` de tu proyecto.

**Mac**
```
mkdir -p .claude/skills
cp -R skills/entrevistador-de-diseno .claude/skills/
```

**Windows (PowerShell)**
```
New-Item -ItemType Directory -Force .claude\skills | Out-Null
Copy-Item -Recurse skills\entrevistador-de-diseno .claude\skills\
```

Para confirmar que quedo, abri Claude Code en esta carpeta y pedile que liste las
skills que tiene cargadas.

## 5. Arranca

```
claude
```

Y usa la skill para cerrar el diseno antes de escribir nada.

---

## Si algo se rompe

**`./algo.sh` no funciona en Windows.** Los scripts `.sh` son de Mac y Linux. Por eso
aca no hay ninguno: todos los comandos estan escritos para los dos sistemas.

**PowerShell no me deja correr un script.** Windows bloquea scripts por defecto. En
este repo no hace falta ninguno, pero si mas adelante necesitas uno, se habilita solo
para esa ventana con `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass`.

**`python` funciona pero `python3` no, o al reves.** En Mac suele ser `python3`; en
Windows suele ser `python`. Usa el que responda.

**Necesito un entorno virtual de Python.** Se crea igual pero se activa distinto:

| | Crear | Activar |
|---|---|---|
| Mac | `python3 -m venv .venv` | `source .venv/bin/activate` |
| Windows | `python -m venv .venv` | `.venv\Scripts\Activate.ps1` |

**Quiero actualizar los archivos.** Si se corrige algo antes de la clase, `git pull`
dentro de esta carpeta trae la version nueva sin volver a clonar.
