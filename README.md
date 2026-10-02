# public-images

Docker runtime and install images used by HIDENCLOUD's servers, published to `ghcr.io/hidencloud`.

They're images in the Pterodactyl format: the runtime ones run as the `container` user, work in `/home/container` and start with an `entrypoint.sh` that expands the egg's `STARTUP` variable; the ones in `installers/` are the containers where install scripts run. They're based on Pterodactyl community images (yolks and the Software-Noob and Makai Marcell collections, as the `author` labels in each Dockerfile show). HIDENCLOUD has gathered them into a single repo, publishes the packages under its own name at `ghcr.io/hidencloud`, has added versions (Java, Python, Node.js, GraalVM and the Source image with SourceMod) and has fixed packages and environment variables in the Debian base image.

## Stack

- Multi-arch Dockerfiles with Docker Buildx and QEMU
- Bases: `debian`, `ubuntu`, `alpine`, `golang`, `eclipse-temurin`, `node`, `python`, `ibm-semeru-runtimes`, `shipilev/openjdk` and the official Corretto, Zulu, Liberica and Dragonwell images
- GitHub Actions to build and publish to GitHub Container Registry

## How it works

### Catalog

| Family | Folder | Versions | Tag | Architectures |
|---|---|---|---|---|
| Base systems | `oses/` | alpine, debian | `images:<os>` | amd64, arm64 |
| Install | `installers/` | alpine, debian | `installers:<os>` | amd64, arm64 |
| Games | `games/` | rust, source, source-sourcemod | `games:<game>` | amd64 |
| Go | `go/` | 1.14 to 1.17 | `images:go_<v>` | amd64, arm64 |
| Java (Temurin) | `java/` | 8, 11, 16, 17, 18, 19, 21 | `images:java_<v>` | amd64, arm64 |
| Java Corretto | `java-corretto/` | 8, 11, 17, 19, 20, 21 | `images:java_<v>_corretto` | amd64, arm64 |
| Java Zulu | `java-zulu/` | 8, 11, 16, 17, 18, 19, 20, 21, 22 | `images:java_<v>_zulu` | amd64, arm64 |
| Java Dragonwell | `java-dragonwell/` | 8, 11, 17, 21 | `images:java_<v>_dragonwell` | amd64, arm64 |
| Java Liberica | `java-liberica/` | 8, 11, 17, 21, 22 | `images:java_<v>_liberica` | amd64, arm64 |
| Java OpenJ9 | `java-openj9/` | 8, 11, 16, 17, 18, 20, 21 | `images:java_<v>_openj9` | amd64, arm64 (16 is amd64 only) |
| Java Shenandoah | `java-shenandoah/` | 8, 11, 17, 21 | `images:java_<v>_shenandoah` | amd64, arm64 |
| GraalVM | `graalvm/` | 11, 17, 19; JDK: 17, 20, 21, 22, 23, 24 | `images:graalvm_<v>`, `images:graalvm_<v>-JDK` | amd64, arm64 |
| Node.js | `nodejs/` | 12, 14, 16 to 22 | `images:nodejs_<v>` | amd64, arm64 |
| Python | `python/` | 2.7, 3.6 to 3.12, 3.13-rc | `images:python_<v>` | amd64, arm64 |

All tags hang off `ghcr.io/hidencloud/`, for example `ghcr.io/hidencloud/images:java_21` or `ghcr.io/hidencloud/games:rust`. The Java Shenandoah images are the experimental builds from [builds.shipilev.net](https://builds.shipilev.net/); Azul, Corretto and Temurin already ship Shenandoah GC since Java 11.

### Java entrypoint

The `java/entrypoint.sh` in the Temurin images does more than start the server. If it finds a modpack start script (`start.sh`, `run.sh`, `ServerStart.sh`, `ServerInstall.sh` or `startserver.sh`), it replaces its `-Xmx` and the one in `user_jvm_args.txt` with `SERVER_MEMORY`, accepts the EULA and runs it. If there's a Forge installer in the root it runs it with `--installServer` and renames it to `*_installed.jar`, and it does the same with FTB installers.

### Source with SourceMod

`games:source-sourcemod` installs and updates SourceMod and Metamod on every start if the egg defines `SOURCEMOD`. `SM_VERSION` and `MM_VERSION` pin specific versions (an invalid version falls back to the latest stable) and `INSTALL_PATH` changes the install folder, which defaults to `csgo`.

## Getting started

For Go, Java (all distributions), GraalVM, Node.js and Python the build context is the family folder, because the Dockerfile copies the `entrypoint.sh` they share; for `installers/` it's also the family folder, and for `oses/` and `games/` it's each image's folder:

```bash
docker buildx build --platform linux/amd64,linux/arm64 \
  -f java/21/Dockerfile -t ghcr.io/hidencloud/images:java_21 java
```

## Deployment

There's one workflow per family in `.github/workflows/` (`base.yml`, `installers.yml`, `games.yml`, `go.yml`, `java.yml`, `java-*.yml`, `graalvm.yml`, `nodejs.yml` and `python.yml`). Each one builds and publishes its images when there's a push to `main` that touches its folder, on the 1st of every month, and by hand from Actions. They log in to `ghcr.io` with the `REGISTRY_TOKEN` secret.

To add a version: create the folder with its `Dockerfile` and add the tag to the `matrix` of the family's workflow. In Python, versions like `"3.10"` go in quotes in the matrix or YAML reads them as `3.1`.

## License and security

Public repository of HIDENENTERPRISES SL. Being able to see it doesn't give you the right to use it: you may not copy, use or distribute its content without written permission. See [LICENSE.md](LICENSE.md).

To report a vulnerability or any other security issue, email [security@hidenenterprises.com](mailto:security@hidenenterprises.com). See [SECURITY.md](SECURITY.md) for details.
