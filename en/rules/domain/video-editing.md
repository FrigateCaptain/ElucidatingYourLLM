# Video Editing — Working with Video via ffmpeg

**Domain rule.** Apply when cutting, joining, adding subtitles/logos, or transcoding.

Globs: `**/*.mp4, **/*.mkv, **/*.avi, **/*.webm, **/*.mov, **/*.srt, **/*.ass`

---

## Required Rules

### Test Before Full Render [MANDATORY]
Always create a test clip (~20–30 sec) and show it to the user. Full render — only after confirmation.

### -ss Always BEFORE -i [MANDATORY]
```bash
# CORRECT:
ffmpeg -y -ss 00:13:56 -i input.mp4 -t 45 ...

# WRONG — will decode for hours:
ffmpeg -y -i input.mp4 -ss 00:13:56 ...
```
**Exception:** test clip around a cut point — `-ss` after `-i` for frame-accurate seeking.

### Transcode Video, Copy Audio [MANDATORY]
```bash
-c:v libx264 -crf 18 -preset fast -c:a copy
```
Never re-encode audio (lossy → lossy = artifacts).

### Joining — Use concat demuxer Only [MANDATORY]
```bash
printf "file 'part1.mp4'\nfile 'part2.mp4'\n" > _list.txt
ffmpeg -y -f concat -safe 0 -i _list.txt -c copy output.mp4
```
`filter_complex concat` — do not use (causes desync, audio duplication).

### Add +0.5 sec to Fragment Duration [MANDATORY]
Compensates for the tail being lost during transcoding.

---

## Canonical Parameters

| Parameter | Value | Purpose |
|-----------|-------|---------|
| `-crf 18` | video quality | visually lossless |
| `-preset fast` | encoding speed | balance of speed and compression |
| `-c:a copy` | audio | no re-encoding |
| `-t` | duration | use instead of `-to` |

Render speed: ~2 min per 1 min of video (1080p, CPU).

---

## Command Templates

### Extract a Fragment
```bash
ffmpeg -y -ss HH:MM:SS -i "input.mp4" -t DURATION \
  -c:v libx264 -crf 18 -preset fast -c:a copy "output.mp4"
```

### Remove a Section from the Middle
```bash
ffmpeg -y -ss 00:00:00 -i "input.mp4" -t T1 \
  -c:v libx264 -crf 18 -preset fast -c:a copy /tmp/_part_a.mp4
ffmpeg -y -ss T2 -i "input.mp4" \
  -c:v libx264 -crf 18 -preset fast -c:a copy /tmp/_part_b.mp4
printf "file '/tmp/_part_a.mp4'\nfile '/tmp/_part_b.mp4'\n" > /tmp/_list.txt
ffmpeg -y -f concat -safe 0 -i /tmp/_list.txt -c copy "output.mp4"
```

### Logo (Permanent)
```bash
ffmpeg -y -i "input.mp4" -i "_logo.png" \
  -filter_complex "[0:v][1:v]overlay=X:Y[vout]" \
  -map "[vout]" -map 0:a \
  -c:v libx264 -crf 18 -preset fast -c:a copy "output.mp4"
```

### Subtitles + Logo
```bash
ffmpeg -y -i "input.mp4" -i "_logo.png" \
  -filter_complex "
    [0:v]subtitles='_subtitles.srt':force_style='FontName=DejaVu Sans,FontSize=11,PrimaryColour=&H00FFFFFF,OutlineColour=&H00000000,Outline=2,Shadow=1,Alignment=2,MarginV=13'[vsub];
    [vsub][1:v]overlay=X:Y[vout]
  " \
  -map "[vout]" -map 0:a \
  -c:v libx264 -crf 18 -preset fast -c:a copy "output.mp4"
```

### Check File Parameters
```bash
ffprobe -v error -select_streams v:0 \
  -show_entries stream=width,height \
  -show_entries format=duration \
  -of compact "input.mp4"
```
