# Криптография
## Задание 1
### Запускаем атаку

```
PS C:\hashcat-7.1.2> .\hashcat.exe -m 1400 -a 0 --username .\task1_hashes.txt .\rockyou.txt
hashcat (v7.1.2) starting

Failed to initialize the AMD main driver HIP runtime library. Please install the AMD HIP SDK.

Failed to initialize AMD HIP RTC library. Please install the AMD HIP SDK.

OpenCL API (OpenCL 2.1 AMD-APP (3652.0)) - Platform #1 [Advanced Micro Devices, Inc.]
=====================================================================================
* Device #01: AMD Radeon RX 6600, 8176/8176 MB (6732 MB allocatable), 14MCU

Minimum password length supported by kernel: 0
Maximum password length supported by kernel: 256

Hashes: 5 digests; 5 unique digests, 1 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 1

Optimizers applied:
* Zero-Byte
* Early-Skip
* Not-Salted
* Not-Iterated
* Single-Salt
* Raw-Hash

ATTENTION! Pure (unoptimized) backend kernels selected.
Pure kernels can crack longer passwords, but drastically reduce performance.
If you want to switch to optimized kernels, append -O to your commandline.
See the above message to find out about the exact limits.

Watchdog: Temperature abort trigger set to 90c

Host memory allocated for this attack: 757 MB (21287 MB free)

Dictionary cache built:
* Filename..: .\rockyou.txt
* Passwords.: 14344392
* Bytes.....: 139921507
* Keyspace..: 14344385
* Runtime...: 1 sec

a87db2423196431c88a1bdfc21d224b9faf9de74cadb7a578930bed9d5e86382:MILO2008
7244957cda5cb2e115aebf8e30c5bd7e539d250f03c1d80fde0c535348e94b4a:washington1776
3b95ecea8aca178ebfbaac1b46f2b0bde7e8b4b2353ffffeea74c5092e3a7159:mmr431723
367c8a75d581c986d352b9ae050ade399506b706d8ddf1b24016b07da1ec307e:hxtour
Approaching final keyspace - workload adjusted.


Session..........: hashcat
Status...........: Exhausted
Hash.Mode........: 1400 (SHA2-256)
Hash.Target......: .\task1_hashes.txt
Time.Started.....: Sun Apr 19 22:00:32 2026 (0 secs)
Time.Estimated...: Sun Apr 19 22:00:32 2026 (0 secs)
Kernel.Feature...: Pure Kernel (password length 0-256 bytes)
Guess.Base.......: File (.\rockyou.txt)
Guess.Queue......: 1/1 (100.00%)
Speed.#01........: 24297.0 kH/s (2.64ms) @ Accel:1024 Loops:1 Thr:64 Vec:1
Recovered........: 4/5 (80.00%) Digests (total), 4/5 (80.00%) Digests (new)
Progress.........: 14344385/14344385 (100.00%)
Rejected.........: 0/14344385 (0.00%)
Restore.Point....: 14344385/14344385 (100.00%)
Restore.Sub.#01..: Salt:0 Amplifier:0-1 Iteration:0-1
Candidate.Engine.: Device Generator
Candidates.#01...: 0844132938 -> $HEX[042a0337c2a156616d6f732103]
Hardware.Mon.#01.: Temp: 43c Fan:  0% Util:  8% Core: 217MHz Mem:1742MHz Bus:8

Started: Sun Apr 19 22:00:29 2026
Stopped: Sun Apr 19 22:00:34 2026
PS C:\hashcat-7.1.2>
```
### Просмотр результатов.
```
PS C:\hashcat-7.1.2> .\hashcat.exe -m 1400 --username .\task1_hashes.txt --show
Mixing --show with --username or --dynamic-x can cause exponential delay in output.

user:a87db2423196431c88a1bdfc21d224b9faf9de74cadb7a578930bed9d5e86382:MILO2008
admin:367c8a75d581c986d352b9ae050ade399506b706d8ddf1b24016b07da1ec307e:hxtour
root:7244957cda5cb2e115aebf8e30c5bd7e539d250f03c1d80fde0c535348e94b4a:washington1776
db_user:3b95ecea8aca178ebfbaac1b46f2b0bde7e8b4b2353ffffeea74c5092e3a7159:mmr431723
```
### Тип хэша:
SHA-256 (-m 1400)
### В итоге мы получили:
user->MILO2008
admin->hxtour
root->washington1776
db_user->mmr431723
web_admin->не восстановлен

> Для повышения эффективности атаки могут использоваться правила мутаций (rules), комбинированные атаки и расширенные словари. 

## Задание 2
### Тип хэша определен
Длина составляет 128 символов
```
PS C:\hashcat-7.1.2> (Get-Content .\task2_hashes.txt)[0].Length
128
```
### Метод атаки:
mask attack, т.к. пин состоит только из цифр + длина ограничена (4-6 символов)
### Используем маски:
?d?d?d?d & ?d?d?d?d?d & ?d?d?d?d?d?d

### Команды
```
hashcat -m 1700 -a 3 -O task2_hashes.txt ?d?d?d?d
hashcat -m 1700 -a 3 -O task2_hashes.txt ?d?d?d?d?d
hashcat -m 1700 -a 3 -O task2_hashes.txt ?d?d?d?d?d?d
```

### Вывод

```
PS C:\hashcat-7.1.2> .\hashcat.exe -m 1700 .\task2_hashes.txt --show
75d25e48a3d92c398bb6a7873d6a22281f6bdd50f78956f666f717135190127cbbeec3fd35b9fb03925d6bf595baa022d10d247104cced3a0a8f4a6656c4bf6a:5472
684a71e209bad7d9c3a802386150a24b31be323e7e42624bbe787e381cfe0796820fb1aeabb45ec966c6e427babb5ece40824297dac97c37f2e41be6958ea324:497235
8f2090b09018f7431d25a92da885c6f3e80ea538778639072aa15b7484b44d92ecb6cae59350f3bd1846ab492e8604f8d3b25f0e5842c2335b0b03bae5e690c0:11082
7765080f31bffe1d14ff17db9316b538db5761ea5592454f3d7a71961567af39e91c1c60898bda23f0c6514b0c6ff8e3c830a22846fe1af94b2d6023c89449a1:4653
7c3a635c9bbedd8f74ddb9cdcea921368e728b6f65cdae7a6eec537748cf8831e57a8706494220b9caf695b4cb79aa655c7c6b635b49c1fdc318ea410c0ae49f:17456
PS C:\hashcat-7.1.2>
```

### Результаты
1. 5472
2. 497235
3. 11082
4. 4653
5. 17456

## Задание 3

### Тип и длина хэшей определена:
SHA256 с добавленной солью (-m 1410) -> sha256($pass.$salt)
### Формат записи:
******(hash).****(salt)
### Используемая команда:
```
PS C:\hashcat-7.1.2> .\hashcat.exe -m 1410 -a 0 -O .\task3_hashes.txt .\rockyou.txt
hashcat (v7.1.2) starting

Failed to initialize the AMD main driver HIP runtime library. Please install the AMD HIP SDK.

Failed to initialize AMD HIP RTC library. Please install the AMD HIP SDK.

OpenCL API (OpenCL 2.1 AMD-APP (3652.0)) - Platform #1 [Advanced Micro Devices, Inc.]
=====================================================================================
* Device #01: AMD Radeon RX 6600, 8176/8176 MB (6732 MB allocatable), 14MCU

Minimum password length supported by kernel: 0
Maximum password length supported by kernel: 31
Minimum salt length supported by kernel: 0
Maximum salt length supported by kernel: 51

Hashes: 5 digests; 5 unique digests, 5 unique salts
Bitmaps: 16 bits, 65536 entries, 0x0000ffff mask, 262144 bytes, 5/13 rotates
Rules: 1

Optimizers applied:
* Optimized-Kernel
* Zero-Byte
* Precompute-Init
* Early-Skip
* Not-Iterated
* Appended-Salt
* Raw-Hash

Watchdog: Temperature abort trigger set to 90c

Host memory allocated for this attack: 1495 MB (21196 MB free)

Dictionary cache hit:
* Filename..: .\rockyou.txt
* Passwords.: 14344385
* Bytes.....: 139921507
* Keyspace..: 14344385

433a276d5c258c089d803c77b76e7367f772f6c4c34fc524c70cda9bc5e3828d:2560:656800
ef62c8bbf7e8bb6e57ca5d8153c7e11864c0ce4cb0be51ee50ebff4e42750dee:6766:rubenkus
Approaching final keyspace - workload adjusted.

44ca6adee541830e8c69ced64b361a51f3be10acb7286af94922449e4b164fd5:3780:cup+preds
6c39425f74db54f7d99cbfb1a12816421b1a1db02003bfbe3270ec0113726b25:9117:428248h
70ab6e15b42f3e8addef4be9651f8c6f872dc8ac5a36d2b6160493bcc3d4f987:1337:54cami9

Session..........: hashcat
Status...........: Cracked
Hash.Mode........: 1410 (sha256($pass.$salt))
Hash.Target......: .\task3_hashes.txt
Time.Started.....: Sun Apr 19 22:40:22 2026 (1 sec)
Time.Estimated...: Sun Apr 19 22:40:23 2026 (0 secs)
Kernel.Feature...: Optimized Kernel (password length 0-31 bytes)
Guess.Base.......: File (.\rockyou.txt)
Guess.Queue......: 1/1 (100.00%)
Speed.#01........: 99757.0 kH/s (4.69ms) @ Accel:1024 Loops:1 Thr:256 Vec:1
Recovered........: 5/5 (100.00%) Digests (total), 5/5 (100.00%) Digests (new), 5/5 (100.00%) Salts
Progress.........: 71721925/71721925 (100.00%)
Rejected.........: 15470/71721925 (0.02%)
Restore.Point....: 11012172/14344385 (76.77%)
Restore.Sub.#01..: Salt:4 Amplifier:0-1 Iteration:0-1
Candidate.Engine.: Device Generator
Candidates.#01...: Jonathan81 -> $HEX[042a0337c2a156616d6f732103]
Hardware.Mon.#01.: Temp: 46c Fan: 0% Util: 33% Core:1400MHz Mem:1744MHz Bus:8

Started: Sun Apr 19 22:40:08 2026
Stopped: Sun Apr 19 22:40:23 2026
PS C:\hashcat-7.1.2>
```

### Результаты
54cami9
cup+preds
656800
rubenkus
428248h

## Задание 4

### Использовал сервис:
[CrackStation](https://crackstation.net)

### Результат первого хэша - superpassword
[Хэш №1](images/cs_hash1.png)
### Результат второго хэша - qwertyui
[Хэш №2](images/cs_hash2.png)
### Результат третьего хэша - P@ssw0rd!
[Хэш №3](images/cs_hash3.png)
### Результат четвертого хэша - azekami
[Хэш №4](images/cs_hash4.png)
### Результат пятого хэша - hesoyam
[Хэш №5](images/cs_hash5.png)
