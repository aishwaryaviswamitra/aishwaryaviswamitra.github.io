# aishwaryaviswamitra.com — portfolio site

A single self-contained page. All images are embedded in the file, so there is nothing else to upload and nothing to break. Total size is about 580 KB.

---

## Put it online (no command line needed)

1. Sign in at [github.com](https://github.com). If you don't have an account, make one — the username becomes part of your free web address, so pick something you're happy with (`aishwaryaviswamitra` is ideal if it's free).

2. Click **+** in the top right → **New repository**.

3. Name it exactly: `YOURUSERNAME.github.io` — replacing `YOURUSERNAME` with your actual GitHub username, lowercase. This exact name is what makes GitHub serve it as a website.

4. Set it to **Public**. Don't tick "Add a README". Click **Create repository**.

5. On the next screen click **uploading an existing file**.

6. Drag in `index.html` and `.nojekyll` from this folder. (If your computer hides `.nojekyll` because it starts with a dot: on Mac press `Cmd + Shift + .` in Finder to show hidden files. It's a completely empty file that just tells GitHub not to process the page — the site works without it, but it avoids occasional oddities.)

7. Click **Commit changes**.

8. Wait two or three minutes, then visit `https://YOURUSERNAME.github.io`

That's the whole thing. It's free and there's no traffic limit worth worrying about.

---

## Use your own domain

Buy a domain anywhere (Namecheap, Cloudflare, Porkbun — roughly £10–15 a year). Then:

**In GitHub:** repository → **Settings** → **Pages** → under "Custom domain" enter `aishwaryaviswamitra.com` → **Save**. Tick **Enforce HTTPS** once it becomes available (it can take an hour or so to appear).

**At your domain registrar,** in the DNS settings, add these five records:

| Type | Name | Value |
|---|---|---|
| A | @ | 185.199.108.153 |
| A | @ | 185.199.109.153 |
| A | @ | 185.199.110.153 |
| A | @ | 185.199.111.153 |
| CNAME | www | YOURUSERNAME.github.io |

DNS changes usually take 10–60 minutes, occasionally a few hours. These IP addresses are GitHub's and are stable, but if something doesn't work, check GitHub's current "Managing a custom domain" documentation in case they've changed.

---

## Making changes later

Open `index.html` in any text editor (VS Code, Sublime, even TextEdit in plain-text mode). It's one file — the content is plain HTML near the bottom, the styling is in the `<style>` block at the top.

To publish an edit: go to the file in your repository on github.com, click the pencil icon, paste in the new version, and commit. The live site updates within a minute or two.

There's a `TO DO` comment near the bottom of the file listing the stories you wanted to add. It's invisible to visitors.

---

## Adding a new video

Find this pattern in the file:

```html
<div class="vid wide" data-v="VIDEO_ID" data-h="HASH">
  <button type="button">
    <span class="ttl">Your title here</span>
    <span class="play"><i></i>Play</span>
  </button>
</div>
<p class="vid-cap">Your caption. &middot; <a href="https://vimeo.com/VIDEO_ID" target="_blank" rel="noopener">Open on Vimeo</a></p>
```

Copy it, then replace:

- `VIDEO_ID` — the number in the Vimeo URL
- `HASH` — the code after `?h=` in Vimeo's embed code (Share → Embed). Private videos need it; public ones may not have one, in which case delete the whole `data-h="..."` attribute.
- `wide` for landscape video, `tall` for vertical

---

## Adding a new image

Images are embedded directly in the file as text, so you can't just drop a photo in. Either:

- Send the photo to me and I'll rebuild the file, or
- Convert it yourself at a site like base64-image.de, then paste the result in place of an existing `src="data:image/jpeg;base64,..."` value.

Resize photos to around 900px wide before converting, or the file gets large and slow.

---

## Notes

- Dark mode is handled automatically — the page follows whatever the visitor's device is set to.
- It's responsive down to phone size.
- Videos load only when clicked, so the page stays fast.
- If you ever want to move off GitHub, this file works anywhere: Netlify, Cloudflare Pages, or any web host. Upload it and it works.
