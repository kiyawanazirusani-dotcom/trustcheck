# TrustCheck — Jagorar Kammalawa da Ɗorawa

App ɗin yana aiki nan take a "demo mode" (babu Firebase). Bi matakan nan don a kunna shi da gaske, sannan a ɗora shi a GitHub.

## Mataki 1 — Ƙirƙirar Firebase Project

1. Je zuwa https://console.firebase.google.com
2. Danna "Add project", ka ba shi suna (misali `trustcheck-ng`)
3. A cikin project, danna icon na Web (`</>`)  don ƙara sabon web app
4. Kwafi `firebaseConfig` da ya bayyana maka

## Mataki 2 — Kunna Sabis ɗin da ake Buƙata

A cikin Firebase Console:

- **Firestore Database** → Create database → Start in production mode
- **Storage** → Get started (don adana hotunan hujja)
- **Authentication** → Sign-in method → kunna **Phone**

> Lura: Phone Authentication na buƙatar ka kunna **Blaze plan** (pay-as-you-go) idan ka wuce iyakar gwaji ta Firebase kyauta. Amma yawan SMS ɗin gwaji na farko yakan isa don fara aiki.

## Mataki 3 — Saka Config ɗinka a index.html

Buɗe `index.html`, ka nemo wannan sashi kusa da farkon `<script type="module">`:

```js
const firebaseConfig = {
  apiKey: "REPLACE_ME",
  authDomain: "REPLACE_ME.firebaseapp.com",
  ...
};
```

Ka sauya kowane `"REPLACE_ME"` da ainihin bayanin da Firebase ya ba ka a Mataki 1.

## Mataki 4 — Saka Security Rules

1. A Firebase Console, je Firestore Database → Rules
2. Share duk abin da ke ciki, ka manna abin da ke cikin fayil ɗin `firestore.rules` da aka haɗa
3. Danna "Publish"

Wannan yana tabbatar da:
- Kowa na iya **karanta** rahotannin da aka riga aka tabbatar (`approved`) kawai
- Sai an tabbatar da lambar waya kafin a iya **aika** sabon rahoto
- Sabon rahoto koyaushe zai fara a matsayin `pending`

## Mataki 5 — Yadda Ake Tabbatar (Approve) da Rahotanni

Tunda kai kaɗai ne (solo), babu buƙatar tsarin admin mai rikitarwa tukuna:

1. Je Firestore Database a Console
2. Buɗe collection ɗin `reports`
3. Duba kowane rahoto mai `status: "pending"`
4. Idan hujja ta gamsar da kai, ka canza filin `status` zuwa `"approved"` da hannu
5. Rahoton zai bayyana ga jama'a a bincike nan take

Idan rahotanni sun yawaita, za mu iya ƙara wani Business Dashboard na admin daga baya.

## Mataki 6 — Ɗorawa a GitHub Pages (kyauta)

1. Ƙirƙiri sabon repository a GitHub, misali `trustcheck`
2. Loda fayilolin nan (`index.html`, `firestore.rules`, `README.md`) zuwa repository ɗin
3. A cikin repository, je **Settings → Pages**
4. A ƙarƙashin "Source", zaɓi branch ɗin `main` da folder `/ (root)`
5. Danna Save — bayan mintuna kaɗan, app ɗinka zai kasance a:
   `https://<sunan-account-naka>.github.io/trustcheck/`

Wannan shi ne kai tsaye, ba tare da wahala ba — babu buƙatar wani sabar (server) domin duk aikin yana faruwa a browser ɗin mai amfani, yana magana kai tsaye da Firebase.

## Fayilolin da ke ciki

- `index.html` — cikakken app ɗin (bincike + rahoto + tabbatar da waya)
- `firestore.rules` — dokokin tsaro na database
- `README.md` — wannan jagorar
