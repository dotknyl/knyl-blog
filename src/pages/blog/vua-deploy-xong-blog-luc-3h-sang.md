---
layout: "../../layouts/BlogPost.astro"
title: "Vừa deploy xong blog lúc 3h sáng"
description: "Dạo này làm microservices bug đấm sấp mặt, mà cũng gặp được nhiều thứ hay ho, vậy nên mình dành ra 2 ngày cuối tuần code cái blog để giải trí sau những giờ code căng thẳng…"
pubDate: "May 30, 2022 2:49 AM"
tags: ["discuss", "career"]
---

Dạo này làm microservices bug đấm sấp mặt, mà cũng gặp được nhiều thứ hay ho, vậy nên mình dành ra 2 ngày cuối tuần code cái blog để giải trí sau những giờ code căng thẳng =))

Set up mọi thứ cũng khá đơn giản:

- Load balancer và API mình dùng .NET Core (dễ đoán).
- Frontend mình dùng Angular, Tailwindcss và Scully, tuy nhiên mình chưa có thời gian build scully và config article routes cho scully.
- Ngay từ đầu, mình khá băn khoăn giữa 2 phương án: tự host database hay dùng Notion.

* Tự host database thì khá nhanh, tuy nhiên, lại phải mất công setup editor để post bài, hay tự viết raw HTML rồi insert thẳng database? =))

* Dùng Notion thì không cần setup gì luôn, editor thì quá gấu rồi, api có sẵn. Nhưng sẽ khó săn ở chỗ render Notion Json thành Raw HTML. Phần này mình mới render đơn giản chứ chưa thực sự hài lòng lắm, hi vọng có thời gian enhance thêm.

Làm api, frontend xong xuôi, setup load balancer chạy ngon lành, cứ tưởng là ngon rồi :)) Nhưng cuộc sống mà, đâu có dễ =))

Mình dùng Systemd trên Linux để chạy apps as services (api, blogs, và tất nhiên là load balancer để điều phối request). Tuy nhiên, lúc deploy xong thì mình gặp lỗi Connection refused. Mất 2 tiếng xác định lỗi, khi chạy systemd thì service get content path sai, dẫn đến service chạy sai settings. Định đi ngủ mai tính tiếp, nhưng mà cay quá, với sợ mai lại bị k8s đấm tiếp, nên gắng kiếm cách fix luôn. Set Content root path trong Startup mãi không được, cuối cùng thì kiếm được cách set trong systemd service.

Deploy xong chạy ngon lành, lên giường nằm rồi mà vẫn hứng quá, lại lấy Notion trên điện thoại ra viết bài này. Lan man xong thì đi ngủ thôi 🤣
