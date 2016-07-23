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
Flash <read|write|erase|benchmark> <device_index> <addr> <size>
```

���磺

- 1����ȡ��һ�� Flash �豸�Ĵӵ�ַ 0 ��ʼ������ 64 �ֽ����ݣ�������������

```
msh >flash read 0 0 64
```

- 2��д���ݴӵ�ַ 10 ��ʼ������ 5 �ֽ����ݵ��ڶ��� Flash �豸��������������

```
msh >flash write 0 10 5 1 2 3 4 5 
```

- 3�������ӵ�ַ 0 ��ʼ������ 8192 �ֽ����ݵ���һ�� Flash �豸��������������

```
msh >flash erase 0 0 8192
```

- 4�����Ե�һ�� Flash �豸ȫƬ�����ƣ� 8388608 �ֽڣ������ܣ����������£�

```
msh >flash benchmark 0 0 8388608
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