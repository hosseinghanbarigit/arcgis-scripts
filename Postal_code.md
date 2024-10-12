<div dir='RTL'>
  
# اصلاح کد پستی
این اسکریپت در جهت اصلاح و اعمال ویرایشات موردنظر روی کدپستی پلاک هایی است که ممکن است ناقص و یا اشتباه وارد شده باشند.

کافی است این قطعه کد را درون `Attribute Table` فیلد موردنظر در جدول وارد کنید.

> **توجه:**
>
> حتماً توجه داشته باشید که گزینه `Python` برای زبان اسکریپت در پنجره Attribute Table انتخاب شده باشد.

اسکریپت زیر را کپی و جانمایی کنید:


```python
import re


def extract_numbers(value):
    # پیدا کردن تمام اعداد درون رشته
    numbers = re.findall(r"\d+", value)
    return numbers


def add_prefix(value):
    # اگر عدد زیر 3 رقم باشد، تغییری نکند
    if len(value) < 3:
        return value
    elif value.startswith("01"):
        return None
    elif value.startswith("88319"):
        return value
    else:
        return "88319" + value


def process_field(value):
    numbers = extract_numbers(value)
    # پردازش اعداد و اعمال پیش‌وند
    processed_numbers = [add_prefix(num) for num in numbers if add_prefix(num)]
    return "-".join(processed_numbers)
```
</div>
