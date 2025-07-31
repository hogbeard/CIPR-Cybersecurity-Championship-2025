# Stealed USB

![alt text](Forensic.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [usb_image.dd](usb_image.dd)
---
**Описание**:
---
Сотрудник скопировал некоторые документы на USB-флешку перед уходом. Нам удалось сделать дамп этой флешки, но он удалил важные файлы. У нас есть только файл образа usb_image.dd. Попробуйте восстановить хотя бы один удаленный файл - флаг может быть еще там.

**Description**:
---
An employee copied some documents to a USB flash drive before leaving. We managed to make a dump of this flash drive, but he deleted all the important files.
We only have the image file usb_image.dd. Try to recover at least one deleted file - the flag may still be there

**Решение**:
---
Файл представляет собой raw образ в формате FAT32, в котором есть два файла - сообщение и фейковый флаг. Нужно найти реальный флаг.

Для поиска используем, к примеру, testdisk и восстанавливаем флаг.

Флаг: solar{d@ta_r3cov3r3d}

**Solution**:
---
The file is a raw image in FAT32 format, which contains two files - a message and a fake flag. We need to find the real flag.

For searching, we use, for example, testdisk and restore the flag.

Flag: solar{d@ta_r3cov3r3d}