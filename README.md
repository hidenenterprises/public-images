# public-images

Imágenes Docker de ejecución e instalación que usan los servidores de HIDENCLOUD, publicadas en `ghcr.io/hidencloud`.

Son imágenes en el formato de Pterodactyl: las de ejecución corren como el usuario `container`, trabajan en `/home/container` y arrancan con un `entrypoint.sh` que expande la variable `STARTUP` del egg; las de `installers/` son los contenedores donde corren los scripts de instalación. Parten de imágenes de la comunidad de Pterodactyl (yolks y las colecciones de Software-Noob y Makai Marcell, como indican las etiquetas `author` de cada Dockerfile). HIDENCLOUD las ha reunido en un solo repo, publica los paquetes con su propio nombre en `ghcr.io/hidencloud`, ha añadido versiones (Java, Python, Node.js, GraalVM y la imagen de Source con SourceMod) y ha corregido paquetes y variables de entorno de la imagen base de Debian.

## Stack

- Dockerfiles multiarquitectura con Docker Buildx y QEMU
- Bases: `debian`, `ubuntu`, `alpine`, `golang`, `eclipse-temurin`, `node`, `python`, `ibm-semeru-runtimes`, `shipilev/openjdk` y las imágenes oficiales de Corretto, Zulu, Liberica y Dragonwell
- GitHub Actions para construir y publicar en GitHub Container Registry

## Funcionamiento

### Catálogo

| Familia | Carpeta | Versiones | Etiqueta | Arquitecturas |
|---|---|---|---|---|
| Sistemas base | `oses/` | alpine, debian | `images:<so>` | amd64, arm64 |
| Instalación | `installers/` | alpine, debian | `installers:<so>` | amd64, arm64 |
| Juegos | `games/` | rust, source, source-sourcemod | `games:<juego>` | amd64 |
| Go | `go/` | 1.14 a 1.17 | `images:go_<v>` | amd64, arm64 |
| Java (Temurin) | `java/` | 8, 11, 16, 17, 18, 19, 21 | `images:java_<v>` | amd64, arm64 |
| Java Corretto | `java-corretto/` | 8, 11, 17, 19, 20, 21 | `images:java_<v>_corretto` | amd64, arm64 |
| Java Zulu | `java-zulu/` | 8, 11, 16, 17, 18, 19, 20, 21, 22 | `images:java_<v>_zulu` | amd64, arm64 |
| Java Dragonwell | `java-dragonwell/` | 8, 11, 17, 21 | `images:java_<v>_dragonwell` | amd64, arm64 |
| Java Liberica | `java-liberica/` | 8, 11, 17, 21, 22 | `images:java_<v>_liberica` | amd64, arm64 |
| Java OpenJ9 | `java-openj9/` | 8, 11, 16, 17, 18, 20, 21 | `images:java_<v>_openj9` | amd64, arm64 (la 16 solo amd64) |
| Java Shenandoah | `java-shenandoah/` | 8, 11, 17, 21 | `images:java_<v>_shenandoah` | amd64, arm64 |
| GraalVM | `graalvm/` | 11, 17, 19; JDK: 17, 20, 21, 22, 23, 24 | `images:graalvm_<v>`, `images:graalvm_<v>-JDK` | amd64, arm64 |
| Node.js | `nodejs/` | 12, 14, 16 a 22 | `images:nodejs_<v>` | amd64, arm64 |
| Python | `python/` | 2.7, 3.6 a 3.12, 3.13-rc | `images:python_<v>` | amd64, arm64 |

Todas las etiquetas cuelgan de `ghcr.io/hidencloud/`, por ejemplo `ghcr.io/hidencloud/images:java_21` o `ghcr.io/hidencloud/games:rust`. Las Java Shenandoah son las compilaciones experimentales de [builds.shipilev.net](https://builds.shipilev.net/); Azul, Corretto y Temurin ya traen Shenandoah GC desde Java 11.

### Entrypoint de Java

El `java/entrypoint.sh` de las imágenes Temurin hace algo más que arrancar. Si encuentra un script de inicio de modpack (`start.sh`, `run.sh`, `ServerStart.sh`, `ServerInstall.sh` o `startserver.sh`), sustituye su `-Xmx` y el de los `user_jvm_args.txt` por `SERVER_MEMORY`, acepta la EULA y lo ejecuta. Si hay un instalador de Forge en la raíz lo ejecuta con `--installServer` y lo renombra a `*_installed.jar`, y hace lo mismo con los instaladores de FTB.

### Source con SourceMod

`games:source-sourcemod` instala y actualiza SourceMod y Metamod en cada arranque si el egg define `SOURCEMOD`. `SM_VERSION` y `MM_VERSION` fijan versiones concretas (una versión no válida vuelve a la última estable) e `INSTALL_PATH` cambia la carpeta de instalación, que por defecto es `csgo`.

## Puesta en marcha

En Go, Java (todas las distribuciones), GraalVM, Node.js y Python el contexto de build es la carpeta de la familia, porque el Dockerfile copia el `entrypoint.sh` que comparten; en `installers/` también es la carpeta de la familia, y en `oses/` y `games/` la de cada imagen:

```bash
docker buildx build --platform linux/amd64,linux/arm64 \
  -f java/21/Dockerfile -t ghcr.io/hidencloud/images:java_21 java
```

## Despliegue

Hay un workflow por familia en `.github/workflows/` (`base.yml`, `installers.yml`, `games.yml`, `go.yml`, `java.yml`, `java-*.yml`, `graalvm.yml`, `nodejs.yml` y `python.yml`). Cada uno construye y publica sus imágenes cuando hay un push a `main` que toca su carpeta, el día 1 de cada mes y a mano desde Actions. Inician sesión en `ghcr.io` con el secreto `REGISTRY_TOKEN`.

Para añadir una versión: crear la carpeta con su `Dockerfile` y añadir la etiqueta a la `matrix` del workflow de la familia. En Python, las versiones como `"3.10"` van entre comillas en la matriz o YAML las lee como `3.1`.

## Licencia y seguridad

Repositorio público de HIDENENTERPRISES SL. Que se pueda ver no da derecho a usarlo: no se permite copiar, usar ni distribuir su contenido sin autorización por escrito. Ver [LICENSE.md](LICENSE.md).

Para reportar una vulnerabilidad o cualquier problema de seguridad, escribe a [security@hidenenterprises.com](mailto:security@hidenenterprises.com). Más detalles en [SECURITY.md](SECURITY.md).
