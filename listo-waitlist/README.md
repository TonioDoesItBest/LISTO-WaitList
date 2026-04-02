# Listo Waitlist Landing Page

Dark luxury waitlist page for the Listo QR mailer campaign.

---

## Deploy to Vercel (5 minutes)

### Step 1 — Set up Supabase table

1. Go to your Supabase project dashboard
2. Open the **SQL Editor** and run this:

```sql
create table waitlist (
  id uuid default gen_random_uuid() primary key,
  name text not null,
  contact text not null,
  role text not null,
  source text default 'qr_mailer',
  created_at timestamptz default now()
);

-- Allow anonymous inserts (for the public form)
alter table waitlist enable row level security;

create policy "Allow public inserts" on waitlist
  for insert with check (true);
```

3. Go to **Settings → API** and copy:
   - Project URL (looks like `https://xxxx.supabase.co`)
   - `anon` public key

### Step 2 — Add your Supabase keys to index.html

Open `index.html` and find these lines near the bottom:

```js
const SUPABASE_URL = 'YOUR_SUPABASE_URL';
const SUPABASE_ANON_KEY = 'YOUR_SUPABASE_ANON_KEY';
```

Replace with your actual values.

### Step 3 — Deploy to Vercel

**Option A — Drag and drop (easiest)**
1. Go to [vercel.com](https://vercel.com) and sign up free
2. Click **Add New → Project**
3. Drag the `listo-waitlist` folder into the upload area
4. Click **Deploy**
5. Done — you'll get a URL like `listo-waitlist.vercel.app`

**Option B — GitHub (recommended for future updates)**
1. Push this folder to a GitHub repo
2. Go to [vercel.com](https://vercel.com) → **Add New → Project**
3. Import your GitHub repo
4. Click **Deploy**
5. Any future pushes to `main` auto-deploy

### Step 4 — Custom domain (optional but recommended)

1. Buy `joinlisto.com` on Namecheap (~$10/yr)
2. In Vercel: **Project Settings → Domains → Add**
3. Type `joinlisto.com` and follow the DNS instructions
4. Takes ~10 minutes to go live

### Step 5 — Generate QR code

1. Go to [qrcode-monkey.com](https://qrcode-monkey.com)
2. Paste your Vercel URL (or custom domain)
3. Set colors: foreground `#C9A84C` (gold), background `#080808` (black)
4. Upload the Listo crow as center logo
5. Download as PNG (high resolution for print)

---

## Viewing signups

In your Supabase dashboard → **Table Editor → waitlist**

You can see every signup with their name, contact, role, and timestamp.

---

## Files

```
listo-waitlist/
├── index.html     ← Full landing page (edit Supabase keys here)
├── vercel.json    ← Vercel routing config
└── README.md      ← This file
```
