# مقطع

<img height="108px" src="https://raw.githubusercontent.com/thomiceli/opengist/master/public/img/opengist.svg" alt="مقطع" align="right" />

مقطع هو مكان لوضع مقاطع صغيرة من الكود البرمجي **مستضاف ذاتيًا** و**مدعوم بـ Git**. يتم تخزين جميع المقاطع في مستودع Git ويمكن
قراءتها و/أو تعديلها باستخدام أوامر Git القياسية أو عبر واجهة الويب.
وهو مشابه لـ [GitHub Gist](https://gist.github.com/)، لكنه مفتوح المصدر ويمكن استضافته ذاتيًا.

[الصفحة الرئيسية](https://opengist.io) • [التوثيق](https://opengist.io/docs) • [ديسكورد](https://discord.gg/9Pm3X5scZT) • [نسخة تجريبية](https://demo.opengist.io)


![GitHub release (latest SemVer)](https://img.shields.io/github/v/release/thomiceli/opengist?sort=semver)
![License](https://img.shields.io/github/license/thomiceli/opengist?color=blue)
[![Go CI](https://github.com/thomiceli/opengist/actions/workflows/go.yml/badge.svg)](https://github.com/thomiceli/opengist/actions/workflows/go.yml)
[![Go Report Card](https://goreportcard.com/badge/github.com/thomiceli/opengist)](https://goreportcard.com/report/github.com/thomiceli/opengist)
[![Translate](https://tr.opengist.io/widget/_/svg-badge.svg)](https://tr.opengist.io/projects/_/opengist/)

## الميزات

* إنشاء مقاطع عامة أو غير مدرجة أو خاصة
* [Init](/docs/usage/init-via-git.md) / Clone / Pull / Push للمقاطع **عبر Git** باستخدام HTTP أو SSH
* تلوين الصياغة؛ دعم Markdown وCSV
* البحث في كود المقاطع؛ وتصفح مقاطع المستخدمين والإعجابات والتفريعات
* إضافة مواضيع للمقاطع
* تضمين المقاطع في مواقع أخرى
* سجل المراجعات
* الإعجاب بالمقاطع / تفريعها
* تنزيل الملفات الخام أو كأرشيف ZIP
* تسجيل الدخول عبر OAuth2 مع GitHub وGitLab وGitea وOpenID Connect
* تقييد أو إلغاء تقييد ظهور المقاطع للمستخدمين المجهولين
* دعم Docker / Helm Chart
* [المزيد...](/docs/introduction.md#features)

## البدء السريع

### باستخدام Docker

صور Docker [images](https://github.com/thomiceli/opengist/pkgs/container/opengist) متاحة لكل إصدار:

```shell
docker pull ghcr.io/thomiceli/opengist:1.12
```

يمكن استخدامه عبر ملف `docker-compose.yml`:

1. أنشئ ملف `docker-compose.yml` بالمحتوى التالي
2. شغّل `docker compose up -d`
3. أصبح مقطع يعمل الآن على المنفذ 6157، ويمكنك التصفح عبر http://localhost:6157

```yml
services:
  opengist:
    image: ghcr.io/thomiceli/opengist:1.12
    container_name: opengist
    restart: unless-stopped
    ports:
      - "6157:6157" # منفذ HTTP
      - "2222:2222" # منفذ SSH، ويمكن حذفه إذا لم تستخدم SSH
    volumes:
      - "$HOME/.opengist:/opengist"
```

يمكنك تحديد المستخدم/المجموعة التي يجب أن تشغّل الحاوية وتمتلك الملفات عبر ضبط متغيري البيئة `UID` و`GID`:

```yml
services:
  opengist:
    # ...
    environment:
      UID: 1001
      GID: 1001
```

### عبر الملف التنفيذي

نزّل الأرشيف المناسب لنظامك من صفحة الإصدارات من [هنا](https://github.com/thomiceli/opengist/releases/latest)، ثم فك الضغط.

```shell
# مثال لنظام linux amd64
wget https://github.com/thomiceli/opengist/releases/download/v1.12.1/opengist1.12.1-linux-amd64.tar.gz

tar xzvf opengist1.12.1-linux-amd64.tar.gz
cd opengist
chmod +x opengist
./opengist # مع أو بدون `--config config.yml`
```

أصبح مقطع يعمل الآن على المنفذ 6157، ويمكنك التصفح عبر http://localhost:6157

### من المصدر

المتطلبات: [Git](https://git-scm.com/downloads) (2.28+)، [Go](https://go.dev/doc/install) (1.25+)، [Node.js](https://nodejs.org/en/download/) (16+)، [Make](https://linux.die.net/man/1/make) (اختياري لكنه أسهل)

```shell
git clone https://github.com/thomiceli/opengist
cd opengist
make
./opengist
```

أصبح مقطع يعمل الآن على المنفذ 6157، ويمكنك التصفح عبر http://localhost:6157

---

لإنشاء وتشغيل بيئة تطوير، راجع [run-development.md](/docs/contributing/development.md).

## التوثيق

التوثيق متاح على [https://opengist.io/](https://opengist.io/) أو داخل مجلد [/docs](/docs).


## الرخصة

مقطع مرخّص تحت [AGPL-3.0 license](/LICENSE).
