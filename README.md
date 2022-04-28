# Описание UART-протокола wifi-модулей кондиционеров, произведенных на заводах AUX.

## Параметры UART
Скорость: 4800
Формат: 4800/8-E-1
Описание: один стартовый `0`, 8 бит данных, один бит четности (равен `1`, если в битах данных нечетное количество единиц) и одна стоповая единица, передача на скорости 4800 бод.

## Структура пакетов
Каждое сообщение, передаваемое по UART, имеет:
1. **заголовок**: 8 байт;
2. **тело**: от 0 до X байт;
3. **контрольную сумму**: 2 байта, CRC16.

### Заголовок
Это обязательная часть пакета.
| START |   ?   | TYPE  | wifi? |   ?   |   ?   |  LEN  |   ?   |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
|   0   |   1   |   2   |   3   |   4   |   5   |   6   |   7   |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
|  0xBB |  0x00 |  0x01 |  0x00 |  0x00 |  0x00 |  0x00 |  0x00 |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |


