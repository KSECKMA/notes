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
