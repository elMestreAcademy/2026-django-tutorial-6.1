# Tutorial de Django 6.1, paso a paso

Proyecto `mysite` con la aplicación de encuestas `polls`, construido siguiendo el [tutorial oficial de Django 6.1](https://docs.djangoproject.com/es/6.1/intro/tutorial01/). Cada sección del tutorial que cambia el código es un commit con su etiqueta: si te atascas, puedes ver cómo queda el proyecto en ese punto y compararlo con el tuyo.

La idea es hacer el tutorial por tu cuenta y usar este repositorio para comprobar, no copiar y pegar.

## Preparar el entorno

Hace falta Python 3.12 o posterior, que es lo que pide Django 6.1.

```bash
git clone https://github.com/elMestreAcademy/2026-django-tutorial-6.1.git
cd 2026-django-tutorial-6.1
python -m venv .venv
.venv\Scripts\activate             # Windows
source .venv/bin/activate          # Linux y macOS
pip install -r requirements.txt
cd djangotutorial
python manage.py migrate
python manage.py createsuperuser
python manage.py runserver
```

La aplicación queda en http://localhost:8000/polls/ y el sitio administrativo, en http://localhost:8000/admin/. La base de datos (`db.sqlite3`) no está en el repositorio: cada uno crea la suya con `migrate` y añade preguntas desde el administrador.

## Moverse entre pasos

```bash
git tag -n                         # lista de pasos con su título
git switch --detach 3.4            # el proyecto tal como queda en el paso 3.4
git diff 3.3 3.4                   # qué cambia en ese paso
git show 3.4                       # el commit del paso, con el enlace a la documentación
git switch main                    # volver al final
```

Después de cambiar de paso, ejecuta `python manage.py migrate` desde `djangotutorial` si el paso añade migraciones. Para los pasos anteriores a la parte 8 no hace falta desinstalar la barra de depuración: simplemente no se usa.

## Pasos

| Etiqueta | Parte | Sección del tutorial                                                                                                                                                               |
| -------- | ----: | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `0.0`    |     - | Punto de partida: README, `.gitignore` y `requirements.txt`                                                                                                                        |
| `1.1`    |     1 | [Creando un proyecto](https://docs.djangoproject.com/es/6.1/intro/tutorial01/#creating-a-project)                                                                                  |
| `1.2`    |     1 | [Creando la aplicación encuestas](https://docs.djangoproject.com/es/6.1/intro/tutorial01/#creating-the-polls-app)                                                                  |
| `1.3`    |     1 | [Escriba su primera vista](https://docs.djangoproject.com/es/6.1/intro/tutorial01/#write-your-first-view)                                                                          |
| `2.1`    |     2 | [Configuración de la base de datos](https://docs.djangoproject.com/es/6.1/intro/tutorial02/#database-setup)                                                                        |
| `2.2`    |     2 | [Creando modelos](https://docs.djangoproject.com/es/6.1/intro/tutorial02/#creating-models)                                                                                         |
| `2.3`    |     2 | [Activando los modelos](https://docs.djangoproject.com/es/6.1/intro/tutorial02/#activating-models)                                                                                 |
| `2.4`    |     2 | [Jugando con la API](https://docs.djangoproject.com/es/6.1/intro/tutorial02/#playing-with-the-api)                                                                                 |
| `2.5`    |     2 | [Haga que la aplicación encuesta se pueda modificar en el sitio administrativo](https://docs.djangoproject.com/es/6.1/intro/tutorial02/#make-the-poll-app-modifiable-in-the-admin) |
| `3.1`    |     3 | [Escribiendo más vistas](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#writing-more-views)                                                                               |
| `3.2`    |     3 | [Escriba vistas que realmente hagan algo](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#write-views-that-actually-do-something)                                          |
| `3.3`    |     3 | [Escriba vistas que realmente hagan algo: plantilla](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#write-views-that-actually-do-something)                               |
| `3.4`    |     3 | [Un atajo: render()](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#a-shortcut-render)                                                                                    |
| `3.5`    |     3 | [Levantar un error 404](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#raising-a-404-error)                                                                               |
| `3.6`    |     3 | [Un atajo: get_object_or_404()](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#a-shortcut-get-object-or-404)                                                              |
| `3.7`    |     3 | [Utilice el sistema de plantillas](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#use-the-template-system)                                                                |
| `3.8`    |     3 | [Quitar URLs codificadas en las plantillas](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#removing-hardcoded-urls-in-templates)                                          |
| `3.9`    |     3 | [Asignando los nombres de URLs](https://docs.djangoproject.com/es/6.1/intro/tutorial03/#namespacing-url-names)                                                                     |
| `4.1`    |     4 | [Escriba un formulario sencillo](https://docs.djangoproject.com/es/6.1/intro/tutorial04/#write-a-minimal-form)                                                                     |
| `4.2`    |     4 | [Escriba un formulario sencillo: resultados](https://docs.djangoproject.com/es/6.1/intro/tutorial04/#write-a-minimal-form)                                                         |
| `4.3`    |     4 | [Utilice vistas genéricas: menos código es mejor](https://docs.djangoproject.com/es/6.1/intro/tutorial04/#use-generic-views-less-code-is-better)                                   |
| `5.1`    |     5 | [Cree una prueba para exponer el error](https://docs.djangoproject.com/es/6.1/intro/tutorial05/#create-a-test-to-expose-the-bug) (el test falla a propósito)                       |
| `5.2`    |     5 | [Solucionando el error](https://docs.djangoproject.com/es/6.1/intro/tutorial05/#fixing-the-bug)                                                                                    |
| `5.3`    |     5 | [Pruebas más exhaustivas](https://docs.djangoproject.com/es/6.1/intro/tutorial05/#more-comprehensive-tests)                                                                        |
| `5.4`    |     5 | [Mejorando nuestra vista](https://docs.djangoproject.com/es/6.1/intro/tutorial05/#improving-our-view)                                                                              |
| `5.5`    |     5 | [Probando nuestra nueva vista](https://docs.djangoproject.com/es/6.1/intro/tutorial05/#testing-our-new-view)                                                                       |
| `5.6`    |     5 | [Probando la DetailView](https://docs.djangoproject.com/es/6.1/intro/tutorial05/#testing-the-detailview)                                                                           |
| `6.1`    |     6 | [Personalice la apariencia de su aplicación](https://docs.djangoproject.com/es/6.1/intro/tutorial06/#customize-your-app-s-look-and-feel)                                           |
| `6.2`    |     6 | [Agregando una imagen de fondo](https://docs.djangoproject.com/es/6.1/intro/tutorial06/#adding-a-background-image)                                                                 |
| `7.1`    |     7 | [Personalice el formulario del sitio administrativo](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#customize-the-admin-form)                                             |
| `7.2`    |     7 | [Personalice el formulario del sitio administrativo: fieldsets](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#customize-the-admin-form)                                  |
| `7.3`    |     7 | [Agregando objetos relacionados](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#adding-related-objects)                                                                   |
| `7.4`    |     7 | [Agregando objetos relacionados: ChoiceInline](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#adding-related-objects)                                                     |
| `7.5`    |     7 | [Agregando objetos relacionados: TabularInline](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#adding-related-objects)                                                    |
| `7.6`    |     7 | [Personalice la lista de cambios del sitio administrativo](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#customize-the-admin-change-list)                                |
| `7.7`    |     7 | [Personalice la lista de cambios: @admin.display](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#customize-the-admin-change-list)                                         |
| `7.8`    |     7 | [Personalice la lista de cambios: filtros y búsqueda](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#customize-the-admin-change-list)                                     |
| `7.9`    |     7 | [Personalizando las plantillas de su proyecto](https://docs.djangoproject.com/es/6.1/intro/tutorial07/#customizing-your-project-s-templates)                                       |
| `8.1`    |     8 | [Instalando Django Debug Toolbar](https://docs.djangoproject.com/es/6.1/intro/tutorial08/#installing-django-debug-toolbar)                                                         |

## Qué no tiene commit propio

Las secciones que solo se hacen en la consola o en el navegador no cambian archivos: el servidor de desarrollo, el usuario administrador, el resto de "Jugando con la API" en `python manage.py shell`, el cliente de prueba de Django y la página de índice del administrador, que el tutorial deja como idea. La sección "Ideas para más pruebas" propone aplicar a `ResultsView` el mismo filtro que a `DetailView`: queda como ejercicio.

## Notas

- **Paso 5.1:** el test falla a propósito (`AssertionError: True is not False`). Es el error que el tutorial descubre en ese paso y corrige en el 5.2.
- **Zona horaria:** el paso 2.1 pone `TIME_ZONE = 'Europe/Madrid'`, como pide el tutorial para cada uno su zona.
- **Comillas:** `settings.py` y `mysite/urls.py` los genera Django con comillas simples, y al editarlos se mantiene ese estilo. El resto del código va tal cual lo escribe el tutorial, con comillas dobles.
- **Imagen de fondo (6.2):** el tutorial deja elegir cualquier imagen; `background.png` es un cuadriculado propio.
- **Parte 8:** el tutorial remite a la [guía de instalación de Django Debug Toolbar](https://django-debug-toolbar.readthedocs.io/en/latest/installation.html), que es la que se sigue aquí (versión 8.0), incluido el paso opcional para no activarla al ejecutar los tests. La barra solo aparece en páginas con etiqueta `<body>`: se ve en el administrador, no en las plantillas de `polls`, que no la tienen.
- **`SECRET_KEY`:** es la que genera `startproject`, válida solo para desarrollo.

El código procede del tutorial oficial de Django, de la Django Software Foundation y sus colaboradores.
