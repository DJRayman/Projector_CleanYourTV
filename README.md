# Projector Jixin (Amlogic T950S) — оптимизация и настройки

Оптимизация проектора на прошивке **Jixin** (Amlogic **T950S**, `t950s_be311`, Android TV 13) по методике
[CleanYourTV](https://github.com/Gathin23/cleanyourtv): отключение рекламы и лишних сервисов через ADB,
минималистичный лаунчер в стиле Apple TV и приложение для запуска скрытых настроек проектора.

Отделено из репозитория с телевизорами: проектор — отдельный класс устройства (Amlogic, projector), со своими
особенностями (трапеция, автофокус, управление вентиляторами), поэтому вынесен сюда.

## Состав
- `launcher/` — лаунчер `com.gathin.tvhome`, форк [CleanYourTV](https://github.com/Gathin23/cleanyourtv)
  (MIT, © Gathin; см. `launcher/LICENSE`, шрифт Outfit — OFL, `launcher/FONT-LICENSE-OFL.txt`). Обои Bing,
  русский системный шрифт, перестановка плиток, вход с антенны, режимы энергопотребления, карточка по кнопке Info.
- `hidden-settings/` — приложение **«Скрытые настройки»**: открывает экраны настроек, которых нет в обычном
  меню (настройки проектора Jixin, изображение и звук Amlogic, стандартные настройки Android TV, выбор режима
  Bluetooth). Пункты, которых нет на устройстве, скрываются сами, так что приложение подходит и для телевизоров.
- `projector/` — разбор проектора: debloat-список, `restore.sh`, заметки по настройкам, яркости, вентиляторам,
  Bluetooth и выбору лаунчера.

## Сборка лаунчера и приложения
    export JAVA_HOME=~/android/tools/jdk-21.0.12.1+1 PATH=$JAVA_HOME/bin:$PATH
    cd launcher && ./gradlew assembleDebug           # или: cd hidden-settings && ./gradlew assembleDebug
    ~/android/adbw -s <ip>:<порт> install -r app/build/outputs/apk/debug/app-debug.apk

Подробности по проектору — в [projector/README.md](projector/README.md), по приложению —
в [hidden-settings/README.md](hidden-settings/README.md).

Тот же лаунчер (общая кодовая база) используется и в репозитории с телевизорами.
