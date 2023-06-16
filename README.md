<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.arte

Parte del código del sitio web es de código abierto, bienvenido a ayudar a optimizar la traducción.

## código de front-end

* [código de front-end](https://github.com/xxai-art/web)
* [Paquetes de idiomas para el sitio en su conjunto](https://github.com/xxai-art/web/tree/main/i18n)
* [Paquetes de idiomas para módulos de inicio de sesión](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Sitio web Documentación multilingüe](https://github.com/xxai-doc)

El lenguaje de programación front-end es [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , que agrega algunas funciones basadas en la sintaxis de coffeescript, consulte [./coffee_plus.md](./coffee_plus.md) .

## Internacionalización de sitios web y documentos

Construir sobre los siguientes 3 proyectos

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  El sufijo es `.mdt` , puede usar una sintaxis similar a `<+ ./coffee_plus/import.js>` para hacer referencia a archivos externos y generar rebajas con el sufijo `.md` .

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  La traducción de Markdown no traducirá códigos ni enlaces, y almacenará en caché las oraciones traducidas. Si se modifica la traducción pero no se modifica el texto original, ejecutarlo de nuevo no sobrescribirá la modificación de la traducción.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Archivos de idioma para traducir sitios web generados `yaml` .

### Instrucciones de automatización de traducción de documentos

Ver repositorio [xxai-art/doc](https://github.com/xxai-art/doc)

Se recomienda instalar nodejs, [direnv](https://direnv.net) y [bun](https://github.com/oven-sh/bun) primero, y luego ejecutar `direnv allow` después de ingresar al directorio.

Para evitar almacenes demasiado grandes traducidos a cientos de idiomas, creé un almacén de código separado para cada idioma y creé una organización para almacenar este almacén.

Establecer la variable de entorno `GITHUB_ACCESS_TOKEN` y luego ejecutar [create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) creará automáticamente el almacén.

Por supuesto, también puedes ponerlo en un almacén.

Referencia del script de traducción [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

El código del script se interpreta de la siguiente manera:

[bunx](https://bun.sh/docs/cli/bunx) es un reemplazo para npx, que es más rápido. Por supuesto, si no tiene instalado bun, puede usar `npx` en su lugar.

`bunx mdt zh` representa `.mdt` en el directorio zh como `.md` , consulte los 2 archivos vinculados a continuación

* [cafe_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [cafe_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` es el código central para la traducción (si solo tiene instalado `nodejs` , pero `bun` y `direnv` no están instalados, también puede ejecutar `npx i18n` para traducir).

Analizará [i18n.yml](https://github.com/xxai-art/doc/blob/main/i18n.yml) , la configuración de `i18n.yml` en este documento es la siguiente:

```
en:
zh: ja ko en
```

El significado es: traducción del chino al japonés, coreano, inglés, traducción del inglés a todos los demás idiomas. Si solo desea admitir chino e inglés, puede escribir `zh: en` .

El último es [gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , que extrae el contenido entre el título principal y el primer subtítulo del `README.md` de cada idioma para generar una entrada `README.md` . El código es muy simple, puedes verlo tú mismo.

La API de Google se utiliza para la traducción gratuita. Si no puede acceder a Google, configure y configure un proxy, como:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

El script de traducción generará un caché de traducción en el directorio `.i18n` , verifíquelo con `git status` y agréguelo al repositorio de código para evitar traducciones repetidas.
