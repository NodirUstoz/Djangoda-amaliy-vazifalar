# DJANGO 1-AMALIY DARS BO'YICHA VAZIFALAR

## Umumiy ma'lumot

**Dars mavzusi:** Django asoslari - Project, App, Model, View, URL, Template, Admin Panel

**Vazifalar soni:** 10 ta (har bir talabaga alohida)

**Topshirish muddati:** 1 soat

**Baholash:** 100 ball

---

# UMUMIY TALABLAR (BARCHA TALABALAR UCHUN)

Har bir talaba o'z vazifasini bajarishda quyidagi umumiy qoidalarga rioya qilishi shart:

## Texnik talablar:
1. Virtual environment yaratish va faollashtirish
2. Django loyiha strukturasini to'g'ri tashkil qilish
3. Kamida 2 ta model yaratish (bir-biriga bog'langan)
4. Admin panelni to'liq sozlash
5. Kamida 5 ta view funksiyasi yaratish
6. URL marshrutlarini to'g'ri sozlash
7. Base template va kamida 4 ta sahifa yaratish
8. Template inheritance (meros) ishlatish
9. Kamida 15 ta test ma'lumot kiritish
10. Kod izohlar (comments) bilan yozilgan bo'lishi kerak

## Papka strukturasi:
```
loyiha_nomi/
├── config/
│   ├── __init__.py
│   ├── settings.py
│   ├── urls.py
│   └── wsgi.py
├── app_nomi/
│   ├── migrations/
│   ├── __init__.py
│   ├── admin.py
│   ├── apps.py
│   ├── models.py
│   ├── urls.py
│   ├── views.py
│   └── tests.py
├── templates/
│   ├── base.html
│   └── app_nomi/
│       ├── home.html
│       ├── list.html
│       ├── detail.html
│       └── ...
├── static/
│   └── css/
│       └── style.css
├── venv/
├── manage.py
├── db.sqlite3
└── requirements.txt
```

## Baholash mezonlari (barcha uchun bir xil):

| Mezon | Ball |
|-------|------|
| Virtual environment va Django o'rnatish | 10 |
| Modellar to'g'ri yaratilgan va bog'langan | 15 |
| Admin panel professional sozlangan | 10 |
| View funksiyalari to'g'ri ishlaydi | 15 |
| URL marshrutlari to'g'ri | 10 |
| Base template professional | 10 |
| Barcha sahifalar to'g'ri ishlaydi | 15 |
| Test ma'lumotlar kiritilgan (15+ ta) | 5 |
| Kod toza va izohlangan | 5 |
| Qo'shimcha funksiyalar (filter, search) | 5 |
| **Jami** | **100** |

---

# VAZIFALAR

---

## 1-TALABA: KITOBLAR KUTUBXONASI

### Loyiha nomi: `KitoblarDunyosi`

### Maqsad:
Kitoblar kutubxonasi web ilovasini yaratish. Foydalanuvchilar kitoblarni ko'rishi, janr bo'yicha filterlashi va kitob haqida to'liq ma'lumot olishi mumkin bo'ladi.

### Yaratilishi kerak bo'lgan modellar:

**1. Book (Kitob) modeli:**
- `title` — Kitob nomi (CharField, max 200 belgi)
- `author` — Muallif ismi (CharField, max 100 belgi)
- `description` — Kitob haqida batafsil ma'lumot (TextField)
- `pages` — Sahifalar soni (IntegerField)
- `published_year` — Nashr yili (IntegerField)
- `genre` — Janr (CharField, max 50 belgi) — masalan: "Roman", "Fantastika", "Tarixiy"
- `language` — Til (CharField, max 30 belgi)
- `isbn` — ISBN raqami (CharField, unique=True)
- `is_available` — Mavjudligi (BooleanField, default=True)
- `created_at` — Qo'shilgan vaqt (DateTimeField, auto_now_add=True)

**2. Author (Muallif) modeli (qo'shimcha):**
- `full_name` — To'liq ismi
- `birth_year` — Tug'ilgan yili
- `country` — Mamlakati
- `biography` — Biografiya

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (so'nggi qo'shilgan 6 ta kitob)
2. `book_list` — Barcha kitoblar ro'yxati
3. `book_detail` — Bitta kitob haqida to'liq ma'lumot
4. `books_by_genre` — Janr bo'yicha kitoblar (dinamik URL)
5. `search` — Kitob qidirish (GET parametri orqali)

### Yaratilishi kerak bo'lgan sahifalar:
1. `base.html` — Asosiy shablon (header, nav, footer)
2. `home.html` — Bosh sahifa
3. `book_list.html` — Kitoblar ro'yxati
4. `book_detail.html` — Kitob detali
5. `search.html` — Qidiruv natijalari

### URL manzillar:
- `/` — Bosh sahifa
- `/kitoblar/` — Barcha kitoblar
- `/kitob/<int:pk>/` — Kitob detali
- `/janr/<str:genre>/` — Janr bo'yicha
- `/qidirish/?q=...` — Qidiruv

### Admin panel talablari:
- Kitoblarni qo'shish, o'chirish, tahrirlash
- Ro'yxatda ko'rsatish: nomi, muallif, janr, yil, mavjudligi
- Qidiruv: nom va muallif bo'yicha
- Filter: janr va yil bo'yicha

### Test ma'lumotlar (kamida):
- 5 xil janrdagi 15 ta kitob
- O'zbek va jahon adabiyotidan namunalar

### Dizayn talablari:
- Kutubxona uslubida (klassik, kitob ranglari)
- Kitob kartochkalari grid ko'rinishda
- Responsive dizayn

---

## 2-TALABA: RESTORAN MENYUSI

### Loyiha nomi: `MazzaliTaomlar`

### Maqsad:
Restoran menyusi web ilovasini yaratish. Foydalanuvchilar taomlarni kategoriya bo'yicha ko'rishi, narxlarni bilishi va taom tarkibini o'qishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Category (Kategoriya) modeli:**
- `name` — Kategoriya nomi (masalan: "Salatlar", "Sho'rvalar", "Asosiy taomlar")
- `description` — Tavsif
- `icon` — Emoji yoki icon nomi
- `order` — Tartib raqami (menuda ko'rsatish uchun)

**2. Dish (Taom) modeli:**
- `name` — Taom nomi
- `category` — Kategoriya (ForeignKey)
- `description` — Tavsif
- `ingredients` — Tarkibi
- `price` — Narxi (IntegerField, so'mda)
- `cooking_time` — Tayyorlanish vaqti (daqiqada)
- `calories` — Kaloriya
- `is_spicy` — Achchiq yoki yo'q (BooleanField)
- `is_vegetarian` — Vegetarian taom (BooleanField)
- `is_available` — Mavjud (BooleanField)
- `is_popular` — Mashhur taom (BooleanField)

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (mashhur taomlar va kategoriyalar)
2. `full_menu` — To'liq menyu (barcha kategoriyalar bilan)
3. `category_dishes` — Kategoriya bo'yicha taomlar
4. `dish_detail` — Taom haqida to'liq ma'lumot
5. `search` — Taom qidirish

### URL manzillar:
- `/` — Bosh sahifa
- `/menyu/` — To'liq menyu
- `/kategoriya/<int:pk>/` — Kategoriya taomlari
- `/taom/<int:pk>/` — Taom detali
- `/qidirish/` — Qidiruv

### Admin panel talablari:
- Kategoriya va taomlarni boshqarish
- Taomlar ro'yxatida: nomi, kategoriya, narx, mavjudligi
- `is_available` va `is_popular` ni ro'yxatdan tahrirlash (list_editable)
- Kategoriya bo'yicha filter

### Test ma'lumotlar:
- 5 ta kategoriya (Salatlar, Sho'rvalar, Asosiy taomlar, Ichimliklar, Shirinliklar)
- Har bir kategoriyada 3-4 ta taom (jami 15-20 ta)
- O'zbek milliy taomlari va Yevropa taomlari

### Dizayn talablari:
- Restoran uslubida (issiq ranglar, qora va qizil)
- Taom kartochkalarida narx va vaqt ko'rsatilsin
- Mashhur taomlar badge bilan belgilansin

---

## 3-TALABA: KINO AFISHA

### Loyiha nomi: `KinoOlami`

### Maqsad:
Kino afisha web ilovasini yaratish. Foydalanuvchilar hozirda namoyish etilayotgan filmlarni ko'rishi, janr bo'yicha filterlashi va film haqida ma'lumot olishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Genre (Janr) modeli:**
- `name` — Janr nomi
- `slug` — URL uchun (SlugField)

**2. Movie (Film) modeli:**
- `title` — Film nomi
- `original_title` — Original nomi (ingliz tilida)
- `genre` — Janr (ForeignKey)
- `description` — Tavsif
- `director` — Rejissyor
- `actors` — Aktyorlar (TextField, vergul bilan ajratilgan)
- `country` — Mamlakat
- `year` — Yil
- `duration` — Davomiyligi (daqiqada)
- `age_rating` — Yosh chegarasi (choices: 0+, 6+, 12+, 16+, 18+)
- `rating` — Reyting (DecimalField, 0.0 dan 10.0 gacha)
- `is_showing` — Hozir namoyishda (BooleanField)
- `is_premiere` — Premyera (BooleanField)
- `release_date` — Chiqish sanasi (DateField)

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (premyeralar va mashhur filmlar)
2. `movie_list` — Barcha filmlar (filter va sort bilan)
3. `movie_detail` — Film haqida to'liq ma'lumot
4. `genre_movies` — Janr bo'yicha filmlar
5. `premieres` — Faqat premyeralar
6. `search` — Film qidirish

### URL manzillar:
- `/` — Bosh sahifa
- `/filmlar/` — Barcha filmlar
- `/film/<int:pk>/` — Film detali
- `/janr/<slug:slug>/` — Janr bo'yicha
- `/premyeralar/` — Premyeralar
- `/qidirish/` — Qidiruv

### Admin panel talablari:
- Film va janrlarni boshqarish
- `is_showing` va `is_premiere` ni ro'yxatdan tahrirlash
- Janr va yil bo'yicha filter
- Sana bo'yicha hierarchy (date_hierarchy)

### Test ma'lumotlar:
- 6-8 ta janr
- 15-20 ta film (turli janrlardan)
- Ba'zilari premyera, ba'zilari oddiy namoyishda

### Dizayn talablari:
- Netflix/Kinopoisk uslubida (qora fon, qizil aksentlar)
- Film kartochkalarida reyting va yosh chegarasi ko'rsatilsin
- Premyera badge bilan belgilansin

---

## 4-TALABA: YANGILIKLAR PORTALI

### Loyiha nomi: `KunlikXabar`

### Maqsad:
Yangiliklar portali yaratish. Foydalanuvchilar turli kategoriyalardagi yangiliklarni o'qishi, eng so'nggi va mashhur yangiliklar bilan tanishishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Category (Kategoriya) modeli:**
- `name` — Kategoriya nomi (Siyosat, Iqtisodiyot, Sport, Texnologiya, Madaniyat)
- `slug` — URL slug
- `color` — Rang kodi (hex formatda, badge uchun)

**2. Article (Maqola) modeli:**
- `title` — Sarlavha
- `slug` — URL slug (unique)
- `category` — Kategoriya (ForeignKey)
- `summary` — Qisqa mazmuni (300-500 belgi)
- `content` — To'liq matni (TextField)
- `author` — Muallif ismi
- `source` — Manba (ixtiyoriy)
- `views_count` — Ko'rishlar soni (IntegerField, default=0)
- `is_featured` — Asosiy yangilik (BooleanField)
- `is_breaking` — Tezkor xabar (BooleanField)
- `status` — Holat (choices: draft, published)
- `published_at` — Nashr vaqti (DateTimeField)
- `created_at` — Yaratilgan vaqt

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (asosiy yangilik, tezkor xabarlar, so'nggi yangiliklar)
2. `article_list` — Barcha yangiliklar
3. `article_detail` — Maqola to'liq matni (views_count oshirish bilan)
4. `category_articles` — Kategoriya bo'yicha
5. `popular` — Eng ko'p o'qilganlar
6. `search` — Qidiruv

### URL manzillar:
- `/` — Bosh sahifa
- `/yangiliklar/` — Barcha yangiliklar
- `/maqola/<slug:slug>/` — Maqola detali
- `/kategoriya/<slug:slug>/` — Kategoriya yangiliklari
- `/mashhur/` — Ko'p o'qilganlar
- `/qidirish/` — Qidiruv

### Admin panel talablari:
- Maqolalarni boshqarish
- Status, is_featured, is_breaking ni ro'yxatdan tahrirlash
- Kategoriya va sana bo'yicha filter
- Fieldsets bilan guruhlab chiqarish

### Test ma'lumotlar:
- 5-6 ta kategoriya
- Har bir kategoriyada 3-4 ta maqola
- Ba'zilari featured, ba'zilari breaking news

### Dizayn talablari:
- Gazeta/news portal uslubida
- Tezkor xabarlar alohida ajratilgan (qizil banner)
- Ko'rishlar soni ko'rsatilsin

---

## 5-TALABA: MEHMONXONA BRONLASH

### Loyiha nomi: `YaxshiDam`

### Maqsad:
Mehmonxona xonalari haqida ma'lumot beruvchi web ilova yaratish. Foydalanuvchilar xona turlari, narxlar va qulayliklar bilan tanishishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Amenity (Qulaylik) modeli:**
- `name` — Qulaylik nomi (Wi-Fi, Konditsioner, TV, Mini-bar, Balkon)
- `icon` — Emoji

**2. RoomType (Xona turi) modeli:**
- `name` — Xona turi nomi (Standart, Deluxe, Suite, Family)
- `slug` — URL slug
- `description` — Tavsif
- `price_per_night` — Bir kechalik narx (IntegerField)
- `max_guests` — Maksimal mehmonlar soni
- `bed_type` — Karavot turi (1 kishilik, 2 kishilik, king-size)
- `size` — Xona hajmi (kv.m)
- `amenities` — Qulayliklar (ManyToManyField)

**3. Room (Xona) modeli:**
- `room_number` — Xona raqami (unique)
- `room_type` — Xona turi (ForeignKey)
- `floor` — Qavat
- `status` — Holat (choices: available, occupied, maintenance)
- `has_view` — Manzarali (BooleanField)

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (statistika, xona turlari)
2. `room_types_list` — Barcha xona turlari
3. `room_type_detail` — Xona turi haqida batafsil
4. `available_rooms` — Bo'sh xonalar
5. `amenities` — Qulayliklar ro'yxati
6. `about` — Mehmonxona haqida

### URL manzillar:
- `/` — Bosh sahifa
- `/xonalar/` — Xona turlari
- `/xona/<slug:slug>/` — Xona turi detali
- `/bosh-xonalar/` — Bo'sh xonalar
- `/qulayliklar/` — Qulayliklar
- `/haqimizda/` — Mehmonxona haqida

### Admin panel talablari:
- Xona turlari va xonalarni boshqarish
- Xonalar holatini ro'yxatdan o'zgartirish
- Filter: xona turi, qavat, holat bo'yicha
- ManyToMany uchun filter_horizontal

### Test ma'lumotlar:
- 8-10 ta qulaylik
- 4-5 ta xona turi
- Har bir turdan 3-4 ta xona (jami 15-20)

### Dizayn talablari:
- Mehmonxona uslubida (elegant, oq va ko'm ranglar)
- Narxlar va qulayliklar aniq ko'rsatilsin
- Bo'sh/band xonalar rangi bilan ajratilsin

---

## 6-TALABA: ONLINE KURSLAR

### Loyiha nomi: `BilimZone`

### Maqsad:
Online kurslar platformasi yaratish. Foydalanuvchilar kurslarni ko'rishi, o'qituvchilar haqida ma'lumot olishi va kurs tarkibini ko'rishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Category (Kategoriya) modeli:**
- `name` — Kategoriya nomi (Dasturlash, Dizayn, Marketing, Tillar)
- `slug` — URL slug
- `icon` — Emoji
- `description` — Tavsif

**2. Instructor (O'qituvchi) modeli:**
- `full_name` — To'liq ismi
- `title` — Lavozimi/mutaxassisligi
- `bio` — Biografiya
- `experience_years` — Tajriba (yil)
- `email` — Email
- `students_count` — O'quvchilar soni

**3. Course (Kurs) modeli:**
- `title` — Kurs nomi
- `slug` — URL slug
- `category` — Kategoriya (ForeignKey)
- `instructor` — O'qituvchi (ForeignKey)
- `description` — Tavsif
- `level` — Daraja (choices: beginner, intermediate, advanced)
- `price` — Narx (0 = bepul)
- `duration_hours` — Davomiyligi (soat)
- `lessons_count` — Darslar soni
- `students_enrolled` — Yozilganlar soni
- `rating` — Reyting (DecimalField)
- `is_featured` — Tavsiya etilgan
- `is_published` — Nashr qilingan

**4. Lesson (Dars) modeli:**
- `course` — Kurs (ForeignKey)
- `title` — Dars nomi
- `order` — Tartib raqami
- `duration_minutes` — Davomiyligi (daqiqa)
- `is_free` — Bepul ko'rish mumkin

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (featured kurslar, statistika)
2. `course_list` — Barcha kurslar (filter bilan)
3. `course_detail` — Kurs haqida va darslar ro'yxati
4. `category_courses` — Kategoriya kurslari
5. `instructor_profile` — O'qituvchi profili va kurslari
6. `search` — Qidiruv

### URL manzillar:
- `/` — Bosh sahifa
- `/kurslar/` — Barcha kurslar
- `/kurs/<slug:slug>/` — Kurs detali
- `/kategoriya/<slug:slug>/` — Kategoriya kurslari
- `/oqituvchi/<int:pk>/` — O'qituvchi profili
- `/qidirish/` — Qidiruv

### Test ma'lumotlar:
- 4-5 ta kategoriya
- 3-4 ta o'qituvchi
- 10-15 ta kurs
- Har bir kursda 5-8 ta dars

### Dizayn talablari:
- Udemy/Coursera uslubida
- Daraja badgelari rangli bo'lsin
- Reyting yulduzlar bilan ko'rsatilsin

---

## 7-TALABA: ELEKTRON DO'KON

### Loyiha nomi: `OnlineShop`

### Maqsad:
Elektron do'kon katalogi yaratish. Foydalanuvchilar mahsulotlarni ko'rishi, kategoriya bo'yicha filterlashi va mahsulot haqida ma'lumot olishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Category (Kategoriya) modeli:**
- `name` — Kategoriya nomi
- `slug` — URL slug
- `parent` — Ota kategoriya (ForeignKey to self, null=True) — sub-kategoriyalar uchun
- `description` — Tavsif

**2. Brand (Brend) modeli:**
- `name` — Brend nomi
- `slug` — URL slug
- `country` — Mamlakat
- `description` — Tavsif

**3. Product (Mahsulot) modeli:**
- `name` — Mahsulot nomi
- `slug` — URL slug
- `category` — Kategoriya (ForeignKey)
- `brand` — Brend (ForeignKey)
- `description` — Tavsif
- `price` — Narx
- `old_price` — Eski narx (chegirma uchun, null=True)
- `quantity` — Ombordagi soni
- `sku` — Artikul (unique)
- `is_available` — Mavjud
- `is_featured` — Tavsiya etilgan
- `is_new` — Yangi mahsulot
- `created_at` — Qo'shilgan vaqt

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (yangi va featured mahsulotlar)
2. `product_list` — Barcha mahsulotlar (filter, sort)
3. `product_detail` — Mahsulot haqida batafsil
4. `category_products` — Kategoriya mahsulotlari
5. `brand_products` — Brend mahsulotlari
6. `search` — Qidiruv
7. `on_sale` — Chegirmadagi mahsulotlar

### URL manzillar:
- `/` — Bosh sahifa
- `/mahsulotlar/` — Barcha mahsulotlar
- `/mahsulot/<slug:slug>/` — Mahsulot detali
- `/kategoriya/<slug:slug>/` — Kategoriya
- `/brend/<slug:slug>/` — Brend
- `/chegirma/` — Chegirmalar
- `/qidirish/` — Qidiruv

### Test ma'lumotlar:
- 5-6 ta kategoriya (sub-kategoriyalar bilan)
- 4-5 ta brend
- 20+ ta mahsulot
- Ba'zilarida chegirma narx

### Dizayn talablari:
- E-commerce uslubida
- Chegirma foizi ko'rsatilsin
- "Yangi" va "Chegirma" badgelari

---

## 8-TALABA: SHIFOXONA XIZMATLARI

### Loyiha nomi: `SoglikPlus`

### Maqsad:
Shifoxona xizmatlari haqida ma'lumot beruvchi web ilova yaratish. Foydalanuvchilar bo'limlar, shifokorlar va xizmatlar haqida ma'lumot olishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Department (Bo'lim) modeli:**
- `name` — Bo'lim nomi (Terapiya, Jarrohlik, Pediatriya, Kardiologiya)
- `slug` — URL slug
- `description` — Tavsif
- `icon` — Emoji
- `floor` — Qavat

**2. Doctor (Shifokor) modeli:**
- `full_name` — To'liq ismi
- `department` — Bo'lim (ForeignKey)
- `specialization` — Mutaxassisligi
- `experience_years` — Tajriba (yil)
- `education` — Ta'lim
- `working_hours` — Ish vaqti
- `phone` — Telefon
- `is_available` — Qabul qiladi (BooleanField)

**3. Service (Xizmat) modeli:**
- `name` — Xizmat nomi
- `department` — Bo'lim (ForeignKey)
- `description` — Tavsif
- `price` — Narx
- `duration_minutes` — Davomiyligi

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (bo'limlar va tezkor ma'lumot)
2. `departments` — Barcha bo'limlar
3. `department_detail` — Bo'lim haqida (shifokorlar va xizmatlar)
4. `doctors` — Barcha shifokorlar
5. `doctor_detail` — Shifokor profili
6. `services` — Barcha xizmatlar va narxlar
7. `contact` — Bog'lanish sahifasi

### URL manzillar:
- `/` — Bosh sahifa
- `/bolimlar/` — Bo'limlar
- `/bolim/<slug:slug>/` — Bo'lim detali
- `/shifokorlar/` — Shifokorlar
- `/shifokor/<int:pk>/` — Shifokor profili
- `/xizmatlar/` — Xizmatlar
- `/boglanish/` — Bog'lanish

### Test ma'lumotlar:
- 5-6 ta bo'lim
- 10-15 ta shifokor
- 15-20 ta xizmat

### Dizayn talablari:
- Tibbiyot uslubida (oq, ko'k, yashil ranglar)
- Shifokor kartochkalarida tajriba va mutaxassislik
- Xizmatlar narxi jadval ko'rinishda

---

## 9-TALABA: FITNESS KLUB

### Loyiha nomi: `FitZone`

### Maqsad:
Fitness klub web ilovasini yaratish. Foydalanuvchilar mashg'ulot turlari, trenerlar va jadval haqida ma'lumot olishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. WorkoutType (Mashg'ulot turi) modeli:**
- `name` — Nomi (Yoga, Kardio, Kuch mashqlari, Pilates)
- `slug` — URL slug
- `description` — Tavsif
- `calories_burn` — Yoqiladigan kaloriya (soatiga)
- `difficulty` — Qiyinlik darajasi (choices: easy, medium, hard)
- `icon` — Emoji

**2. Trainer (Trener) modeli:**
- `full_name` — To'liq ismi
- `specialization` — Mutaxassisligi (ManyToManyField to WorkoutType)
- `bio` — Biografiya
- `experience_years` — Tajriba
- `certifications` — Sertifikatlar (TextField)
- `phone` — Telefon
- `instagram` — Instagram username

**3. ClassSchedule (Dars jadvali) modeli:**
- `workout_type` — Mashg'ulot turi (ForeignKey)
- `trainer` — Trener (ForeignKey)
- `day_of_week` — Hafta kuni (choices: 0-6)
- `start_time` — Boshlanish vaqti (TimeField)
- `end_time` — Tugash vaqti (TimeField)
- `max_participants` — Maksimal qatnashchilar
- `current_participants` — Hozirgi qatnashchilar
- `is_active` — Faol

**4. Membership (A'zolik) modeli:**
- `name` — Tarif nomi (Kunlik, Oylik, Yillik)
- `price` — Narx
- `duration_days` — Muddati (kun)
- `features` — Imkoniyatlar (TextField)
- `is_popular` — Mashhur tarif

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa
2. `workout_types` — Mashg'ulot turlari
3. `workout_detail` — Mashg'ulot turi haqida
4. `trainers` — Trenerlar
5. `trainer_detail` — Trener profili va jadvali
6. `schedule` — Haftalik jadval
7. `membership` — Tariflar

### URL manzillar:
- `/` — Bosh sahifa
- `/mashgulotlar/` — Mashg'ulot turlari
- `/mashgulot/<slug:slug>/` — Mashg'ulot detali
- `/trenerlar/` — Trenerlar
- `/trener/<int:pk>/` — Trener profili
- `/jadval/` — Haftalik jadval
- `/tariflar/` — A'zolik tariflari

### Test ma'lumotlar:
- 5-6 ta mashg'ulot turi
- 4-5 ta trener
- 15-20 ta jadval yozuvi
- 3-4 ta a'zolik tarifi

### Dizayn talablari:
- Sport uslubida (qora, to'q ko'k, yashil)
- Jadval jadval (table) ko'rinishda
- Tariflar comparison card ko'rinishda

---

## 10-TALABA: YETKAZIB BERISH XIZMATI

### Loyiha nomi: `TezYetkazish`

### Maqsad:
Ovqat yetkazib berish xizmati katalogini yaratish. Foydalanuvchilar restoranlarni ko'rishi, menyularini o'rganishi mumkin.

### Yaratilishi kerak bo'lgan modellar:

**1. Cuisine (Oshxona turi) modeli:**
- `name` — Oshxona turi (O'zbek, Italyan, Yapon, Fast-food)
- `slug` — URL slug
- `icon` — Emoji

**2. Restaurant (Restoran) modeli:**
- `name` — Restoran nomi
- `slug` — URL slug
- `cuisine` — Oshxona turi (ForeignKey)
- `description` — Tavsif
- `address` — Manzil
- `phone` — Telefon
- `rating` — Reyting (DecimalField)
- `delivery_time` — Yetkazish vaqti (daqiqada, masalan: "30-45")
- `min_order` — Minimal buyurtma summasi
- `delivery_fee` — Yetkazish narxi (0 = bepul)
- `is_open` — Ochiq (BooleanField)
- `is_featured` — Tavsiya etilgan
- `working_hours` — Ish vaqti

**3. MenuItem (Menyu elementi) modeli:**
- `restaurant` — Restoran (ForeignKey)
- `name` — Taom nomi
- `description` — Tavsif
- `price` — Narx
- `category` — Kategoriya (Salatlar, Asosiy, Ichimlik)
- `is_popular` — Mashhur
- `is_available` — Mavjud

### Yaratilishi kerak bo'lgan view funksiyalari:
1. `home` — Bosh sahifa (featured restoranlar, oshxona turlari)
2. `restaurants` — Barcha restoranlar (filter bilan)
3. `restaurant_detail` — Restoran menyusi
4. `cuisine_restaurants` — Oshxona turi bo'yicha
5. `open_now` — Hozir ochiq restoranlar
6. `search` — Qidiruv

### URL manzillar:
- `/` — Bosh sahifa
- `/restoranlar/` — Barcha restoranlar
- `/restoran/<slug:slug>/` — Restoran menyusi
- `/oshxona/<slug:slug>/` — Oshxona turi bo'yicha
- `/ochiq/` — Hozir ochiq
- `/qidirish/` — Qidiruv

### Test ma'lumotlar:
- 5-6 ta oshxona turi
- 10-12 ta restoran
- Har bir restoranda 8-10 ta taom

### Dizayn talablari:
- Delivery app uslubida (Glovo, Yandex.Eda)
- Yetkazish vaqti va narxi aniq ko'rsatilsin
- Ochiq/yopiq holati rangli badge bilan

---

# TOPSHIRISH TARTIBI

## Har bir talaba topshirishi kerak:

1. **Github Repository** — to'liq ishlaydigan Django loyihasi
2. **README.md** — loyihani ishga tushirish bo'yicha qo'llanma
3. **requirements.txt** — `pip freeze > requirements.txt`

## README.md da bo'lishi kerak:

```markdown
# Loyiha nomi

## Loyiha haqida
Qisqacha tavsif

## O'rnatish
1. Virtual environment yaratish
2. Django o'rnatish
3. Migration
4. Superuser yaratish
5. Server ishga tushirish

## Admin panel
- Login: admin
- Parol: (siz belgilagan)

## Sahifalar
- Bosh sahifa: http://127.0.0.1:8000/
- ...
```

---

# MUHIM ESLATMALAR

1. **Plagiat qat'iyan man etiladi** — bir-biringizdan ko'chirmaslik
2. **Har bir talaba o'z loyihasini mustaqil bajaradi**
3. **Savollar bo'lsa — guruhda yoki shaxsiy yozing**
4. **Muddatdan kechikish — har 10 daqiqa uchun -10 ball**
5. **Ishlamaydigan loyiha — 0 ball**

---

# QO'SHIMCHA BALL OLISH IMKONIYATLARI

Har bir qo'shimcha funksiya uchun **+5 ball** (maksimum +15):

1. **Pagination** — sahifalash (10 ta elementdan keyin)
2. **Filter** — narx, sana, kategoriya bo'yicha
3. **Sorting** — saralash (A-Z, narx bo'yicha)
4. **Responsive dizayn** — mobil versiya
5. **Custom 404 sahifa** — chiroyli xato sahifasi
6. **Static fayllar** — alohida CSS fayl

---
