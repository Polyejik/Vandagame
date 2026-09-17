# Ванда — полёт за мечтой

Одна кодовая база для **Web/PWA** и **Android / Google Play**.

- `web/` — каноническая игровая сборка.
- корневой `index.html` только открывает `web/` на постоянном GitHub Pages URL.
- Android строится из `web/` через Capacitor.
- `.github/workflows/android-debug.yml` собирает тестовый APK.
- `.github/workflows/android-release.yml` готовит release AAB; signing будет подключён через GitHub Secrets.

Web: https://polyejik.github.io/Vandagame/

Package id сейчас: `com.polyejik.vanda`. До первой публикации в Google Play его нужно окончательно утвердить.

Следующий этап — перенести рабочую Vanda v36 и её assets в `web/` без изменения игровой механики.
