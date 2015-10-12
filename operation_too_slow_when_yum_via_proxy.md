Khi thêm một repo tại /etc/yum.repos.d và yum qua một proxy, gặp lỗi sau:

"Operation too slow. less than 1 bytes/sec transferred the last 30 seconds"

Cách fix:

Thêm hai dòng sau vào tập tin yum.conf
```
http_caching=packages
timeout=300
```
Trước khi cài đặt packages tại repo, cần chạy lệnh sau:
```
yum --enablerepo=<repo name> clean metadata
```
Done!
