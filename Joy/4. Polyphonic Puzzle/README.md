# Polyphonic Puzzle

![alt text](Joy.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [pp.zip](pp.zip)
---
**Описание**: 
---
🎧 У нас есть странный аудиофайл.
Звучит как обычный фортепианный цикл, но где-то в этом полифоническом хаосе закодирован флаг.
Угадайте, как он был спрятан, и заставьте звук говорить.

**Description**:
--- 
🎧 We have a strange audio file.
It sounds like a regular piano loop, but somewhere in this polyphonic chaos - a flag is encoded.
Guess how it was hidden and make the sound speak.

**Решение**:
---
Нужно понять, что такое .mid расширение, как с ним работать, какие есть библиотеки для работы с такими файлами и создания таких файлов в целом. 
Можно наткнуться на библиотеку pretty_midi и посмотреть, как генерируются файлы и как можно при помощи параметров звука зашифровать сообщение.

Итогово нас может заинтересовать высота и скорость нот, после чего можно уже попытаться написать скрипт, в котором перебирать различные параметры, пока не получится что-то вроде:

```
import pretty_midi

scale = 0.01
pm = pretty_midi.PrettyMIDI("mystery_rhythm.mid")

flag_notes = []

for instr in pm.instruments:
    for note in instr.notes:
        if note.pitch == 60 and note.velocity == 127:
            duration = note.end - note.start
            value = round(duration / scale)
            flag_notes.append((note.start, chr(value)))
 
flag_notes.sort()
flag = ''.join([ch for _, ch in flag_notes])
print("Флаг:", flag)
```

И сам флаг: solar{r1tmic_m3ssenger}

**Solution**:
---
You need to understand what the .mid extension is, how to work with it, what libraries exist for working with such files and creating such files in general.
You can stumble upon the pretty_midi library and see how files are generated and how you can encrypt a message using sound parameters.

Finally, we may be interested in the pitch and speed of the notes, after which we can try to write a script in which we iterate through various parameters until we get something like:

```
import pretty_midi

scale = 0.01
pm = pretty_midi.PrettyMIDI("mystery_rhythm.mid")

flag_notes = []

for instr in pm.instruments:
    for note in instr.notes:
        if note.pitch == 60 and note.velocity == 127:
            duration = note.end - note.start
            value = round(duration / scale)
            flag_notes.append((note.start, chr(value)))
 
flag_notes.sort()
flag = ''.join([ch for _, ch in flag_notes])
print("Flag:", flag)
```

And the flag itself: solar{r1tmic_m3ssenger}