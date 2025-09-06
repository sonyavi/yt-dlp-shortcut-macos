# 🎬 yt-dlp Shortcut for macOS

Интеграция [yt-dlp](https://github.com/yt-dlp/yt-dlp) с macOS Shortcuts.  
Копируешь ссылку → запускаешь Shortcut → выбираешь формат → готово.

👉 **Автоматически удаляются сегменты SponsorBlock**  
👉 Встраиваются **метаданные, главы и миниатюры**  

---

## 🚀 Установка Shortcut

[![Install via iCloud](https://img.shields.io/badge/Install%20via%20iCloud-Shortcut-blue?logo=icloud)](https://www.icloud.com/shortcuts/baa81804fcf64011bab7a1a3c0ad22f4)

> Если iCloud-ссылка https://www.icloud.com/shortcuts/baa81804fcf64011bab7a1a3c0ad22f4 недоступна, можно импортировать файл из `shortcuts/YouTube_DL.shortcut` (см. раздел «Альтернатива» ниже).

---

## 📦 Зависимости

```bash
brew install yt-dlp ffmpeg
```

---

## 📂 Структура репозитория

```
yt-dlp-shortcut-macos/
├── yt-clip-dl             # основной скрипт (zsh)
├── README.md              # документация
```

---

## ⚙️ Установка скрипта

```bash
chmod +x yt-clip-dl
mkdir -p ~/bin
cp yt-clip-dl ~/bin/
```

> На Apple Silicon `yt-dlp` и `ffmpeg` обычно в `/opt/homebrew/bin`.  
> Скрипт сам находит пути и работает из Shortcuts (где PATH урезан).

---

## 🖥 Использование

1) Скопируй ссылку на YouTube в буфер обмена.  
2) Запусти Shortcut **YouTube DL** (меню-бар / Spotlight / горячая клавиша).  
3) Выбери нужный пресет.  
4) Дождись уведомления «Загрузка завершена».

Файлы сохраняются в:
```
~/Downloads/YouTube/<Uploader>/<YYYY-MM-DD - Title [ID].mp4>
```

---

## 🎛 Пресеты (названия для меню)

- **iPhone (H.264/AAC · MP4 · 1080p)**
- **H.264 (AVC/AAC · MP4 · max)**
- **HEVC (H.265/AAC · MP4 · max)**
- **HEVC (H.265/AAC · MP4 · 1080p)**
- **VP9 (VP9/Opus · MKV · max)**
- **AV1 (AV1/Opus · MKV · max)**
- **Best auto (mixed · MKV · max)**

> Для максимальной совместимости iPhone/macOS и мессенджеров используйте **iPhone** или **H.264**.

---

## 🧩 Что делает скрипт

- выбирает форматы по пресетам (кодек/контейнер/разрешение),
- **всегда** удаляет сегменты SponsorBlock: `sponsor,selfpromo,interaction,music_offtopic`,
- встраивает метаданные/главы/миниатюру,
- автоматически ищет `ffmpeg`/`yt-dlp` (поддержка Apple Silicon и Intel),
- показывает уведомления о старте/завершении.

---

## 🔧 Альтернатива: импорт файла Shortcut

Если не используете iCloud-ссылку:
1. Откройте `shortcuts/YouTube_DL.shortcut` → подтвердите импорт в «Команды».
2. При необходимости укажите путь к скрипту: `~/bin/yt-clip-dl`.

---

## ❓ FAQ

**Видео не объединяются в один файл**  
Установите `ffmpeg` или укажите путь через `--ffmpeg-location`. Скрипт делает это автоматически, если находит бинарь.

**Нужны субтитры**  
Можно добавить в скрипт:
```bash
--write-subs --write-auto-subs --embed-subs --sub-langs "ru.*,en.*"
```

**Где хранятся файлы?**  
По умолчанию: `~/Downloads/YouTube`. Можно изменить переменную `out_dir` в скрипте.

---

## 🙌 Авторство

Скрипт и Shortcut настроены пользователем **<your github nick>**.  
Основано на [yt-dlp](https://github.com/yt-dlp/yt-dlp).

---

## 📜 Лицензия

MIT
