# Ванда — полёт за мечтой

Единый репозиторий игры для **Web/PWA** и **Android / Google Play**.

## Архитектура

Одна игровая кодовая база живёт в `web/`. Web-версия публикуется через GitHub Pages. Android-приложение собирается из той же папки через Capacitor, поэтому игровую механику, UI, параллакс, бонусы и багфиксы не нужно поддерживать дважды.

```text
Vandagame/
├── web/                    # единая игровая web/PWA сборка
│   ├── index.html
│   ├── assets/
│   ├── manifest.webmanifest
│   └── sw.js
├── play-store/             # материалы и checklist Google Play
├── .github/workflows/      # Web deploy + Android CI
├── capacitor.config.json
└── package.json
```

## Текущая рабочая база

Миграция начинается с `Vanda_Game_v36_FULL_QA_FIX.html`. Следующий технический этап — вынести встроенные изображения/звук из монолитного HTML в `web/assets/`, не меняя игровую механику. Это уменьшит память и загрузку на мобильных устройствах и подготовит проект к Android.

## Web

После миграции ресурсов:

```bash
npm install
npm run web:serve
```

GitHub Pages должен публиковать папку `web/` через workflow `.github/workflows/pages.yml`.

## Android

Capacitor использует **ту же** папку `web/`:

```bash
npm install
npm run cap:add:android
npm run cap:sync
npm run cap:open
```

Для тестовых Android-сборок GitHub Actions может собирать APK. Для Google Play финальный формат — подписанный **Android App Bundle (`.aab`)**.

> Важно: текущий package id `com.polyejik.vanda` пока считается рабочим. Перед первой публикацией в Google Play его нужно окончательно утвердить: после публикации package id приложения менять нельзя.

## Релизная логика

- `main` — стабильная версия.
- новые изменения желательно делать в ветках/PR;
- Web и Android всегда собираются из одной версии `web/`;
- сначала Internal testing в Google Play, затем Production.
