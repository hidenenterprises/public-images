# HidenCloud Images

## Base OSes [AMD64/ARM64]

* [`alpine`](https://github.com/hidencloud/images/tree/main/oses/alpine)
	* `ghcr.io/hidencloud/images:alpine`
* [`debian`](https://github.com/hidencloud/images/tree/main/oses/debian)
	* `ghcr.io/hidencloud/images:debian`

## Games [AMD64]

* [`rust`](https://github.com/hidencloud/images/tree/main/games/rust)
	* `ghcr.io/pterodactyl/games:rust`
* [`source`](https://github.com/hidencloud/images/tree/main/games/source)
	* `ghcr.io/pterodactyl/games:source`
* [`Source with sourcemod`](https://github.com/hidencloud/images/tree/main/games/source-sourcemod)
    * `ghcr.io/pterodactyl/games:source-sourcemod`

  Optionally installs and updates SourceMod/Metamod on each server startup. Requires adding egg environment variable `SOURCEMOD`.

  ![image](https://user-images.githubusercontent.com/10975908/159126935-2e3f2883-3b89-4395-b28d-ab23dad0e5f8.png)

  Custom versions can be set with the use of `SM_VERSION` and `MM_VERSION` variables. Invalid versions will default to the latest stable version. Default path is set to csgo and can be overridden with `INSTALL_PATH` egg environment variable.

## GoLang [AMD64/ARM64]

* [`go1.14`](https://github.com/hidencloud/images/tree/main/go/1.14)
	* `ghcr.io/hidencloud/images:go_1.14`
* [`go1.15`](https://github.com/hidencloud/images/tree/main/go/1.15)
	* `ghcr.io/hidencloud/images:go_1.15`
* [`go1.16`](https://github.com/hidencloud/images/tree/main/go/1.16)
	* `ghcr.io/hidencloud/images:go_1.16`
* [`go1.17`](https://github.com/hidencloud/images/tree/main/go/1.17)
	* `ghcr.io/hidencloud/images:go_1.17`

## Minecraft (Java) [AMD64/ARM64]

* [`java8`](https://github.com/hidencloud/images/tree/main/java/8)
	* `ghcr.io/hidencloud/images:java_8`
* [`java11`](https://github.com/hidencloud/images/tree/main/java/11)
	* `ghcr.io/hidencloud/images:java_11`
* [`java16`](https://github.com/hidencloud/images/tree/main/java/16)
	* `ghcr.io/hidencloud/images:java_16`
* [`java17`](https://github.com/hidencloud/images/tree/main/java/17)
	* `ghcr.io/hidencloud/images:java_17`
* [`java18`](https://github.com/hidencloud/images/tree/main/java/18)
	* `ghcr.io/hidencloud/images:java_18`
* [`java19`](https://github.com/hidencloud/images/tree/main/java/19)
	* `ghcr.io/hidencloud/images:java_19`
* [`java21`](https://github.com/hidencloud/images/tree/main/java/21)
	* `ghcr.io/hidencloud/images:java_21`

## Installation Images [AMD64/ARM64]

* [`alpine-install`](https://github.com/hidencloud/images/tree/main/installers/alpine)
	* `ghcr.io/hidencloud/installers:alpine`
* [`debian-install`](https://github.com/hidencloud/images/tree/main/installers/debian)
	* `ghcr.io/hidencloud/installers:debian`

## Node.js [AMD64/ARM64]

- [Nodejs 12](https://github.com/hidencloud/images/tree/main/nodejs/12)
	- `ghcr.io/hidencloud/images:nodejs_12`
- [Nodejs 14](https://github.com/hidencloud/images/tree/main/nodejs/14)
	- `ghcr.io/hidencloud/images:nodejs_14`
- [Nodejs 15](https://github.com/hidencloud/images/tree/main/nodejs/15)
	- `ghcr.io/hidencloud/images:nodejs_15`
- [Nodejs 16](https://github.com/hidencloud/images/tree/main/nodejs/16)
	- `ghcr.io/hidencloud/images:nodejs_16`
- [Nodejs 17](https://github.com/hidencloud/images/tree/main/nodejs/17)
	- `ghcr.io/hidencloud/images:nodejs_17`
- [Nodejs 18](https://github.com/hidencloud/images/tree/main/nodejs/18)
	- `ghcr.io/hidencloud/images:nodejs_18`
- [Nodejs 19](https://github.com/hidencloud/images/tree/main/nodejs/19)
	- `ghcr.io/hidencloud/images:nodejs_19`
- [Nodejs 20](https://github.com/hidencloud/images/tree/main/nodejs/20)
	- `ghcr.io/hidencloud/images:nodejs_20`
- [Nodejs 21](https://github.com/hidencloud/images/tree/main/nodejs/21)
	- `ghcr.io/hidencloud/images:nodejs_21`
- [Nodejs 22](https://github.com/hidencloud/images/tree/main/nodejs/22)
	- `ghcr.io/hidencloud/images:nodejs_22`

## Python [AMD64/ARM64]

- [Python 2.7](https://github.com/hidencloud/images/tree/main/python/2.7)
	- `ghcr.io/hidencloud/images:python_2.7`
- [Python 3.6](https://github.com/hidencloud/images/tree/main/python/3.6)
	- `ghcr.io/hidencloud/images:python_3.6`
- [Python 3.7](https://github.com/hidencloud/images/tree/main/python/3.7)
	- `ghcr.io/hidencloud/images:python_3.7`
- [Python 3.8](https://github.com/hidencloud/images/tree/main/python/3.8)
	- `ghcr.io/hidencloud/images:python_3.8`
- [Python 3.9](https://github.com/hidencloud/images/tree/main/python/3.9)
	- `ghcr.io/hidencloud/images:python_3.9`
- [Python 3.10](https://github.com/hidencloud/images/tree/main/python/3.10)
	- `ghcr.io/hidencloud/images:python_3.10`
- [Python 3.11](https://github.com/hidencloud/images/tree/main/python/3.11)
	- `ghcr.io/hidencloud/images:python_3.11`
- [Python 3.12](https://github.com/hidencloud/images/tree/main/python/3.12)
	- `ghcr.io/hidencloud/images:python_3.12`
- [Python 3.13-rc](https://github.com/hidencloud/images/tree/main/python/3.13-rc)
	- `ghcr.io/hidencloud/images:python_3.13-rc`

## Java Amazon Corretto [AMD64/ARM64]

- [Java 8 Amazon Corretto](https://github.com/hidencloud/images/tree/main/java-corretto/8)
    - `ghcr.io/hidencloud/images:java_8_corretto`
- [Java 11 Amazon Corretto](https://github.com/hidencloud/images/tree/main/java-corretto/11)
    - `ghcr.io/hidencloud/images:java_11_corretto`
- [Java 17 Amazon Corretto](https://github.com/hidencloud/images/tree/main/java-corretto/17)
    - `ghcr.io/hidencloud/images:java_17_corretto`
- [Java 19 Amazon Corretto](https://github.com/hidencloud/images/tree/main/java-corretto/19)
    - `ghcr.io/hidencloud/images:java_19_corretto`
- [Java 20 Amazon Corretto](https://github.com/hidencloud/images/tree/main/java-corretto/20)
    - `ghcr.io/hidencloud/images:java_20_corretto`
- [Java 21 Amazon Corretto](https://github.com/hidencloud/images/tree/main/java-corretto/21)
    - `ghcr.io/hidencloud/images:java_21_corretto`

## Java Azul Zulu [AMD64/ARM64]

- [Java 8 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/8)
    - `ghcr.io/hidencloud/images:java_8_zulu`
- [Java 11 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/11)
    - `ghcr.io/hidencloud/images:java_11_zulu`
- [Java 16 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/16)
    - `ghcr.io/hidencloud/images:java_16_zulu`
- [Java 17 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/17)
    - `ghcr.io/hidencloud/images:java_17_zulu`
- [Java 18 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/18)
    - `ghcr.io/hidencloud/images:java_18_zulu`
- [Java 19 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/19)
    - `ghcr.io/hidencloud/images:java_19_zulu`
- [Java 20 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/20)
    - `ghcr.io/hidencloud/images:java_20_zulu`
- [Java 21 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/21)
    - `ghcr.io/hidencloud/images:java_21_zulu`
- [Java 22 Zulu](https://github.com/hidencloud/images/tree/main/java-zulu/22)
    - `ghcr.io/hidencloud/images:java_22_zulu`

## Java Dragonwell [AMD64/ARM64]

- [Java 8 Dragonwell](https://github.com/hidencloud/images/tree/main/java-dragonwell/8)
    - `ghcr.io/hidencloud/images:java_8_dragonwell`
- [Java 11 Dragonwell](https://github.com/hidencloud/images/tree/main/java-dragonwell/11)
    - `ghcr.io/hidencloud/images:java_11_dragonwell`
- [Java 17 Dragonwell](https://github.com/hidencloud/images/tree/main/java-dragonwell/17)
    - `ghcr.io/hidencloud/images:java_17_dragonwell`
- [Java 21 Dragonwell](https://github.com/hidencloud/images/tree/main/java-dragonwell/21)
    - `ghcr.io/hidencloud/images:java_21_dragonwell`

## Java Liberica [AMD64/ARM64]

- [Java 8 Liberica](https://github.com/hidencloud/images/tree/main/java-liberica/8)
    - `ghcr.io/hidencloud/images:java_8_liberica`
- [Java 11 Liberica](https://github.com/hidencloud/images/tree/main/java-liberica/11)
    - `ghcr.io/hidencloud/images:java_11_liberica`
- [Java 17 Liberica](https://github.com/hidencloud/images/tree/main/java-liberica/17)
    - `ghcr.io/hidencloud/images:java_17_liberica`
- [Java 21 Liberica](https://github.com/hidencloud/images/tree/main/java-liberica/21)
    - `ghcr.io/hidencloud/images:java_21_liberica`
- [Java 22 Liberica](https://github.com/hidencloud/images/tree/main/java-liberica/22)
    - `ghcr.io/hidencloud/images:java_22_liberica`

## Java OpenJ9 [AMD64/ARM64]

``Java 16 OpenJ9`` does only work on AMD64.

- [Java 8 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/8)
    - `ghcr.io/hidencloud/images:java_8_openj9`
- [Java 11 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/11)
    - `ghcr.io/hidencloud/images:java_11_openj9`
- [Java 16 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/16)
    - `ghcr.io/hidencloud/images:java_16_openj9`
- [Java 17 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/17)
    - `ghcr.io/hidencloud/images:java_17_openj9`
- [Java 18 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/18)
    - `ghcr.io/hidencloud/images:java_18_openj9`
- [Java 20 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/20)
    - `ghcr.io/hidencloud/images:java_20_openj9`
- [Java 21 OpenJ9](https://github.com/hidencloud/images/tree/main/java-openj9/21)
    - `ghcr.io/hidencloud/images:java_21_openj9`

## Java Shipilev Experimental [AMD64/ARM64]

These are [shipilev experimental builds.](https://builds.shipilev.net/) If you're looking for Shenandoah GC, it is also by default shipped with at least Azul, Corretto and Temurin images starting with Java 11.

- [Java 8 Shenandoah](https://github.com/hidencloud/images/tree/main/java-shenandoah/8)
    - `ghcr.io/hidencloud/images:java_8_shenandoah`
- [Java 11 Shenandoah](https://github.com/hidencloud/images/tree/main/java-shenandoah/11)
    - `ghcr.io/hidencloud/images:java_11_shenandoah`
- [Java 17 Shenandoah](https://github.com/hidencloud/images/tree/main/java-shenandoah/17)
    - `ghcr.io/hidencloud/images:java_17_shenandoah`
- [Java 21 Shenandoah](https://github.com/hidencloud/images/tree/main/java-shenandoah/21)
    - `ghcr.io/hidencloud/images:java_21_shenandoah`

## GraalVM [AMD64/ARM64]

| Java | Standard                               | JDK                                        	 |
|------|----------------------------------------|----------------------------------------------|
| 11   | `ghcr.io/hidencloud/images:graalvm_11` | ❌                                            |
| 17   | `ghcr.io/hidencloud/images:graalvm_17` | `ghcr.io/hidencloud/images:graalvm_17-JDK`   |
| 19   | `ghcr.io/hidencloud/images:graalvm_19` | ❌                                            |
| 20   | ❌                                      | `ghcr.io/hidencloud/images:graalvm_20-JDK`   |
| 21   | ❌                                      | `ghcr.io/hidencloud/images:graalvm_21-JDK`	  |
| 22   | ❌                                  	   | `ghcr.io/hidencloud/images:graalvm_22-JDK`	  |
| 23   | ❌                                 	    | `ghcr.io/hidencloud/images:graalvm_23-JDK`   | 
| 24   | ❌                                  	   | `ghcr.io/hidencloud/images:graalvm_24-JDK`	  |

