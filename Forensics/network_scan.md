# Một vài kỹ thuật sử dụng để xác định mô hình mạng

1. Nmap
```bash
nmap -p 1-65535 -T4 -A -v 192.168.1.1
```
2. Linux ping sweep
```bash
for i in `seq 1 255`; do ping -c 1 10.10.10.$i | tr \\n ' ' | awk '/1 received/ { print $2}'; done
```
3. Window ping sweep
```bash
FOR /L %i in (1,1,255) do @ping -n 1 10.10.10.%i | find "Reply"
```
