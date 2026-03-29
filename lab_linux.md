# Лабораторная работа по Linux и Git

## Команды выполненных работ и комментарии

Создание виртуальной машины и настройка пользователя — screen_1  
Удаление git и попытка установки — screen_2  
Поиск и устранение проблемы с репозиториями — screen_3  
Успешная установка git — screen_4  

---

## Работа с командами Linux

```bash
git --version
sudo apt remove git -y
git

sudo apt update
sudo apt install git -y
git --version

ping -c 4 google.com

mkdir lab
cd lab
pwd

touch file1.txt
echo "Hello" > file1.txt
cat file1.txt
nano file1.txt

ls
ls -la

head file1.txt
tail file1.txt
less file1.txt

mkdir testdir
cd testdir
touch text.txt
cd ..

tree

rm file1.txt
rmdir testdir
rm testdir/text.txt
rmdir testdir
```

Комментарий:  
Команда `rmdir` не удаляет директорию, если она не пустая.

---

## Работа со snapshot

Установлен пакет:

```bash
sudo apt install htop -y
htop
```

Демонстрация работы — screen_5  

После этого выполнен откат системы через snapshot — screen_6  

---

## Настройка sudo

В файл `/etc/sudoers` была добавлена строка:

```
jetjoyred ALL=(ALL) NOPASSWD: ALL
```

После этого команды с `sudo` выполняются без запроса пароля.
