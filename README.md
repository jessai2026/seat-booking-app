# Seat-Booking App

[![CI](https://github.com/jessai2026/cpt304-seat-booking/actions/workflows/ci.yml/badge.svg)](https://github.com/jessai2026/cpt304-seat-booking/actions/workflows/ci.yml)
[![codecov](https://codecov.io/gh/jessai2026/cpt304-seat-booking/branch/main/graph/badge.svg)](https://codecov.io/gh/jessai2026/cpt304-seat-booking)

A vanilla `JavaScript` seat-reservation system. It can be easily adjusted to be used in any project that needs a simple **seat-reservation system**.

The app uses `ES6` classes and modern browser APIs such as `querySelector`, `createElement`, and `localStorage`. It also uses the `crypto` API to generate random ids for services and sectors.

**Live demo:** https://cpt304-seat-booking.vercel.app

## How it works

The app has three main classes: `SeatBookingApp`, `Service`, and `Sector`.

1. **`SeatBookingApp`** creates instances of `Service` and `Sector`, renders services to the DOM, and caches data to `localStorage`. It provides methods to add sectors and services, get the list of services, and set the current service.
2. **`Service`** represents a service with a name, price, and available seats. It provides methods to reserve seats, add/remove reserved seats, and mark them as booked.
3. **`Sector`** represents a sector with a unique id, a price multiplier, and a list of seats in each row. It generates unique seat ids and renders sectors to the DOM.

## Coursework Enhancements (CPT304 CW1)

This fork extends the original project for the CPT304 *Research-Led Software Enhancement* coursework.

### Accessibility fixes (WCAG 2.1)
- **D1** — Replaced `<h3>` headings with `<label for="…">` for all form inputs; fixed a dynamic-id bug (`price-[object Object]` → `price-${sector.sector}`). *WCAG 1.3.1 / 4.1.2*
- **D2** — Added a `<label>` for the service `<select>` dropdown. *WCAG 1.3.1 / 4.1.2*
- **D3** — Wrapped the app in a `<main>` landmark element. *WCAG 1.3.1*
- **D4** — Added `role="button"`, `aria-label`, `tabindex="0"`, and `Enter`/`Space` keyboard handlers to seat elements. *WCAG 4.1.2 / 2.1.1*
- **State reset** — Reserved seats and order details are now cleared on service add / update / delete and on dropdown change.

### Baseline standards
- **Live uptime** — Deployed to Vercel (auto-deploy on push to `main`).
- **Test coverage** — Jest unit tests for `Service` and `Sector` (`__tests__/models.test.js`), reported via Codecov.
- **Internationalisation** — English / Simplified Chinese toggle with `localStorage` preference (`script/i18n.js`, `locales/en.json`, `locales/zh.json`).
- **Legal compliance** — Cookie consent banner (`script/cookies.js`) and a dedicated [Privacy Policy](privacy.html) page.
- **CI/CD** — GitHub Actions runs tests and uploads coverage to Codecov on every push and PR (`.github/workflows/ci.yml`).

## Local development

```bash
npm install
npm test           # run Jest with coverage
```

Open `index.html` directly in a browser to run the app (no build step required).

## Future work

- Allow users to update the price multiplier for each sector through the UI.
- Allow users to create new sectors at runtime (storage mechanism is already in place but disabled).
