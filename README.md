What
----

Hosts file which is used for improving IPv6 access speed to Google, YouTube, 
Facebook, Wikipedia, etc. in Mainland China.

|   \   |                                                                    |
| ----- | ------------------------------------------------------------------ |
| Hosts | https://raw.githubusercontent.com/lennylxx/ipv6-hosts/master/hosts |
| Wiki  | https://github.com/lennylxx/ipv6-hosts/wiki                        |
| Info  | [1e100 servers deployment geoinfo], [SN-domain servers list]       |

* You may need [HTTPS Everywhere] to secure your transmission.
* [How to decode Google SN domains]
* How to [Do It Yourself]

Scripts
-------

[update_hosts.py]

```
usage: update_hosts [OPTIONS] FILE
A simple multi-threading tool used for updating hosts file.

Options:
  -h, --help             show this help message and exit
  -s DNS                 set another dns server, default: 2001:4860:4860::8844
  -o OUT_FILE            output file, default: inputfilename.out
  -t QUERY_TYPE          dig command query type, default: aaaa
  -c, --cname            write canonical name into hosts file
  -n THREAD_NUM          set the number of worker threads, default: 10
```

[merge_snippets.sh]

```
usage: ./merge_snippets.sh new_hosts
```

Some Public DNS Servers
-----------------------

|          |           USA          |           USA          |
| -------- | ---------------------- | ---------------------- |
| Hostname | **ordns.he.net**       | **tserv1.lax1.he.net** |
| IPv6     | 2001:470:20::2         | 2001:470:0:9d::2       | 
| IPv4     | 74.82.42.42            | 66.220.18.42           |
| ISP      | Hurricane Electric Inc.| Hurricane Electric Inc.|
| City     | Anycast                | Los Angeles            |


|          |      Hong Kong         |       Japan        |
| -------- | ---------------------- | ------------------ |
| Hostname | **dns.hutchcity.com**  | **ns01.miinet.jp** |
| IPv4     | 202.45.84.58           | 203.112.2.4        |
| ISP      | Hutchison Whampoa Ltd. | UCOM Corporation   |
| City     | Hong Kong              | Tokyo              |

More public DNS servers please refer to http://public-dns.info

Privacy
-------

* The hosts file just redirects domain to its official IPs. You can check them on any other public DNS servers.
* There is no absolute privacy on the Internet. Learn to protect yourself.
* Act smart.

License
-------

Code of this project is licensed under the [MIT license](LICENSE).  
Content of this project (including hosts files, wiki, and Google sheets) is licensed under [![CC Image]][CC BY-NC-SA 3.0].



#!/usr/bin/python

# coding:utf-8

from PIL import Image, ImageDraw, ImageFont, ImageFilter

import random
img = Image.open("1.jpg")

##图像处理##
#转换为RGB图像
img = img.convert("RGB")              

#经过PIL自带filter处理
imgfilted_b = img.filter(ImageFilter.BLUR)
imgfilted_c = img.filter(ImageFilter.CONTOUR)
imgfilted_ee = img.filter(ImageFilter.EDGE_ENHANCE)
imgfilted_ee_m = img.filter(ImageFilter.EDGE_ENHANCE_MORE)
imgfilted_em = img.filter(ImageFilter.EMBOSS)                    
imgfilted_fe = img.filter(ImageFilter.FIND_EDGES)                                                
imgfilted_sm = img.filter(ImageFilter.SMOOTH)
imgfilted_sm_m = img.filter(ImageFilter.SMOOTH_MORE)
imgfilted_sh = img.filter(ImageFilter.SHARPEN)
imgfilted_d = img.filter(ImageFilter.DETAIL)

##组合使用filter
group_imgfilted = img.filter(ImageFilter.CONTOUR)
group_imgfilted = group_imgfilted.filter(ImageFilter.SMOOTH_MORE)

##图像保存##
imgfilted_b.save("1b.jpg")
imgfilted_c.save("1c.jpg")
imgfilted_ee.save("1ee.jpg")
imgfilted_ee_m.save("1eem.jpg")
imgfilted_em.save("1em.jpg")
imgfilted_fe.save("1fe.jpg")                                
imgfilted_sm.save("1sm.jpg")
imgfilted_sm_m.save("1smm.jpg")
imgfilted_sh.save("1sh.jpg")
imgfilted_d.save("1d.jpg")
group_imgfilted.save("1group.jpg")

##图像显示##
imgfilted_b.show()
imgfilted_c.show()
imgfilted_ee.show()
imgfilted_ee_m.show()
imgfilted_em.show()
imgfilted_fe.show()                                
imgfilted_sm.show()
imgfilted_sm_m.show()
imgfilted_sh.show()
imgfilted_d.show()
group_imgfilted.show()
#end

[merge_snippets.sh]: merge_snippets.sh
[update_hosts.py]: update_hosts.py
[1e100 servers deployment geoinfo]: https://docs.google.com/spreadsheets/d/1a5HI0lkc1TycJdwJnCVDVd3x6_gemI3CQhNHhdsVmP8
[SN-domain servers list]: https://docs.google.com/spreadsheets/d/14gT1GV1IE0oYCq-1Dy747_5FWNxL26R-9T5htJ485dY
[HTTPS Everywhere]: https://www.eff.org/https-everywhere
[How to decode Google SN domains]: https://github.com/lennylxx/ipv6-hosts/wiki/sn-domains
[Do It Yourself]: https://github.com/lennylxx/ipv6-hosts/wiki/Do-It-Yourself
[CC Image]: https://licensebuttons.net/l/by-nc-sa/3.0/88x31.png
[CC BY-NC-SA 3.0]: https://creativecommons.org/licenses/by-nc-sa/3.0/
