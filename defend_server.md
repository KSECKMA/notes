---------------------------------------------------------------------------------------------------------------------------------
Script sử dụng để ngăn ngừa các user không được phép sử dụng các command hay shell. Sử dụng trong phòng thủ server với ctf attack and defend.
```bash
#!/bin/bash

cat /etc/passwd | cut -d ":" -f1 > /tmp/listuser_tmp
listuser=(`cat /tmp/listuser_tmp`)
cat /etc/passwd | cut -d ":" -f3 > /tmp/listuserid_tmp
listuserid=(`cat /tmp/listuserid_tmp`)
while true
do
    for t in "${!listuser[@]}"
    do
        if [ ${listuser[t]} != 'root' ]
        then
            sudo -u ${listuser[t]} pkill -U ${listuserid[t]} 'sh|nc|cat'
        fi
    done
done
```
---------------------------------------------------------------------------------------------------------------------------------
Liệt kê các user đang đăng nhập:
```bash
> who -u
mmrozek  tty1         Aug 17 10:03 09:01        9250
mmrozek  pts/3       Aug 17 10:09 01:46       19467 (:pts/2:S.0)
```
Troll user:
```bash
echo "HAHAHAHAHAHAHAHA" | write mmrozek pts/3
```
Kickout user:
```bash
kill -9 19467
```
