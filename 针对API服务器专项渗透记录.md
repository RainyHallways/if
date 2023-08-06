# 针对 `api.fastbuilder.pro` の专项渗透の记录

#### 1.使用Fofa引擎对域名进行IP地址检索
![sc](https://img1.imgtp.com/2023/08/06/iJaOFP1X.png)
获取后直接访问 `24.80.45.75`
发现为 `OpenWrt` 登录界面
使用 `OWASP ZAP` 进行抓包,获取请求 `Header` 及 `Body`
![oz](https://img1.imgtp.com/2023/08/06/FIRn4lCD.png)
将请求 `Header` 及 `Body` 代入 `PKAV` 进行字典爆破
![pkav](https://img1.imgtp.com/2023/08/06/PJ97gqYP.png)

> 恭喜,爆破并没有成功

#### 2.使用工具进行扫描
`Nmap` 扫描成果:
```txt
Host discovery disabled (-Pn). All addresses will be marked 'up' and scan times may be slower.
Starting Nmap 7.94 ( https://nmap.org ) at 2023-08-06 15:56 中国标准时间
NSE: Loaded 156 scripts for scanning.
NSE: Script Pre-scanning.
NSE: Starting runlevel 1 (of 3) scan.
Initiating NSE at 15:56
Completed NSE at 15:56, 0.00s elapsed
NSE: Starting runlevel 2 (of 3) scan.
Initiating NSE at 15:56
Completed NSE at 15:56, 0.00s elapsed
NSE: Starting runlevel 3 (of 3) scan.
Initiating NSE at 15:56
Completed NSE at 15:56, 0.00s elapsed
Initiating SYN Stealth Scan at 15:56
Discovered open port 80/tcp on 24.80.45.75
Discovered open port 443/tcp on 24.80.45.75
Discovered open port 32768/tcp on 24.80.45.75
Completed SYN Stealth Scan at 15:58, 101.96s elapsed (1000 total ports)
Initiating UDP Scan at 15:58
Scanning 24.80.45.75 [1000 ports]
Completed UDP Scan at 16:42, 2628.97s elapsed (1000 total ports)
Not shown: 996 filtered tcp ports (no-response), 1 filtered tcp ports (port-unreach)
PORT      STATE SERVICE
80/tcp    open  http
443/tcp   open  https
32768/tcp open  filenet-tms
```
微步云给出的结果:
```txt
24.80.45.75开放的端口:80,443,2053这3个端口。
24.80.45.75部署的应用或服务:WebSocket++(版本0.8.3-dev),Apache(版本2.4.54 (Debian))。
```