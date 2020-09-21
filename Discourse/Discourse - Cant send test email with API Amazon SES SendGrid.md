Có thể nhiều bạn khi cài đặt setup email dùng API từ SendGrid, Amazon SES để gửi email mặc định trên thì hệ thống lại không gửi được, mặc dù các cấu hình đã đúng nhưng vẫn không gửi được email, bạn chú ý check như sau nhé:

Discourse Can’t send test email with API Amazon SES, SendGrid …


Tìm và edit file config 1 chút nhé
```
cd /var/discourse
nano containers/app.yml
```
Tìm dòng cấu hình SMTP bỏ dấu # và sửa thành

```
DISCOURSE_SMTP_ENABLE_START_TLS: true           # (optional, default true)
```
Kéo xuống cuối tìm dòng này, và sửa y chang như vậy nhé (chú ý là Email phải đúng với Email đã Verify trong SES hoặc Sendgrid

```
- exec: rails r "SiteSetting.notification_email='news @ gafaba.com'"
```
Sau khi Edit xong nhớ lưu và Build lại APP bằng command sau nhé

```
./launcher rebuild app
```
Và cuối cùng là thử nhé…