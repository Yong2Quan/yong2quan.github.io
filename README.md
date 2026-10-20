# [Thomas Yong's Personal Website](https://yong2quan.github.io/) 🚀

This repository contains the source code for my personal portfolio website, hosted via GitHub Pages.

👉 **Live Demo:** [yong2quan.github.io](https://yong2quan.github.io/)

---

## 🛠️ Built With

A quick breakdown of the tech stack used to build this site:

* **Frontend:** HTML5, CSS3, JavaScript (ES6+)
* **Framework/Static Site Generator:** None — a single hand-written page, no build step
* **Styling:** Plain CSS, written by hand (no Tailwind or Bootstrap)
* **Fonts:** Space Grotesk and JetBrains Mono, via Google Fonts
* **Forms:** [FormSubmit](https://formsubmit.co) for contact form delivery
* **Deployment:** GitHub Pages, serving the repository root

Everything lives in `index.html` — styles and scripts are inline, so the only
external requests are Google Fonts and the form relay. There is nothing to
compile and no dependencies to install.

## 📂 Repository Structure

* `index.html` — The entire site: markup, styles and scripts.
* `/shots` — Screenshots of the projects shown in the carousel.
* `.nojekyll` — Tells GitHub Pages to serve the files as-is, skipping Jekyll.

## 🚀 Local Development

If you want to clone this repository and run it locally, follow these steps:

1. **Clone the repo:**
   ```bash
   git clone https://github.com/Yong2Quan/yong2quan.github.io.git
   ```
2. **Navigate into the directory:**
   ```bash
   cd yong2quan.github.io
   ```
3. **Serve it over HTTP:**
   ```bash
   python -m http.server 8000
   ```
   Then open <http://localhost:8000>.

Opening `index.html` directly as a file works for everything except the contact
form — FormSubmit rejects requests that do not come from a web server, so use
the local server above when testing it.

## ✏️ Updating the Projects Carousel

Projects are defined in the `screens` array near the bottom of `index.html`:

```js
var screens=[
  {img:"shots/makan-simi.png", t:"Makan Roulette", note:"...", url:"...", href:"...", tall:false}
];
```

`tall: true` renders the screenshot in a phone frame, `false` in a browser
frame. Add an entry and drop a matching image into `/shots`.

Screenshots of live sites are captured with headless Chrome or Edge:

```bash
msedge --headless=new --hide-scrollbars --virtual-time-budget=6000 \
  --window-size=1280,800 --screenshot=shots/name.png https://example.com
```

## ✉️ Contact Form

A static page cannot send email on its own, so the form POSTs to FormSubmit,
which relays the message on. Two constants in `index.html` configure it:

```js
var MAIL_TO="...";
var FORM_ENDPOINT="https://formsubmit.co/ajax/"+MAIL_TO;
```

The form needs one-time activation: the first message sent from the live site
triggers a confirmation email, and the link inside it has to be clicked before
anything is delivered.

To keep the address out of the page source, swap `FORM_ENDPOINT` for the alias
(`/ajax/el/<alias>`) that FormSubmit issues after activation.

## 🙏 Credits

* **Design inspiration** — the rotating project carousel is a reimplementation
  of the scrolling work scene on [wodniack.dev](https://wodniack.dev) by
  Antoine Wodniack. The CSS-variable approach to the 3D transform is his idea;
  the code here was written from scratch.
* **[Space Grotesk](https://fonts.google.com/specimen/Space+Grotesk)** — designed
  by Florian Karsten, based on Colophon Foundry's Space Mono. SIL Open Font License.
* **[JetBrains Mono](https://www.jetbrains.com/lp/mono/)** — by JetBrains.
* **[FormSubmit](https://formsubmit.co)** — free form-to-email relay, no account required.
* **GitHub Pages** — hosting. The `.nojekyll` escape hatch is a GitHub Pages
  convention rather than a third-party project, introduced in
  [Bypassing Jekyll on GitHub Pages](https://github.blog/news-insights/bypassing-jekyll-on-github-pages/) (2009).

## 📄 License

No licence has been applied to this repository yet, so default copyright
applies and all rights are reserved.

If you would like others to be free to fork and adapt it, add a `LICENSE` file
(MIT is the usual choice for a portfolio) and update this section to match.
