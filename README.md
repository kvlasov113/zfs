## https://github.com/kvlasov113/zfs/
## Практическая работа по zfs
## Вывод команд записывался утилитой script --> zfs.log
## Скрипт утсановки zfs в теле файла вагрант.

## Определить алгоритм с наилучшим сжатием

Команда zpool status показывает информацию о каждом диске, состоянии сканирования и об ошибках чтения, записи и совпадения хэш-сумм. 
Команда zpool list показывает информацию о размере пула, количеству занятого и свободного места, дедупликации и т.д. 


### Добавим разные алгоритмы сжатия в каждую файловую систему:
Алгоритм lzjb: zfs set compression=lzjb otus1
Алгоритм lz4:  zfs set compression=lz4 otus2
Алгоритм gzip: zfs set compression=gzip-9 otus3
Алгоритм zle:  zfs set compression=zle otus4

### Определить настройки пула
zpool import -d zpoolexport/ otus
zpool get all otus

### Работа со снапшотами
Восстановим файловую систему из снапшота: zfs receive otus/test@today < otus_task2.file

