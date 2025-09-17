# Mod Menu 1.1x

## About

A fork of [Mod Menu](https://modrinth.com/mod/modmenu) to try and maintain less supported versions of Minecraft, mainly 1.14.x as of now.

![modmenu](showcase_screenshot.png)

### Other Forks

Similar forks of modmenu:<br/>

- [Mod Menu Ornithe](https://modrinth.com/mod/modmenu-ornithe)
- [Mod Menu Babric](https://modrinth.com/mod/modmenu-babric)

### Current and Projected Version Support

- [x] 1.14.4
- [x] 1.14.2

### Why

Well trying to mod Minecraft 1.14.2 I found that Mod Menu did not work correctly and since I was looking for a small project I decided try to back port it, in the process I started by getting 1.14.4 updated and releasing that first then releasing 1.14.2

## Development Info

Most other development info is the same from normal Mod Menu with the exception of a few things.<br/>

1. All API imports are kept at `io.github.prospector.modmenu.api` this is becuase it enables the maximum level of compatiblity with pre-existing mods for 1.14.x

Example imports:

```
import io.github.prospector.modmenu.api.ModMenuApi;
import io.github.prospector.modmenu.api.ConfigScreenFactory;
```

2. `ConfigScreenFactory` is supported this is done through a 1.15.2 backport
3. When adding as a dependency use `maven.modrinth`, below are some examples of what you need to add to your `build.gradle`.

More information on `maven.modrinth` can be [found here.](https://support.modrinth.com/en/articles/8801191-modrinth-maven)

`build.gradle`

```
repositories {
    exclusiveContent {
            forRepository {
                maven {
                    name = "Modrinth"
                    url = "https://api.modrinth.com/maven"
                }
            }
            filter {
                includeGroup "maven.modrinth"
            }
        }
    }
```

`build.gradle`

```
dependencies {
    modApi include("maven.modrinth:mod-menu-1.1x:ABC")
}
```

`ABC` should be replaced with the version of the release of Mod Menu 1.1x you are trying to support, you can find the version on the versions page.
