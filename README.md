# Lockbyte | Cyber Awareness Terminal

Lockbyte is a hacker-terminal-themed cyber awareness web app. Test how strong your password is, take a short quiz on common online threats, and learn simple habits that keep you safe online.

Everything runs **privately in your browser**. There is no backend, no tracking, and nothing you type is ever sent or stored anywhere.

## Features

- **Welcome / login screen**: enter a codename, watch an animated boot sequence with a glitch-style logo and a Matrix-style rain background.
- **Password Scanner**
  - Live strength meter with a 0-100 score and verdict (Very Weak to Very Strong)
  - Length, entropy (bits) and estimated time-to-crack
  - Requirements checklist (length, lowercase, uppercase, digits, symbols)
  - Warnings for common passwords, repeated characters, easy sequences (`abcd`, `1234`, `qwer`), year-like numbers, and "word + digits" patterns
  - Show/hide toggle for the password field
  - Defender tips on passphrases, password reuse, 2FA, OTP safety and password managers
- **Cyber Awareness Quiz**: 5 questions on strong passwords, OTP fraud, password reuse, 2FA and phishing, with instant feedback, a score and a rank (Rookie, Security Agent, Elite Defender).
- **Mission Debrief (feedback)**: star rating, "what did you learn" chips, and an optional message (up to 300 characters).
- **Mission Complete screen**: summary of your quiz score, rating and rank, plus three key rules to remember.

## Getting Started

No build step or dependencies are needed.

1. Download or clone the project.
2. Open the HTML file (`index.html`) in any modern browser.

That's it. You can also host it on any static host (GitHub Pages, Netlify, Vercel, etc.) by uploading the single file.

## Project Structure

```
.
├── index.html   # The entire app: HTML, CSS and JavaScript in one file
└── README.md
```

## How the Password Scanner Works

1. The character pool is estimated from the types of characters used (lowercase 26, uppercase 26, digits 10, symbols 32).
2. Entropy is calculated as `effective length x log2(pool size)`, ignoring runs of repeated characters.
3. Penalties are applied for common passwords, sequences, repeats, years, only-digit or only-letter passwords, and "word + number" patterns.
4. The score is `entropy / 80 x 100`, capped at 100, with hard caps for very short or very common passwords.
5. Time-to-crack assumes an offline attack of **10 billion guesses per second** and is only a rough estimate. Real-world results vary.

> This is an educational tool, not a security guarantee. Do not rely on it as the sole judge of a real password.

## Privacy

- Passwords are analysed locally with JavaScript and are never transmitted or saved.
- Feedback and quiz results stay in the page and are cleared when you log out or start a new session.
- No cookies, analytics, or external requests.

## Accessibility

- Semantic HTML with labelled form controls and ARIA roles for the strength meter and alerts
- Keyboard-friendly navigation with visible focus outlines
- Respects `prefers-reduced-motion` (animations and the rain effect are disabled)
- Responsive layout for phones and desktops

## Tech Stack

- HTML5, CSS3 (custom properties, grid, flexbox)
- Vanilla JavaScript (no frameworks or libraries)
- Canvas for the Matrix rain effect and inline SVG for the logo set

## Customising

- **Quiz questions**: edit the `Q` array in the script (fields: `q` question, `o` options, `a` correct index, `e` explanation).
- **Common passwords list**: edit the `COMMON` array.
- **Colours and theme**: change the CSS variables in `:root` (e.g. `--green`, `--cyan`, `--bg`).
- **Crack-speed assumption**: change the `1e10` value in `analyze()`.

## Disclaimer

For cybersecurity awareness and ethical use only. No real hacking happens in this app.

## License

Add your preferred license here (for example, MIT).
