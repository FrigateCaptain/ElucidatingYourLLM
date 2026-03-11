# Video Editing — Работа с видео через ffmpeg

**Доменное правило.** Применять при нарезке, склейке, наложении субтитров/логотипов, перекодировании.

Globs: `**/*.mp4, **/*.mkv, **/*.avi, **/*.webm, **/*.mov, **/*.srt, **/*.ass`

---

## Обязательные правила

### Тест перед полным рендером [MANDATORY]
Всегда делать тест-клип (~20-30 сек) и показывать пользователю. Полный рендер — только после подтверждения.

### -ss всегда ПЕРЕД -i [MANDATORY]
```bash
# ПРАВИЛЬНО:
ffmpeg -y -ss 00:13:56 -i input.mp4 -t 45 ...

# НЕПРАВИЛЬНО — будет декодировать часами:
ffmpeg -y -i input.mp4 -ss 00:13:56 ...
```
**Исключение:** тест-клип вокруг точки реза — `-ss` после `-i` для точного seek.

### Видео перекодировать, аудио копировать [MANDATORY]
```bash
-c:v libx264 -crf 18 -preset fast -c:a copy
```
Никогда не перекодировать аудио (lossy → lossy = артефакты).

### Склейка — только concat demuxer [MANDATORY]
```bash
printf "file 'part1.mp4'\nfile 'part2.mp4'\n" > _list.txt
ffmpeg -y -f concat -safe 0 -i _list.txt -c copy output.mp4
```
`filter_complex concat` — не использовать (рассинхрон, дублирование звука).

### К длительности фрагмента добавлять +0.5 сек [MANDATORY]
Компенсирует потерю концовки при перекодировании.

---

## Канонические параметры

| Параметр | Значение | Назначение |
|----------|----------|------------|
| `-crf 18` | качество видео | визуально без потерь |
| `-preset fast` | скорость кодирования | баланс скорости и сжатия |
| `-c:a copy` | аудио | без перекодирования |
| `-t` | длительность | использовать вместо `-to` |

Скорость рендера: ~2 мин на 1 мин видео (1080p, CPU).

---

## Шаблоны команд

### Вырезать фрагмент
```bash
ffmpeg -y -ss HH:MM:SS -i "input.mp4" -t ДЛИТЕЛЬНОСТЬ \
  -c:v libx264 -crf 18 -preset fast -c:a copy "output.mp4"
```

### Удалить кусок из середины
```bash
ffmpeg -y -ss 00:00:00 -i "input.mp4" -t T1 \
  -c:v libx264 -crf 18 -preset fast -c:a copy /tmp/_part_a.mp4
ffmpeg -y -ss T2 -i "input.mp4" \
  -c:v libx264 -crf 18 -preset fast -c:a copy /tmp/_part_b.mp4
printf "file '/tmp/_part_a.mp4'\nfile '/tmp/_part_b.mp4'\n" > /tmp/_list.txt
ffmpeg -y -f concat -safe 0 -i /tmp/_list.txt -c copy "output.mp4"
```

### Логотип (постоянный)
```bash
ffmpeg -y -i "input.mp4" -i "_logo.png" \
  -filter_complex "[0:v][1:v]overlay=X:Y[vout]" \
  -map "[vout]" -map 0:a \
  -c:v libx264 -crf 18 -preset fast -c:a copy "output.mp4"
```

### Субтитры + логотип
```bash
ffmpeg -y -i "input.mp4" -i "_logo.png" \
  -filter_complex "
    [0:v]subtitles='_subtitles.srt':force_style='FontName=DejaVu Sans,FontSize=11,PrimaryColour=&H00FFFFFF,OutlineColour=&H00000000,Outline=2,Shadow=1,Alignment=2,MarginV=13'[vsub];
    [vsub][1:v]overlay=X:Y[vout]
  " \
  -map "[vout]" -map 0:a \
  -c:v libx264 -crf 18 -preset fast -c:a copy "output.mp4"
```

### Проверить параметры файла
```bash
ffprobe -v error -select_streams v:0 \
  -show_entries stream=width,height \
  -show_entries format=duration \
  -of compact "input.mp4"
```
