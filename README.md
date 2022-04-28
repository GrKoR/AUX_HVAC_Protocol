# Описание UART-протокола wifi-модулей кондиционеров, произведенных на заводах AUX.

## Параметры UART
Скорость: 4800
Формат: 4800/8-E-1
Описание: один стартовый `0`, 8 бит данных, один бит четности (равен `1`, если в битах данных нечетное количество единиц) и одна стоповая единица, передача на скорости 4800 бод.

## Структура пакета
Каждое сообщение, передаваемое по UART, имеет:
1. **заголовок**: 8 байт;
2. **тело**: от 0 до X байт;
3. **контрольную сумму**: 2 байта, CRC16.

### Заголовок
Это обязательная часть пакета.
| START |   ?   | TYPE  | wifi? |   ?   |   ?   |  LEN  |   ?   |
| ----- | ----- | ----- | ----- | ----- | ----- | ----- | ----- |
|   0   |   1   |   2   |   3   |   4   |   5   |   6   |   7   |
|  0xBB |  0x00 |  0x01 |  0x00 |  0x00 |  0x00 |  0x00 |  0x00 |

#### Байт 0, START
Номер в пакете:


| № байта | обозначение | описание |
| ------- | ----------- | -------- |
| 0       | **START**   | Стартовый байт. Всегда равен `0xBB`. |
| 1       | **?**   | Не расшифрован. Всегда равен `0x00`.  |
| 2       | **TYPE**   | тип команды. Пока встречал эти: Всегда равен `0xBB`. |
| 3       | **wifi?**   | Стартовый байт. Всегда равен `0xBB`. |
| 4       | **?**   | Стартовый байт. Всегда равен `0xBB`. |
| 5       | **?**   | Стартовый байт. Всегда равен `0xBB`. |
| 6       | **LEN**   | Стартовый байт. Всегда равен `0xBB`. |
| 7       | **?**   | Стартовый байт. Всегда равен `0xBB`. |


