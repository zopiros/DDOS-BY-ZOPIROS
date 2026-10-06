# DDOS-BY-ZOPIROS
A FULL DDOS SCRIPT MADE BY ZOPIROS 

🚀 Locust Max-RPS Chaos Test — v∞++++ PATCHED EDITION
you can copy paste all this to AI for better understanding
برای درک بهتر تمامی محتوای زیر را کپی کرده و به یک هوش مصنوعی داده تا به شما نحوه کار را توضیح دهد 

⚠️ هشدار / WARNING
این ابزار فقط باید روی سیستم‌هایی اجرا شود که مالک آن‌ها هستید یا اجازه کتبی صریح برای تست آن‌ها دارید. استفاده غیرمجاز از این اسکریپت می‌تواند منجر به پیگرد قانونی شود.
This tool must ONLY be run against systems you own or have explicit written permission to test. Unauthorized use may result in legal prosecution.
🇬🇧 English Documentation
Overview
The v∞++++ PATCHED EDITION is a battle-hardened, high-performance stress testing framework built on Locust. It extends standard load testing with advanced Chaos Engineering features designed to uncover hidden infrastructure weaknesses, WAF misconfigurations, database contention, and memory leaks.
This patched edition resolves critical bugs from previous versions including gzip content-length validation, race conditions, thundering herd feedback loops, and false-positive failures.
Key Features
⚡ FastHttpUser Engine: High-concurrency greenlet-based HTTP client
🎭 IP Spoofing: Randomized X-Forwarded-For headers to test rate limiters
💣 Header Bombing: Configurable oversized headers to stress proxy buffers
🔀 Method Chaos: Random HTTP method injection (GET/POST/PUT/DELETE/OPTIONS/PATCH)
✍️ Mutation Mix: Write-heavy traffic patterns for DB lock testing
📄 Deep Pagination: Massive offset parameters to expose query planner issues
⛈️ Thundering Herd: Reactive retry storms triggered by error rate thresholds
📈 Pulse Load Shape: Sawtooth traffic patterns for memory leak detection
🛡️ Strict Validation: Content-length, body size, and status code verification
🔧 Distributed Ready: Master/Worker architecture support with safe state management
Prerequisites
Python 3.8+
pip package manager
Installation 
# Clone or download the script
git clone <your-repo-url> && cd locust-chaos-test

# Create virtual environment
python3 -m venv venv
source venv/bin/activate        # Linux/Mac
# .\venv\Scripts\Activate       # Windows PowerShell

# Install dependencies
pip install locust
Quick Start
Web UI Mode (Interactive Dashboard)
locust -f locust-chaos.py --host https://your-target.com
# Open http://localhost:8089 in your browser
Headless Mode (CLI / CI-CD)
TARGET_USERS=1000 RUN_TIME=180 STEPS=6 \
locust -f locust-chaos.py --host https://your-target.com \
    --headless -u 1000 -r 50 -t 180s --html report.html --csv results
    Full Chaos Mode
رSPOOF_IP=true HEADER_BOMB=true METHOD_CHAOS=true \
MUTATION_PROB=0.1 DEEP_PAGINATION=true THUNDER_HERD=true \
PULSE_SHAPE=true TARGET_USERS=5000 RUN_TIME=300 \
locust -f locust-chaos.py --host https://your-target.com \
    --headless -u 5000 -r 200 -t 300s --html chaos-report.html
    Configuration Reference
Variable
Type
Default
Description
TARGET_USERS
int
1000
Maximum concurrent users
RUN_TIME
int
180
Test duration in seconds
SPAWN_RATE
int
100
Users spawned per second
ENDPOINTS
csv
/v1/search
Comma-separated endpoint list
SPOOF_IP
bool
false
Enable X-Forwarded-For randomization
HEADER_BOMB
bool
false
Enable oversized header injection
HEADER_BOMB_KB
int
16
Header bomb payload size in KB
METHOD_CHAOS
bool
false
Enable random HTTP method injection
MUTATION_PROB
float
0.0
Probability of write requests (0.0–1.0)
DEEP_PAGINATION
bool
false
Enable massive offset parameters
THUNDER_HERD
bool
false
Enable reactive retry storm
THUNDER_THRESHOLD
float
0.15
Error rate trigger for herd (0.01–1.0)
PULSE_SHAPE
bool
false
Enable sawtooth load pattern
STRICT_VALIDATION
bool
true
Enable deep response validation
AUTH_TOKEN
str
—
Bearer token for authentication
Distributed Execution
# Master node
locust -f locust-chaos.py --master --host https://target.com \
    --web-port=8089 --expect-workers=4

# Worker nodes (run on each worker machine)
locust -f locust-chaos.py --worker --master-host=<MASTER_IP> \
    --host https://target.comHardware Recommendations
Scale
Users
Recommended Specs
Light
1K–5K
4 vCPU, 8 GB RAM, Laptop OK
Medium
10K–30K
8–16 vCPU, 16–32 GB RAM, VPS
Heavy
50K+
Distributed cluster, 1 Gbps+ NIC
TroubleshootingTroubleshooting
Issue
Solution
Cannot assign requested address
Run sysctl -w net.ipv4.ip_local_port_range="1024 65535"
Too many open files
Run ulimit -n 65535
False 415 errors
Ensure Content-Type is set (auto-fixed in this version)
Thundering herd loop
Cooldown & rate-limit built-in; raise THUNDER_THRESHOLD if needed
Windows socket limits
Disable firewall temporarily or use WSL2/Linux
🇮🇷 مستندات فارسی
معرفی
نسخه v∞++++ PATCHED EDITION یک فریمورک تست استرس با عملکرد بالا و مقاوم‌سازی شده است که بر پایه Locust ساخته شده است. این نسخه قابلیت‌های پیشرفته مهندسی آشوب (Chaos Engineering) را به تست بار استاندارد اضافه می‌کند تا ضعف‌های پنهان زیرساخت، تنظیمات نادرست WAF، قفل‌های دیتابیس و نشت حافظه را آشکار سازد.
این نسخه اصلاح‌شده، باگ‌های بحرانی نسخه‌های قبلی از جمله اعتبارسنجی Content-Length در پاسخ‌های فشرده، Race Conditionها، حلقه‌های بازخورد Thundering Herd و خطاهای کاذب را برطرف کرده است.
ویژگی‌های کلیدی
⚡ موتور FastHttpUser: کلاینت HTTP مبتنی بر Greenlet با همزمانی بالا
🎭 جعل IP: هدرهای تصادفی X-Forwarded-For برای تست Rate Limiterها
💣 بمب هدر: تزریق هدرهای حجیم قابل تنظیم برای استرس تست بافر پراکسی‌ها
🔀 آشوب متد: تزریق تصادفی متدهای HTTP (GET/POST/PUT/DELETE/OPTIONS/PATCH)
✍️ ترکیب Mutation: الگوهای ترافیکی نوشتن‌محور برای تست قفل دیتابیس
📄 صفحه‌بندی عمیق: پارامترهای offset حجیم برای شناسایی مشکلات Query Planner
⛈️ گله رعدآسا: طوفان تلاش مجدد واکنشی که توسط آستانه نرخ خطا فعال می‌شود
📈 الگوی بار Pulse: الگوی ترافیک اره‌ای برای شناسایی نشت حافظه
🛡️ اعتبارسنجی سختگیرانه: بررسی Content-Length، اندازه بدنه و کد وضعیت
🔧 آماده توزیع: پشتیبانی از معماری Master/Worker با مدیریت امن State
پیش‌نیازها
پایتون ۳.۸ یا بالاتر
مدیر بسته pip
نصب و راه‌اندازی
bash

12345678910
شروع سریع
حالت رابط گرافیکی (داشبورد تعاملی)
bash

12
حالت بدون رابط گرافیکی (CLI / CI-CD)
bash

123
حالت آشوب کامل
bash

12345
مرجع پیکربندی
متغیر
نوع
پیش‌فرض
توضیحات
TARGET_USERS
عدد صحیح
1000
حداکثر کاربران همزمان
RUN_TIME
عدد صحیح
180
مدت زمان تست به ثانیه
SPAWN_RATE
عدد صحیح
100
تعداد کاربر تولیدشده در هر ثانیه
ENDPOINTS
لیست
/v1/search
لیست اندپوینت‌ها جداشده با کاما
SPOOF_IP
بولین
false
فعال‌سازی جعل X-Forwarded-For
HEADER_BOMB
بولین
false
فعال‌سازی تزریق هدر حجیم
HEADER_BOMB_KB
عدد صحیح
16
اندازه بمب هدر به کیلوبایت
METHOD_CHAOS
بولین
false
فعال‌سازی تزریق متد تصادفی HTTP
MUTATION_PROB
اعشاری
0.0
احتمال درخواست‌های نوشتن (۰.۰ تا ۱.۰)
DEEP_PAGINATION
بولین
false
فعال‌سازی پارامترهای offset حجیم
THUNDER_HERD
بولین
false
فعال‌سازی طوفان تلاش مجدد واکنشی
THUNDER_THRESHOLD
اعشاری
0.15
آستانه نرخ خطا برای فعال‌سازی گله (۰.۰۱ تا ۱.۰)
PULSE_SHAPE
بولین
false
فعال‌سازی الگوی بار اره‌ای
STRICT_VALIDATION
بولین
true
فعال‌سازی اعتبارسنجی عمیق پاسخ
AUTH_TOKEN
رشته
—
توکن Bearer برای احراز هویت
اجرای توزیع‌شده
bash

1234567
توصیه‌های سخت‌افزاری
مقیاس
تعداد کاربر
مشخصات پیشنهادی
سبک
۱K–5K
۴ هسته CPU، ۸ گیگ RAM، لپ‌تاپ کافی است
متوسط
۱۰K–30K
۸–۱۶ هسته CPU، ۱۶–۳۲ گیگ RAM، سرور مجازی
سنگین
۵۰K+
کلاستر توزیع‌شده، کارت شبکه ۱ Gbps+
عیب‌یابی
مشکل
راه‌حل
Cannot assign requested address
اجرای sysctl -w net.ipv4.ip_local_port_range="1024 65535"
Too many open files
اجرای ulimit -n 65535
خطای کاذب 415
اطمینان از تنظیم Content-Type (در این نسخه خودکار اصلاح شده)
حلقه بی‌پایان Thundering Herd
Cooldown و Rate-Limit داخلی؛ در صورت نیاز THUNDER_THRESHOLD را افزایش دهید
محدودیت سوکت ویندوز
غیرفعال کردن موقت فایروال یا استفاده از WSL2/لینوکس
License
MIT — Use responsibly and ethically. Always obtain proper authorization before testing.
