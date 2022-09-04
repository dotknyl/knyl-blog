---
layout: "../../layouts/BlogPost.astro"
title: "Bài toán tối ưu"
description: "Có một bài toán trong sách giáo khoa lớp 8 nói vể sự tối ưu mà tới giờ mình vẫn nhớ…"
pubDate: "June 21, 2022 10:40 PM"
heroImage: "/images/bai-toan-toi-uu/Untitled.png"
tags: ["discuss", "career"]
---

Có một bài toán trong sách giáo khoa lớp 8 nói vể sự tối ưu mà tới giờ mình vẫn nhớ, cụ thể là tìm đường đi ngắn nhất từ điểm A đến bờ sông lấy nước rồi di chuyển đến đám cháy ở điểm B. Đây là một bài toán tối ưu về đường đi để ứng dụng được kiến thức trong bài đã dạy (và tất nhiên là mình không còn nhớ =]]). Lời giải của tác giả đưa ra là một điểm nào đó trên bờ sông nằm giữa vị trí hiện tại và đám cháy.

<div class="my-5" align="center">
    <img src="/images/bai-toan-toi-uu/Untitled.png" alt="Bài toán tối ưu" />
</div>

Tuy nhiên, cá nhân mình thấy đáp án đó không tối ưu trên thực tế, bởi vì người ra đề bài chỉ xét trên góc nhìn toán học.

Chúng ta chia quãng đường dập lửa thành 2 đoạn:

- Đoạn từ điểm xuất phát ra bờ sông: Vì chưa phải xách nước nên di chuyển dễ dàng và không tốn nhiều sức.

- Đoạn từ bờ sông xách nước tới đám cháy: Đoạn này di chuyển chậm và mất sức hơn do phải xách nhiều nước.

Lúc đó, trên góc nhìn của bản thân mình, bài toán này cần tối ưu thời gian, nhưng phải tính yếu tố vận tốc và sức lực bỏ ra để gánh nước, khi đó quãng đường đi ngắn nhất chưa hẳn đã tối ưu, vì phải gánh nước xa hơn. Vậy nên mình sẽ chọn sao cho quảng đường từ bờ sông xách nước đến đám cháy ngắn nhất.

Dù vậy, đến hôm nay là ngày thứ 20 viết bài này, mình lại nghĩ ra một lập luận mới, phản biện lập luận mà mình vừa nêu ở trên, và tác giả sẽ đúng, đó là khi có phương tiện di chuyển vì sẽ không bị ảnh hưởng bởi việc phải tự gánh nước (có nhưng không quá nhiều) - phương tiện là thứ trong bài toán không đề cập.

Câu chuyện tối ưu trong ngành phát triển phần mềm cũng muôn hình vạn trạng như vậy. Sẽ không có một phương án nào thực sự tối ưu cả, tất cả đều là trade-off, phải cân đối chi phí (thời gian, công sức), tính hiệu quả, và cả resource hiện tại (dự án có và cần gì, khả năng team members). Những quyết định này thường do chính dev experience mỗi người tạo nên. Và dev experience thường được ảnh hướng rất nhiều bởi loại hình công ty, kiểu dự án, team members mà developer gắn bó những năm đầu đi làm; có công ty sẽ rush task, có công ty lại cần một solution tốt dù tốn thời gian hơn một chút.

Sẽ không có một lời khuyên cụ thể nào cả. Dù vậy, để viết code chạy thì rất dễ, việc deal sao để solution mình chọn phù hợp nhất với resource đang có, với context hiện đang gặp mới là thứ cần tập. Vậy nên don’t be rush, đi chậm lại sẽ thấy được nhiều điều!
