````markdown name=SETUP.md
# 🚀 Przewodnik Instalacji Cobweeb Bot

Instrukcja krok po kroku jak zainstalować i uruchomić bota.

## 📋 Wymagania Wstępne

Przed rozpoczęciem upewnij się, że masz zainstalowane:

- **Node.js 16+** - [Pobierz tutaj](https://nodejs.org/)
- **npm** - pochodzi z Node.js
- **Git** - [Pobierz tutaj](https://git-scm.com/)

### ✅ Sprawdź czy masz zainstalowane:

```bash
node --version
npm --version
git --version
```

Powinny wyświetlić numery wersji (np. `v16.14.0`)

---

## 🔧 Krok 1: Sklonuj Repozytorium

Pobierz projekt z GitHub:

```bash
git clone https://github.com/multivers0/cobweeb-bot
cd cobweeb-bot
```

**Na Windows w PowerShell:**
```powershell
git clone https://github.com/multivers0/cobweeb-bot
cd cobweeb-bot
```

---

## 📦 Krok 2: Zainstaluj Zależności

Teraz zainstaluj wszystkie potrzebne pakiety:

```bash
npm install
```

**To potrwa 1-2 minuty...** ☕

Powinnaś zobaczyć coś takiego:
```
added 150 packages in 45s
```

---

## 🔑 Krok 3: Skonfiguruj Discord Bot

Zanim uruchomisz bota, musisz stworzyć aplikację Discord.

### A) Przejdź na Discord Developers Portal

1. Otwórz https://discord.com/developers/applications
2. Kliknij **"New Application"**
3. Wpisz nazwę: `Cobweeb Bot`
4. Zaakceptuj Terms of Service
5. Kliknij **"Create"**

### B) Skopiuj Client ID i Client Secret

Na stronie aplikacji:

1. Przejdź do zakładki **"OAuth2"** > **"General"**
2. Skopiuj **Client ID**
3. Skopiuj **Client Secret** (jeśli go nie widzisz, kliknij "Reset Secret")

### C) Ustaw Redirect URI

W **OAuth2** > **General**:

1. Przewiń do **"Redirects"**
2. Kliknij **"Add Redirect"**
3. Wpisz: `http://localhost:3000/auth/discord/callback`
4. Kliknij **"Save Changes"**

### D) Stwórz Bot Token

1. Przejdź do zakładki **"Bot"**
2. Kliknij **"Add Bot"**
3. Pod "TOKEN" kliknij **"Copy"**
4. Zapisz token gdzieś bezpiecznie

**⚠️ NIGDY nie udostępniaj tokenu!**

---

## 🔐 Krok 4: Utwórz Plik .env

W folderze projektu utwórz plik `.env`:

### Na Windows (PowerShell):
```powershell
copy .env.example .env
```

### Na Mac/Linux:
```bash
cp .env.example .env
```

### Edytuj `.env` plikiem tekstowym:

Otwórz plik `.env` w edytorze (Notepad, VS Code, itp) i wpisz:

```
DISCORD_CLIENT_ID=TUTAJ_WPISZ_CLIENT_ID
DISCORD_CLIENT_SECRET=TUTAJ_WPISZ_CLIENT_SECRET
DISCORD_REDIRECT_URI=http://localhost:3000/auth/discord/callback
DISCORD_BOT_TOKEN=TUTAJ_WPISZ_BOT_TOKEN

PORT=3000
NODE_ENV=development
SESSION_SECRET=zmien-to-na-losowy-tekst-np-abc123xyz

BASE_URL=http://localhost:3000
```

**Zastąp:**
- `TUTAJ_WPISZ_CLIENT_ID` → Wklej Client ID z kroku 3B
- `TUTAJ_WPISZ_CLIENT_SECRET` → Wklej Client Secret z kroku 3B
- `TUTAJ_WPISZ_BOT_TOKEN` → Wklej Bot Token z kroku 3D

**Przykład:**
```
DISCORD_CLIENT_ID=1234567890123456789
DISCORD_CLIENT_SECRET=abc123defXYZ_secretkey
DISCORD_REDIRECT_URI=http://localhost:3000/auth/discord/callback
DISCORD_BOT_TOKEN=MTA1OTI2Mzk3MzA5MjAzNTI2.GaBcDe.xyz123abc
PORT=3000
NODE_ENV=development
SESSION_SECRET=mysupersecretkey123
BASE_URL=http://localhost:3000
```

---

## 🤖 Krok 5: Zaproś Bota na Serwer Discord

Zanim uruchomisz aplikację, zaproś bota na swój serwer Discord.

### A) Utwórz link zapraszający

1. Wróć do https://discord.com/developers/applications
2. Wybierz swoją aplikację **"Cobweeb Bot"**
3. Przejdź do **"OAuth2"** > **"URL Generator"**
4. Pod **"Scopes"** zaznacz: `bot`
5. Pod **"Bot Permissions"** zaznacz:
   - ✅ Send Messages
   - ✅ Embed Links
   - ✅ Manage Webhooks

6. Skopiuj **Generated URL** z dołu

### B) Zaproś Bota

1. Otwórz skopiowany URL w przeglądarce
2. Wybierz swój serwer Discord
3. Kliknij **"Authorize"**
4. Rozwiąż CAPTCHA
5. Bot powinien być teraz na Twoim serwerze! ✅

---

## ▶️ Krok 6: Uruchom Aplikację

W folderze projektu uruchom:

```bash
npm start
```

Powinnaś zobaczyć:
```
✅ Database initialized
🚀 Server running on http://localhost:3000
```

---

## 🌐 Krok 7: Otwórz Aplikację

1. Otwórz przeglądarke
2. Przejdź na http://localhost:3000
3. Kliknij **"Login with Discord"**
4. Zaloguj się na swoje konto Discord
5. Autoryzuj aplikację
6. 🎉 Powinnaś zobaczyć Dashboard!

---

## 🪝 Krok 8: Dodaj Feed

W Dashboardzie:

1. Kliknij **"➕ Dodaj Feed"**
2. Wypełnij formularz:
   - **Nazwa Feeda**: np. "Mój Twitter"
   - **Typ Źródła**: Wybierz (Twitter, Instagram, itp)
   - **URL/Handle**: np. `@username`
   - **Discord Serwer**: Wybierz swój serwer
   - **Discord Kanał**: Wybierz kanał
   - **Webhook URL**: Patrz kroku poniżej 👇
   - **Interwał**: 300 (sekund)

### Jak uzyskać Webhook URL?

1. Na serwerze Discord przejdź do kanału
2. Kliknij ustawienia kanału (⚙️)
3. Wybierz **"Integracje"** > **"Webhooks"**
4. Kliknij **"Nowy Webhook"**
5. Wpisz nazwę: "Cobweeb Bot"
6. Kliknij **"Kopiuj URL Webhooka"**
7. Wklej do formularza

3. Kliknij **"Dodaj Feed"**

---

## ✅ Gotowe!

Bot powinien teraz monitorować Twoje źródła i wysyłać powiadomienia na Discord!

---

## 🐛 Rozwiązywanie Problemów

### Problem: "Cannot find module 'express'"
**Rozwiązanie:**
```bash
npm install
```

### Problem: "DISCORD_CLIENT_ID is not defined"
**Rozwiązanie:** Sprawdź czy plik `.env` istnieje i ma prawidłowe wartości

### Problem: "Port 3000 already in use"
**Rozwiązanie:** Zmień PORT w `.env` na np. 3001:
```
PORT=3001
```

### Problem: Bot się nie łączy
**Rozwiązanie:** 
- Sprawdź czy Bot Token jest poprawny
- Sprawdź czy bot jest na serwerze (Krok 5)

---

## 📚 Dodatkowe Zasoby

- [Discord Developers Docs](https://discord.com/developers/docs)
- [Node.js Dokumentacja](https://nodejs.org/docs/)
- [Express.js Guide](https://expressjs.com/)

---

## 💬 Potrzebujesz Pomocy?

Otwórz issue na [GitHub](https://github.com/multivers0/cobweeb-bot/issues)

````
