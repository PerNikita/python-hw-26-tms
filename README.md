# python-hw-26-tms

Задание:
1 Написать скрипт, который принимает на вход список IP-адресов и
проверяет их доступность с помощью ping-запросов. Результаты
проверки сохраняются в отдельный файл.
```
import subprocess

def ping_host(host):
    command = ['ping', '-c', '4', host]   
    process = subprocess.Popen(command, stdout=subprocess.PIPE, stderr=subprocess.PIPE, text=True)
    stdout, stderr = process.communicate()

    if process.returncode == 0:
        return True, stdout
    else:
        return False, stderr

HOSTS = ["192.168.1.1", "192.168.1.2", "192.168.1.3"]

for host in HOSTS:
    success, output = ping_host(host)
    print(host)
    
    if success:
        print("Успешно:")
        print(output)
    else:
        print("Ошибка:")
        print(output)
```
4 Написать скрипт, который принимает на вход массив чисел и сортирует
его в порядке убывания.

```
NUMBERS=[1,3,2,4,5,6,7]

sort = sorted(NUMBERS, reverse=True)
print(sort)
```

5 Написать скрипт, который принимает на вход кортеж и проверяет, все
ли его элементы являются уникальными.
```
from collections import Counter

TUPLE = (1,3,2,4,5,6,7,2,4,1)
counts = Counter(TUPLE)
duplicates = [item for item, count in counts.items() if count > 1]
for item in set(TUPLE):
    if item in duplicates:
        print(f"{item} повторяется")
    else:
        print(f"{item} уникален")
```
