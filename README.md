# Write-up-CSAW-CTF-Qualification-Round-2022
## Word Wide Web (web)
Trang web này khi vào sẽ ra một list các title và chỉ có 1 title là có tag href dẫn đến path tiếp theo và khi vào path hiện tại vd: 
`http://web.chal.csaw.io:5010/stuff`
trang web sẽ tự động cập nhật cookie với cú pháp cookie = cookie + path
Để vào được path tiếp theo cookie phải bao gôm path của web trước đó và đoạn script sẽ giải quyết 
```
import requests 
import string
payload="stuff"
cookie="stuff"
while True: 
    url = "http://web.chal.csaw.io:5010/"+payload
    burp0_cookies = {"solChain": cookie}
    re=requests.get(url=url, cookies=burp0_cookies)
    flag=re.text
    print(flag)
    flag=flag.split(chr(10))
    for line in flag:
        if "<a href=" in line:
            break
    flag=line.split("\"")
    print(flag)
    flag=flag[1]
    print(flag)
    flag=flag[1:]
    print(flag)
    cookie=cookie+" "+flag
    payload=flag
    print(cookie)
    print("----------------------------------------")
```
![image](https://user-images.githubusercontent.com/82523299/189525673-50d0b957-aef5-480b-afad-9d396a6061e6.png)
### Flag: `CTF{w0rdS_4R3_4mAz1nG_r1ght}`
## 2. Our Spy In New Terrain (OSINT)
Đây là thử thách phải vượt qua nhiều vòng, như wayback , morse, repo github, các thông tin về thành phố , ngân hàng
![image](https://user-images.githubusercontent.com/82523299/189528598-f3996c45-d48d-461a-9b94-db7db6689397.png)
### Flag: flag{C0N6r475463N7600DW0rKN3X771M3N0PU811C53rV3r}

