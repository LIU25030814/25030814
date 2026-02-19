# 25030814
2026/2/14
## 1.Recon-ng
>Due to the fact that **Rrcon-ng V5** does not come with built-in modules, all functions need to be downloaded from the **marketplace**.

```
marketplace install all
```
<img width="551" height="95" alt="image" src="https://github.com/user-attachments/assets/39a0fb1d-0cfd-4447-8539-5fccac76f85a" />


### 1.1 Collect subdomains
```
modules search bing
```
<img width="490" height="163" alt="image" src="https://github.com/user-attachments/assets/d02bf7e4-c091-4470-86bf-660e126d9ad9" />

```
module load <Module Name>
```
```
option set SOURCE example.com
```
```
run
```
<img width="628" height="144" alt="image" src="https://github.com/user-attachments/assets/51c9c1bc-cff6-48d7-a998-4fff59511260" />

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

<img width="661" height="126" alt="image" src="https://github.com/user-attachments/assets/5cfebfd8-216f-4cf2-9e14-b3b60b9e2f93" />

### 1.3 DNS resolution
```
module load recon/hosts-hosts/resolve
```
```
run
```
<img width="524" height="35" alt="image" src="https://github.com/user-attachments/assets/e4155220-4ab5-460c-8cab-a9668e34fc76" />

-[渗透测试RECON-NG介绍](https://blog.csdn.net/weixin_42952508/article/details/124443273)
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
[Nmap完整使用教程](https://blog.csdn.net/wrjhs/article/details/147080972)
