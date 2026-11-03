# ACTIMED iOS (TestFlight)

`www/` ichidagi ACTIMED prototipi Capacitor orqali iOS ilovaga o'ralgan (`ios/`).
`main` ga har push qilinganda (yoki Actions → "iOS → TestFlight" → Run workflow) GitHub Mac serverida
ilova yig'iladi, imzolanadi va TestFlight'ga yuklanadi.

## Bir martalik sozlash

1. **Bundle ID:** developer.apple.com → Certificates, IDs & Profiles → Identifiers → **+** → App IDs → App →
   Bundle ID (Explicit): `uz.actimed.app`, Description: ACTIMED.
2. **Ilova yozuvi:** appstoreconnect.apple.com → Apps → **+ → New App** → iOS, nomi `ACTIMED`
   (band bo'lsa `ACTIMED Health`), til, Bundle ID `uz.actimed.app`, SKU `actimed`.
3. **API kalit:** App Store Connect → Users and Access → Integrations → **App Store Connect API** →
   Team Keys → **+**, Access: **Admin**. `.p8` faylni yuklab oling (faqat bir marta beriladi).
   Sahifadagi **Issuer ID** va kalitning **Key ID** sini yozib oling.
4. **Team ID:** developer.apple.com → Account → Membership details → Team ID (10 belgi).
5. **GitHub secrets:** repo → Settings → Secrets and variables → Actions → New repository secret:
   - `APPLE_TEAM_ID` — Team ID
   - `ASC_KEY_ID` — Key ID
   - `ASC_ISSUER_ID` — Issuer ID
   - `ASC_KEY_P8` — `.p8` faylning butun matni (`-----BEGIN PRIVATE KEY-----` dan oxirigacha)
6. Actions → **iOS → TestFlight** → **Run workflow**. ~15 daqiqa. Keyin App Store Connect → TestFlight'da
   build paydo bo'ladi (Apple qayta ishlashi 10–30 daqiqa).

## Sinovchilar

App Store Connect → TestFlight → **Internal Testing** (jamoa a'zolari, darhol) yoki **External Testing**
(email yoki Public Link, birinchi build uchun Apple tekshiruvi ~1 kun). Sinovchi App Store'dan
**TestFlight** ilovasini o'rnatadi va taklif havolasini ochadi.

## Prototipni yangilash

`www/index.html` ni yangilang va `main` ga push qiling: yangi build avtomatik TestFlight'ga chiqadi.
