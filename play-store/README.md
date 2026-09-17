# Google Play

Одна папка `web/` является источником и для GitHub Pages/PWA, и для Android через Capacitor.

До первой публикации: окончательно подтвердить package id `com.polyejik.vanda`; создать release keystore и хранить его вне репозитория; подключить signing secrets; подготовить иконку 512×512, feature graphic 1024×500, скриншоты, описание и privacy policy; первый `.aab` загрузить во Internal testing Google Play Console.

`android-debug.yml` собирает тестовый APK. `android-release.yml` пока делает unsigned AAB; подпись подключается отдельно через secrets.
