# Juvielyne's 18th Birthday Site 💙

A single-page gift site: iPhone-style passcode lock → holographic/glitter blue reveal →
photo gallery + letter, with background music.

Everything lives in **one file**: `index.html`. No build step, no dependencies.

---

## 1. Add your photos (Cloudinary)

Open `index.html` and search for `gallery-item`. You'll see 6 `<img>` tags like:

```html
<img src="https://res.cloudinary.com/YOUR_CLOUD_NAME/image/upload/v1/juvielyne/photo1.jpg" alt="Photo 1">
```

For each one:
1. Upload the photo to your Cloudinary account.
2. Copy its delivery URL (Cloudinary gives you this after upload — it looks like
   `https://res.cloudinary.com/<your-cloud-name>/image/upload/.../filename.jpg`).
3. Paste it in as the `src`, replacing the placeholder.

You can add more or fewer photos — just copy/paste another `.gallery-item` block and
give the new `<img>` a real Cloudinary URL. Add `wide` to the `class` (e.g.
`class="gallery-item wide"`) if you want that photo to span both columns.

**Note on "Stitch" imagery:** I wasn't able to include actual Disney/Lilo & Stitch
artwork since that's copyrighted. Instead there's a small original blue-alien doodle
under the hero heading for the vibe. If you have your own Stitch photos, stickers, or
fan art you're allowed to use, upload them to Cloudinary like any other photo and drop
them into the gallery the same way.

## 2. Add your song

Put your song file at `assets/song.mp3` (create an `assets` folder next to
`index.html`). The page already looks for it:

```html
<audio id="bg-music" loop preload="auto">
  <source src="assets/song.mp3" type="audio/mpeg">
</audio>
```

If your file has a different name or format, just update that `src` (e.g.
`assets/song.ogg` + `type="audio/ogg"`).

Music starts automatically right after the correct passcode is entered (this counts as
her tapping the screen, so browsers will allow the audio to play). There's also a small
🔊 button in the bottom-right corner once she's in, in case her browser blocks autoplay.

## 3. Add your letter

Search for `letter-text` in `index.html` and replace the placeholder paragraph with
your real letter. You can use line breaks freely — it will keep your formatting.

## 4. Passcode

Already set to `042308`, styled like the iPhone passcode screen (6-digit dots + number
pad). To change it later, find this line near the bottom of the file:

```js
const CORRECT_CODE = "042308";
```

## 5. Deploy

### Push to GitHub
```bash
cd juvielyne-gift
git init
git add .
git commit -m "Juvielyne's 18th birthday site"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

### Host on Cloudflare Pages
1. Go to the Cloudflare dashboard → **Workers & Pages** → **Create** → **Pages** →
   **Connect to Git**.
2. Select the GitHub repo you just pushed.
3. Build settings: leave **Build command** empty and set **Build output directory**
   to `/` (this is a static site, no build needed).
4. Deploy. Cloudflare will give you a URL like `juvielyne-gift.pages.dev` — that's the
   link you share with her.

## 6. Test on a phone before sending

Open the Cloudflare Pages URL on your own phone first:
- Confirm the passcode keypad is easy to tap.
- Confirm the music actually starts after unlocking.
- Confirm photos load and the letter reads well.

That's it — happy birthday to Juvielyne! 🎉
