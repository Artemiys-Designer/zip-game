# Зип: путь домой — упаковка для телефона

В папке `www` лежит готовая игра. Дальше два пути.

## Путь 1. Установка с браузера (PWA) — проще и быстрее всего

Нужен любой хостинг с HTTPS. Подойдёт бесплатный:
- **Netlify Drop**: зайдите на app.netlify.com/drop и перетащите туда папку `www`. Через минуту будет ссылка.
- или **GitHub Pages**, **Cloudflare Pages**.

Дальше на телефоне:
- **Android (Chrome)**: откройте ссылку, меню ⋮ → «Установить приложение» (или «Добавить на главный экран»).
- **iPhone (Safari)**: откройте ссылку, «Поделиться» → «На экран Домой».

Иконка появится на экране, игра откроется на весь экран и будет работать без интернета. Прогресс и наряды хранятся в самом телефоне.

Если вы обновили игру, поменяйте в `www/sw.js` строку `const CACHE = 'zip-v1'` на `zip-v2`, иначе телефон покажет старую версию.

## Путь 2. Android-приложение (APK / Google Play) через Capacitor

Нужны Node.js и Android Studio.

```
npm i @capacitor/core @capacitor/cli @capacitor/android
npx cap add android
npx cap sync
npx cap open android
```

В Android Studio: Build → Build APK(s) для пробной сборки или Generate Signed Bundle для Google Play.

Чтобы игра всегда шла горизонтально, в файле `android/app/src/main/AndroidManifest.xml` у `<activity ...>` добавьте:
`android:screenOrientation="sensorLandscape"`

Иконку приложения замените через Android Studio: правый клик на `res` → New → Image Asset, файл `www/icons/icon-512.png`.

Для Google Play понадобится аккаунт разработчика (разовый платёж 25 $).

## iPhone-приложение (App Store)

Нужен Mac с Xcode и аккаунт Apple Developer (99 $ в год):
```
npm i @capacitor/ios
npx cap add ios
npx cap open ios
```
Без Mac и аккаунта остаётся способ из Пути 1 (Safari → «На экран Домой»).
