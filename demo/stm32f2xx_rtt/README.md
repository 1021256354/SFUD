# stm32f2xx RT-Thread Demo

---

## 1�����

�� Demo ʹ�� RT-Thread �����Ŷӵ� [ART-WiFi](http://www.rt-thread.org/product/5.html) �����壬����� `STM32F205RG` ������������� `W25Q64` SPI Flash��������һ· SPI ���ߣ����Ի��������һ· SPI Flash����ͼ��ʾ
![RTT_ART_WiFi](http://git.oschina.net/Armink/SFUD/raw/master/docs/zh/images/RTT_ART_WiFi.jpg)

> ע�⣺���û�� ART_WiFi �����壬ֻҪ���������ƣ�ͬ������ʹ�ô� Demo ��

### 1.1��ʹ�÷���

- Flash �豸���� `components/sfud/inc/sfud_cfg.h` �е� `SFUD_FLASH_DEVICE_TABLE` �궨���ж������� Flash �豸����һ��Ϊ���ص� `W25Q64` ���ڶ��������Լ���ӵ� `W25Q16`�����û����ӻ���ӵ������� Flash �����Բο� [��ҳ�ĵ��н��ܵ� Flash �豸�����÷���](https://github.com/armink/SFUD#234-flash-�豸��) �����޸ġ�
- SFUD ��ʼ������ `app/src/app_task.c` �� `sys_init_thread` �߳�����ɶ� SFUD �ĳ�ʼ����
- �����նˣ���ʼ����ɺ���Խ������е��ն��뿪�������ӣ�����1�������ն����������������ɲ��Թ��̡�

#### 1.1.1 Flash ��������

```
msh >sf
Usage:
sf select [index]             - select a flash chip with device's index
sf read addr size             - read 'size' bytes starting at 'addr'
sf write addr data1 ... dataN - write some bytes 'data' to flash starting at 'addr'
sf erase addr size            - erase 'size' bytes starting at 'addr'
sf bench                      - full chip benchmark test

```

���磺

- 1��ѡ���һ��(������ֵΪ 0) Flash �豸���в�����������������ѡ��󣬽������Ĳ���������Դ� Flash �豸��

```
msh >sf select 0
8 MB W25Q64 is current selected device.
```

- 2����ȡ�ӵ�ַ 0 ��ʼ������ 64 �ֽ����ݣ�������������

```
msh >sf read 0 64
Read the W25Q64 flash data success. Start from 0x00000000, size is 64. The data is:
Offset (h) 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
[00000000] 54 00 00 00 90 8F E3 A7 69 61 70 5F 6E 65 65 64 
[00000010] 5F 63 6F 70 79 5F 61 70 70 3D 30 00 69 61 70 5F 
[00000020] 63 6F 70 79 5F 61 70 70 5F 73 69 7A 65 3D 30 00 
[00000030] 73 74 6F 70 5F 69 6E 5F 62 6F 6F 74 6C 6F 61 64 
```

- 3��д���ݴӵ�ַ 10 ��ʼ������ 5 �ֽ����ݣ�������������

```
msh >sf write 10 1 2 3 4 5
Write the W25Q64 flash data success. Start from 0x0000000A, size is 5.
Write data: 1 2 3 4 5 .
```

- 4�������ӵ�ַ 0 ��ʼ������ 8192 �ֽ����ݣ�������������

```
msh >sf erase 0 8192
Erase the W25Q64 flash data success. Start from 0x00000000, size is 8192
```

- 5������ Flash ȫƬ�����ܣ����������£�

```
msh >sf bench
Erasing the W25Q64 8388608 bytes data, waiting...
Erase benchmark success, total time: 20.591S.
Writing the W25Q64 8388608 bytes data, waiting...
Write benchmark success, total time: 32.768S.
Reading the W25Q64 8388608 bytes data, waiting...
Read benchmark success, total time: 16.129S.
```

�������ܲ��Խ������ [`/docs/zh/benchmark.txt`](https://github.com/armink/SFUD/blob/master/docs/zh/benchmark.txt)

#### 1.1.2 ��ȡ/�޸� Flash ״̬����

```
flash_status <read|write> <device_index> [<1:volatile|0:non-volatile> <status>]
```

## 2���ļ����У�˵��

- `components\sfud\port\sfud_port.c` ��ֲ�ο��ļ�
- `components\sfud\inc\sfud_cfg.c` �������ļ�

`RVMDK` ��ΪKeil�����ļ������ڼ��룩

`EWARM` ��ΪIAR�����ļ�