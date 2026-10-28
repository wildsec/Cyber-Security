https://remnux.org/

## Oledump.py
is a Python tool that analyzes **OLE2** files
**OLE** stands for **Object Linking and Embedding**
OLE2 files are typically used to store multiple data types, such as documents, spreadsheets, and presentations, within a single file.
``` bash
oledump.py agenttesla.xlsm 

#output
A: xl/vbaProject.bin 
A1: 468 'PROJECT' 
A2: 62 'PROJECTwm' 
A3: m 169 'VBA/Sheet1' 
A4: M 688 'VBA/ThisWorkbook' 
A5: 7 'VBA/_VBA_PROJECT' 
A6: 209 'VBA/dir'
```

The A (index) +Numbers are called **data streams**
**M** means there is a **Macro**

``` bash
#s = select, 4 = datastream
oledump.py agenttesla.xlsm -s 4

#decompress any compressed VBA macros it finds into a more readable format
--vbadecompress
```

## INetSim
create fake newtwork

```bash
sudo nano /etc/inetsim/inetsim.conf
> dns_default_ip THISIP

sudo inetsim
> Simulation running.
```

## Volatility
[[Volatility]]