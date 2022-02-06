# Установка OpenSSL 3 версии на Ubuntu

## Шаг 0
Обновляем все репозитории и софт
```
sudo apt update && sudo apt upgrade -y
```
Устанавливаем пакет build-essential
```
sudo apt install build-essential
```

## Шаг 1
Необходимо избавиться от идущей из коробки версии OpenSSL.
```
sudo apt remove openssl 
```
## Шаг 2
Архив с исходниками новой версии можно достать по 2 адресам
https://www.openssl.org/source/ \
https://github.com/openssl/openssl/tags
```
wget --no-check-certificate https://www.openssl.org/source/openssl-3.0.1.tar.gz
```
Распаковываем архив:
```
tar -xvzf openssl-3.0.1.tar.gz
```
## Шаг 3
Заходим в распакованную папку и вводим по очереди следующие команды, дожидаясь выполнения каждой.
```
cd openssl-3.0.1
chmod +x ./config
./Configure
make
make test
make install
sudo ldconfig /usr/local/lib64/
```
Делаем ссылку:
```
ln -s /usr/local/bin/openssl /usr/bin/
```
Проверяем версию:
```
openssl version
```