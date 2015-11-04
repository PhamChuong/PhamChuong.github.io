---
published: true
title: CEPH - REPLICATION
layout: post
tags: [CEPH]
---
Replication là phương pháp lưu trữ các dữ liệu tương tụ nhau trên nhiều vị trí khác nhau . Với Replication thì hiệu suất cũng như độ tin cậy về dữ liệu rất cao , việc phục hồi dữ liẹu rất nhanh .
Với Ceph thì replication sử dụng CRUSH algorithm dùng để tính toán 1 object được replicate ở đâu.
Để rõ ràng hơn mọi người xem : 
1 client sẽ sử dụng CRUSH algorithm để tính toán nơi lưu trữ , nằm ở đâu trong pool và placement group . KHi nhìn vào Crush map biết được  primary OSD của placement group .
Tiếp theo đó client sẽ ghi đúng vào primary OSD sau khi đã xác định . Sau đó primary OSD sẽ copy vào các secondary and tertiary OSDs  . Sau khi copy xong sẽ gưởi 1 response cho client biết object đã lưu xong .