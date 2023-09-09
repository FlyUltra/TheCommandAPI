# TheCommandAPI
![badge](https://img.shields.io/github/v/release/iVantional/TheCommandAPI)
[![badge](https://jitpack.io/v/iVantional/TheCommandAPI.svg)](https://jitpack.io/#iVantional/TheCommandAPI)
![badge](https://img.shields.io/github/downloads/iVantional/TheCommandAPI/total)
![badge](https://img.shields.io/github/last-commit/iVantional/TheCommandAPI)
![badge](https://img.shields.io/badge/platform-spigot-lightgrey)
[![badge](https://img.shields.io/discord/896466173166747650?label=discord)](https://discord.gg/E8AkAjaX8m)
[![badge](https://img.shields.io/github/license/iVantional/TheCommandAPI)](https://github.com/iVantional/TheCommandAPI/blob/master/LICENSE.txt)


Are you bored of creating typical commands? <br>
Try our API for your Spigot commands. <br>

## Table of contents

* [Getting started](#getting-started)
* [Example](#example)
* [License](#license)

## Getting started

Make sure you reloaded maven or gradle in your project.

### Add TheCommandAPI to your project

[![badge](https://jitpack.io/v/iVantional/TheCommandAPI.svg)](https://jitpack.io/#iVantional/TheCommandAPI)

You need to add this dependency into your plugin, then look at under the dependencies example

<details>
    <summary>Maven</summary>

```xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>com.github.iVantional</groupId>
        <artifactId>TheCommandAPI</artifactId>
        <version>VERSION</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```
</details>

<details>
    <summary>Gradle</summary>

```gradle
allprojects {
    repositories {
        ...
        maven { url 'https://jitpack.io' }
    }
}

dependencies {
    implementation 'com.github.iVantional:TheCommandAPI:VERSION'
}
```
</details>

### Example

<details>
    <summary>Command example</summary>

```java
public class Example extends Command {
    
    // One type of constructor for register
    public Example() {
        super("example", new String[]{"test"}, "Example command!");
    }

    // Second type of constructor for register
    public Example(String command, String[] aliases, String description) {
        super(command, aliases, description);
    }

    // Command example
    @Override
    public void execute(CommandSender sender, String[] args) {
        sender.sendMessage("Example command!");

    }

    // Tab completer example
    @Override
    public List<String> onTabComplete(CommandSender sender, String[] args) {
        List<String> arguments = new ArrayList<>();
        Player player = (Player) sender;

        if (!player.hasPermission("admin")) {
            return Arrays.asList(" ");
        }

        if (args.length == 1) {
            return StringUtil.copyPartialMatches(args[0], Arrays.asList("tab", "complete"), new ArrayList<>());
        }

        return arguments;
    }
}
```
</details>


## License
TheCommandAPI is licensed under the permissive MIT license. Please see [`LICENSE.txt`](https://github.com/iVantional/TheCommandAPI/blob/master/LICENSE.txt) for more information.