---
refcn: chapter_02/protocols/freedom
refen: configuration/protocols/freedom
---

# Freedom

* نام: `آزادی`45.77.33.69
* نوع: خروجی

«آزادی» یک پروتکل برای ارتباطات خروجی است. او تمام اتصال TCP یا UDP را به مقاصد خود منتقل می کند. این خروجی زمانی استفاده می شود که می خواهید ترافیک را به مقصد واقعی خود ارسال کنید.

## ConfigurationObject

```javascript
{
  "domainStrategy": "AsIs",
  "redirect": "127.0.0.1:3366",
  "userLevel": 0
}
```

> `domainStrategy`: "AsIs" | "UseIP"

استراتژی برای حل و فصل نام دامنه. گزینه ها عبارتند از:

* `"AsIs"`: مقدار پیش فرض. تعیین نام دامنه توسط سیستم
* `"UseIP"`: استفاده از [DNS داخلی](../dns.md) برای وضوح نام دامنه.
* `"UseIPv4"`: فقط آدرس‌های IPv4, پس از حل شدن توسط DNS داخلی.
* `"UseIPv6"`: فقط آدرس‌های IPv6 , پس از حل شدن توسط DNS داخلی. 

(V2Ray 4.6+) In `UseIP` mode, when `sendThrough` is specified in [OutboundObject](../overview.md#outboundobject), Freedom will automatically choose between IPv4 and IPv6 address for destination based on `sendThrough` settings.

(V2Ray 4.7+) اگر نشانی`sendThrough` با `"UseIPv4"` یا `"UseIPv6"` همپوشانی داشته باشد, «آزادی» در تماس با ارتباطات خروجی شکست میخورد.

> `redirect`: address_port

تمامی ارتباطات را به این نشانی منتقل میکند، در قالب `"127.0.0.1:80"` یا `":1234"`.

* وقتی آدرس خالی است، به عنوان مثال `": 443"`، «آزادی» از آدرس اصلی اصلی استفاده می کند.
* هنگامی که پورت `0`، به عنوان مثال `"v2ray.com:0"`، آزادی از پورت اصلی استفاده می‌کند.

> `userLevel`: number

سطح کاربر. تمامی ارتباطات این سطح را به اشتراک می‌‌گذارند.