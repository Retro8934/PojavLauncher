<h1 align="center">PojavLauncher</h1>

<img src="https://github.com/PojavLauncherTeam/PojavLauncher/blob/v3_openjdk/app_pojavlauncher/src/main/assets/pojavlauncher.png" align="left" width="130" height="150" alt="Логотип PojavLauncher">

[![Android CI](https://github.com/PojavLauncherTeam/PojavLauncher/workflows/Android%20CI/badge.svg)](https://github.com/PojavLauncherTeam/PojavLauncher/actions)
[![Активность коммитов на GitHub](https://img.shields.io/github/commit-activity/m/PojavLauncherTeam/PojavLauncher)](https://github.com/PojavLauncherTeam/PojavLauncher/actions)
[![Crowdin](https://badges.crowdin.net/pojavlauncher/localized.svg)](https://crowdin.com/project/pojavlauncher)
[![Discord](https://img.shields.io/discord/724163890803638273.svg?label=&logo=discord&logoColor=ffffff&color=7389D8&labelColor=6A7EC2)](https://discord.com/invite/aenk3EUvER)
[![Подписаться в Twitter](https://img.shields.io/twitter/follow/plaunchteam?color=blue&style=flat-square)](https://twitter.com/PLaunchTeam)

*Из пепла [Boardwalk](https://github.com/zhuowei/Boardwalk) появляется PojavLauncher!*

PojavLauncher — это лаунчер, позволяющий играть в Minecraft: Java Edition на устройствах Android и [iOS](https://github.com/PojavLauncherTeam/PojavLauncher_iOS).

Для получения дополнительной информации ознакомьтесь с нашей [вики](https://pojavlauncher.app/)!

## Важные примечания

**PojavLauncher был прекращён** и больше не поддерживается. Его преемник доступен [здесь](https://github.com/AngelAuraMC/Amethyst-Android).

## Содержание

* [Введение](#введение)
* [Получение PojavLauncher](#получение-pojavlauncher)
* [Сборка](#сборка)
    * [Быстрая сборка (рекомендуется)](#быстрая-сборка-рекомендуется)
    * [Подробная сборка](#подробная-сборка)
* [Текущий статус](#текущий-статус)
* [Известные проблемы](#известные-проблемы)
* [FAQ](#faq)
* [Участие в разработке](#участие-в-разработке)
* [Поддержка](#поддержка)
* [Лицензия](#лицензия)
* [Благодарности и зависимости](#благодарности-и-зависимости)
* [План развития](#план-развития)

## Введение

* PojavLauncher — это лаунчер Minecraft: Java Edition для Android и iOS, основанный на [Boardwalk](https://github.com/zhuowei/Boardwalk)
* Этот лаунчер может запускать почти все доступные версии Minecraft, от rd-132211 до снапшотов 1.21 (включая версии Combat Test)
* Также поддерживаются моды через Forge и Fabric.
* Этот репозиторий содержит исходный код для Android. Для iOS/iPadOS ознакомьтесь с [PojavLauncher_iOS](https://github.com/PojavLauncherTeam/PojavLauncher_iOS).

## Получение PojavLauncher

Вы можете получить PojavLauncher тремя способами:

1. **Релизы:** Скачайте готовое приложение из наших [стабильных релизов](https://github.com/PojavLauncherTeam/PojavLauncher/releases) или [автоматических сборок](https://github.com/PojavLauncherTeam/PojavLauncher/actions).
2. **Google Play:** Получите его из Google Play, нажав на этот значок: [![Google Play](https://play.google.com/intl/en_us/badges/static/images/badges/en_badge_web_generic.png)](https://play.google.com/store/apps/details?id=net.kdt.pojavlaunch)
3. **Сборка из исходного кода:** Следуйте [инструкциям по сборке](#сборка) ниже.

## Сборка

### Быстрая сборка (рекомендуется)

Самый простой способ собрать PojavLauncher — использовать готовые JRE, предоставленные нашим CI.

1. Клонируйте репозиторий: `git clone https://github.com/PojavLauncherTeam/PojavLauncher.git`
2. Соберите лаунчер: `./gradlew :app_pojavlauncher:assembleDebug` (используйте `gradlew.bat` в Windows)

Собранный APK будет находиться в `app_pojavlauncher/build/outputs/apk/debug/`.

### Подробная сборка

Если вам нужен больший контроль над процессом сборки, выполните следующие шаги:

1. **Среда выполнения Java (JRE):** Скачайте артефакт `jre8-pojav` из наших [автоматических сборок CI](https://github.com/PojavLauncherTeam/android-openjdk-build-multiarch/actions). Этот пакет содержит готовые JRE для всех поддерживаемых архитектур. Если вам нужно собрать JRE самостоятельно, следуйте инструкциям в репозитории [android-openjdk-build-multiarch](https://github.com/PojavLauncherTeam/android-openjdk-build-multiarch).

2. **LWJGL:** Инструкции по сборке кастомного LWJGL доступны в [репозитории LWJGL](https://github.com/PojavLauncherTeam/lwjgl3).

3. **Список языков:** Поскольку языки автоматически добавляются через Crowdin, перед сборкой необходимо запустить генератор списка языков. В каталоге проекта выполните:
   * Linux/macOS:
     ```bash
     chmod +x scripts/languagelist_updater.sh
     bash scripts/languagelist_updater.sh
     ```
   * Windows:
     ```batch
     scripts\languagelist_updater.bat
     ```

4. **Сборка заглушки GLFW:** `./gradlew :jre_lwjgl3glfw:build`

5. **Сборка лаунчера:** `./gradlew :app_pojavlauncher:assembleDebug` (замените `gradlew` на `gradlew.bat` в Windows).

## Текущий статус

* [x] Мобильный порт OpenJDK 8: ARM32, ARM64, x86, x86_64
* [x] Мобильный порт OpenJDK 17: ARM32, ARM64, x86, x86_64
* [x] Мобильный порт OpenJDK 21: ARM32, ARM64, x86, x86_64
* [x] Установщик модов без графического интерфейса
* [x] Установщик модов с графическим интерфейсом
* [x] OpenGL в среде OpenJDK
* [x] OpenAL (работает на большинстве устройств)
* [x] Поддержка Minecraft 1.12.2 и ниже
* [x] Поддержка Minecraft 1.13 и выше
* [x] Поддержка Minecraft 1.17 (22w13a) и выше
* [x] Масштабирование игровой поверхности
* [x] Новый канал ввода, переписанный на нативный код
* [x] Полностью переписанная система управления
* [ ] Больше в будущем!

## Известные проблемы

Список известных проблем и их текущий статус смотрите в нашем [трекере проблем](https://github.com/PojavLauncherTeam/PojavLauncher/issues).

## FAQ

Для получения дополнительной информации смотрите нашу [вики](https://pojavlauncherteam.github.io/).

## Участие в разработке

Мы приветствуем вклад! Мы рады любому типу вклада, не только коду. Например, вы можете помочь улучшить [вики](https://pojavlauncherteam.github.io/), внести вклад в [переводы](https://crowdin.com/project/pojavlauncher) или отправить отчёты об ошибках и запросы на новые функции.

Любое изменение кода должно быть отправлено в виде pull request. Описание должно объяснять, что делает код, и приводить шаги для его выполнения.

## Поддержка

Для получения поддержки присоединяйтесь к нашему [серверу Discord](https://discord.com/invite/aenk3EUvER).

## Лицензия

PojavLauncher лицензирован под [GNU LGPLv3](https://github.com/PojavLauncherTeam/PojavLauncher/blob/v3_openjdk/LICENSE).

## Благодарности и зависимости

* [Boardwalk](https://github.com/zhuowei/Boardwalk) (JVM-лаунчер): неизвестная лицензия/[Apache License 2.0](https://github.com/zhuowei/Boardwalk/blob/master/LICENSE) или GNU GPLv2.
* Android Support Libraries: [Apache License 2.0](https://android.googlesource.com/platform/prebuilts/maven_repo/android/+/master/NOTICE.txt).
* [GL4ES](https://github.com/PojavLauncherTeam/gl4es): [MIT License](https://github.com/ptitSeb/gl4es/blob/master/LICENSE).
* [OpenJDK](https://github.com/PojavLauncherTeam/openjdk-multiarch-jdk8u): [GNU GPLv2 License](https://openjdk.java.net/legal/gplv2+ce.html).
* [LWJGL3](https://github.com/PojavLauncherTeam/lwjgl3): [BSD-3 License](https://github.com/LWJGL/lwjgl3/blob/master/LICENSE.md).
* [LWJGLX](https://github.com/PojavLauncherTeam/lwjglx) (слой совместимости API LWJGL2 для LWJGL3): неизвестная лицензия.
* [Mesa 3D Graphics Library](https://gitlab.freedesktop.org/mesa/mesa): [MIT License](https://docs.mesa3d.org/license.html).
* [pro-grade](https://github.com/pro-grade/pro-grade) (менеджер безопасности песочницы Java): [Apache License 2.0](https://github.com/pro-grade/pro-grade/blob/master/LICENSE.txt).
* [bhook](https://github.com/bytedance/bhook) (используется для перехвата кода выхода): [MIT license](https://github.com/bytedance/bhook/blob/main/LICENSE).
* [libepoxy](https://github.com/anholt/libepoxy): [MIT License](https://github.com/anholt/libepoxy/blob/master/COPYING).
* [virglrenderer](https://github.com/PojavLauncherTeam/virglrenderer): [MIT License](https://gitlab.freedesktop.org/virgl/virglrenderer/-/blob/master/COPYING).
* Спасибо [MCHeads](https://mc-heads.net) за предоставление аватаров Minecraft.

## План развития

В настоящее время мы сосредоточены на:

* Изучении новых технологий рендеринга.

В будущие планы входит:

* Улучшение стабильности и производительности.
* Улучшение процесса установки модов.

Мы приветствуем отзывы и предложения сообщества по нашему плану развития. Пожалуйста, не стесняйтесь открывать запрос на новую функцию в нашем [трекере проблем](https://github.com/PojavLauncherTeam/PojavLauncher/issues).