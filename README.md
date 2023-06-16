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
