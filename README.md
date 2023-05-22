# RM toolkit System view
## Serial
19200 baud, inverted rx/tx
## Description
RM Toolkit's System view tab data except Mainboard serial number
## Request protocol
```
0xAA 0x07 0x14 0x01 0x00 0x00 0x39
```
## Response protocol
Byte index|Example bytes (hex)|Description|Value length|Value type|Scale
----------|-------------------|-----------|------------|----------|-----
0|aa|Preamble (fix 0xAA)|1 byte|fix|-
1|55|Length (full packet length, included preamble + length + CRC bytes)|1 byte|value|1/bit
2|14 01|Request ID???|2 bytes|value|1/bit
4|0|Bumper state|1 bytes|mapping|0=clear, 1=left, 2=right, 3=front
5|42|Bumper reading L|1 byte|value|1/bit
6|42|Bumper reading R|1 byte|value|1/bit
7|0|???|||
8|0|???|||
9|0|Front wheel active|1 byte|bool|1bit
10|2|Front wheel reading|1 byte|value|1/bit
11|0|???|||
12|0|???|||
13|0|Cover active|1 byte|bool|1bit
14|3|Cover reading|1 byte|value|1/bit
15|3|Wire state LR|1 byte|mapping|0=ININ, 1=INOUT, 2=OUTIN, 3=OUTOUT
16|11|Wire amplitude L|1 byte|value|1/bit
17|12|Wire amplitude R|1 byte|value|1/bit
18|3|Wire gain L|1 byte|value |1/bit
19|3|Wire gain R|1 byte|value |1/bit
20|0|Wire active (!)|1 byte|bool|1bit
21|00 00|Wire count L|2 bytes|value|signed 1/bit
23|00 00|Wire count R|2 bytes|value|signed 1/bit
25|0|Remote control active|1 bytes|bool |1bit
26|0|Remote control|1 bytes|mapping|1=safety, 2=mow, 4=left, 8=backward, 16=right, 32=forward
27|0|Mow active|1 bytes|bool|1bit
28|0|Mow power|1 bytes|value|1%/bit
29|00 00|Mow current|2 bytes|value|0.001A/bit
31|00 16|Mow temperature|2 bytes|value|signed 1°C/bit
33|0|Mow over-current|1 byte|bool|1bit
34|0|Drive active|1 byte|bool|1bit
35|0|Drive power L|1 bytes|value|1%/bit
36|0|Drive power R|2 bytes|value|1%/bit
37|00 00|Drive current L|2 bytes|value|0.001A/bit
39|00 00|Drive current R|2 bytes|value|0.001A/bit
41|00 16|Drive temperature L|2 bytes|value|signed 1°C/bit
43|00 16|Drive temperature R|2 bytes|value|signed 1°C/bit
45|0|Drive speed L|1 bytes|value|1%/bit
46|0|Drive speed R|1 bytes|value|1%/bit
47|0|Drive over-current L|1 bytes|bool|1bit
48|0|Drive over-current R|1 bytes|bool|1bit
49|64 fb|Battery voltage|2 bytes|value|0.001V/bit
51|00 16|Battery temperature|2 bytes|value|signed 1°C/bit
53|0|Battery type|1 bytes|mapping|1=Lead acid, 2=NiMh
54|25 a8|Charging voltage|2 bytes|value|0.001V/bit
56|00 02|Charging current|2 bytes|value|0.001A/bit
58|0|Charging power|1 byte|value|1%/bit
59|0|Charging state|1 byte|value|1/bit
60|0|Push buttons|1 byte|mapping|1=GO, 2=STOP, 4=UP, 8=DOWN, 16=ON/OFF
61|1d|Rain sensor reading|1 byte|value|1/bit
62|0|Rain sensor active|1 byte|bool|1bit
63|0|Tilt|1 byte|bool|1bit
64|01 38|Drive direction|2 bytes|value|1°/bit
66|00 00 00 11|Drive distance|4 bytes|value|1cm/bit
70|00 00 00 00|Drive ticks L|4 bytes|value|1tick/bit
74|00 00 00 5d|Drive ticks R|4 bytes|value|1tick/bit
78|0|???|||
79|1e|???|||
80|2|Software|1 byte|mapping|1=v5.2, 2=v5.4, 3=v1.1 
81|4|Mainboard|1 byte|mapping|1=ESB5000E, 2=ESB5000F, 3=ESB5000G, 4=ESB5000H
82|29|Base|1 byte|value|1/bit
83|0|???|||
84|a2|CRC|1 byte|value|1/bit
