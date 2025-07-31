# Riddler`s Riddle

![alt text](Crypto.jpg)

**Формат флага/Flag format**: solar{}

**Файлы/Files**: [task.zip](task.zip)
---

**Описание**:
---
 Ах, добро пожаловать, умник! Игра началась, и только те, у кого острый ум, смогут победить. В этом испытании скрыты замаскированные подсказки и тайны - загадки, которые дразнят секреты открытых шифров и ключей, которые их открывают. Ты готов сыграть в мою маленькую игру?

**Description**:
---
Ah, welcome, clever one! The game is afoot, and only those with a sharp mind shall preveil. Hidden within this challenge are clies cloaked and mistery - riddles that tease the secrets of the open cipheres and the keys that unlock them. Are you ready to play my little game?

**Идея задачи**:
---
Кроме зашифрованного текста нам даны две загадки, в которых скрыты наименования шифров и ключи к данным шифрам. В остальном - здесь используется два известных шифра и все.

**Problem idea**:
---
In addition to the encrypted text, we are given two riddles, in which the names of the ciphers and the keys to these ciphers are hidden. Otherwise, two known ciphers are used here and that's it.

**Решение**:
---
Первая загадка:

*In ancient scrolls, my trace is found,**
*A winding path where secrets abound,*
*To unlock the cipher, ponder the clue well:*
*How many digits on your hand can you tell?*

Ответом на эту загадку будет шифр сцитала (скитала), где для шифрования использовалась пергаментная лента и палочка цилиндрической формы. Ключ к шифру - 5, поскольку мы одной рукой можем посчитать только до 5.

Вторая загадка:

*Imagine a fence not meant for a home,*
*But with three neat rows where secrets roam,*
*Count the paths that cross and weave throught the air,*
*And the key to this cipher will soon be there.*

Ответом на эту загадку будет шифр Rail Fence (рельсового ограждения), ключ к которому - 3.

Далее нужно понять, в какой последовательности нужно расшифровать и написать скрипт для дешифровки на базе полученных данных:

```
def rail(cipher, rails):
    fence = [['' for _ in range(len(cipher))] for _ in range(rails)]
    idx = 0
    row, step = 0, 1

    for i in range(len(cipher)):
        fence[row][i] = '*'
        if row == 0:
            step = 1
        elif row == rails - 1:
            step = -1
        row += step

    for r in range(rails):
        for c in range(len(cipher)):
            if fence[r][c] == '*' and idx < len(cipher):
                fence[r][c] = cipher[idx]
                idx += 1
    result = []
    row, step = 0, 1
    for i in range(len(cipher)):
        result.append(fence[row][i])
        if row == 0:
            step = 1
        elif row == rails - 1:
            step = -1
        row += step
    return ''.join(result)

ciphertext = ""

with open('for_riddlers.txt', 'r') as f:
    ciphertext = f.read()
rails = 3

decrypted = rail(ciphertext, rails)

with open('for_scitale.txt', 'w') as f:
    f.write(decrypted)

def scytale(cipher, key):
    num_cols = len(cipher) // key
    decrypted = [''] * num_cols
    for i, char in enumerate(cipher):
        decrypted[i % num_cols] += char
    return ''.join(decrypted)
text = ""

with open ('for_scitale.txt', 'r') as f:
    text = f.read()
decrypted_text = scytale(text, 5)
 
with open('flag.txt', 'w') as f:
    f.write(decrypted_text)
```

И по итогу получим наш желанный флаг:
solar{3ncRypt10n_a4d_r1DDl3_1s_f4n}


**Solution**:
---
First riddle:

*In ancient scrolls, my trace is found,**
*A winding path where secrets abound,*
*To unlock the cipher, ponder the clue well:*
*How many digits on your hand can you tell?*

The answer to this riddle is the scytale cipher, where a parchment strip and a cylindrical stick were used for encryption. The key to the cipher is 5, since we can only count to 5 with one hand.

Second riddle:

*Imagine a fence not meant for a home,*
*But with three neat rows where secrets roam,*
*Count the paths that cross and weave throught the air,*
*And the key to this cipher will soon be there.*

The answer to this riddle is the Rail Fence cipher, the key to which is 3.

Next, you need to figure out the sequence in which to decrypt and write a script to decrypt based on the data you received:

```
def rail(cipher, rails):
    fence = [['' for _ in range(len(cipher))] for _ in range(rails)]
    idx = 0
    row, step = 0, 1

    for i in range(len(cipher)):
        fence[row][i] = '*'
        if row == 0:
            step = 1
        elif row == rails - 1:
            step = -1
        row += step

    for r in range(rails):
        for c in range(len(cipher)):
            if fence[r][c] == '*' and idx < len(cipher):
                fence[r][c] = cipher[idx]
                idx += 1
    result = []
    row, step = 0, 1
    for i in range(len(cipher)):
        result.append(fence[row][i])
        if row == 0:
            step = 1
        elif row == rails - 1:
            step = -1
        row += step
    return ''.join(result)

ciphertext = ""

with open('for_riddlers.txt', 'r') as f:
    ciphertext = f.read()
rails = 3

decrypted = rail(ciphertext, rails)

with open('for_scitale.txt', 'w') as f:
    f.write(decrypted)

def scytale(cipher, key):
    num_cols = len(cipher) // key
    decrypted = [''] * num_cols
    for i, char in enumerate(cipher):
        decrypted[i % num_cols] += char
    return ''.join(decrypted)
text = ""

with open ('for_scitale.txt', 'r') as f:
    text = f.read()
decrypted_text = scytale(text, 5)
 
with open('flag.txt', 'w') as f:
    f.write(decrypted_text)
```

And in the end we will get our desired flag:
solar{3ncRypt10n_a4d_r1DDl3_1s_f4n}