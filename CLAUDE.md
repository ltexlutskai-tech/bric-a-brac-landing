# CLAUDE.md — bricabrac.com.ua

## Керування: Штаб L-TEX

Закріплено рішенням власника 08.11.2026 (Р-240). Цей сайт — окремий
репозиторій, але ним керує той самий Штаб, що й системою L-TEX.

- **Задачі** цього сайту реєструються в реєстрі Штабу:
  `ltexlutskai-tech/ltex-ecosystem` → `docs/ops/REQUESTS.md` (нумерація Р-N
  спільна з L-TEX).
- **Правила Штабу** — `ltex-ecosystem` → `docs/ops/SHTAB_PROTOCOL.md`
  (розділ «Проєкти Штабу»).
- **У `main` зливає ЛИШЕ Штаб і лише після згоди власника.** Сайт на GitHub
  Pages: злиття в `main` = одразу на бойовому сайті.
- **Робочі сесії** працюють у гілці `claude/<задача>` і віддають звіт Штабу; у
  `main` самі не зливають.
- **Правило 6:** перед кожним пунктом перевір, чи це (або частина) вже є в
  коді сайту і в `ltex-ecosystem` (журнал сесій `docs/sessions/INDEX.md`,
  `docs/DECISIONS.md`). Є — будуй поверх, а не поруч.
- **Правило 8:** усе, що побачить відвідувач (нове/змінене поле форми, текст,
  кнопка, сторінка), — окремим пунктом у звіті Штабу.

**Форми → CRM L-TEX.** Усі форми шлють заявку через `window.ltexSendLead`
(скрипт «ЗАЯВКИ → CRM L-TEX» у `<head>` сторінки з формою) на
`https://ltex.com.ua/api/public/site-form` — там вона стає лідом і йде
менеджеру за областю, як заявки з ltex.com.ua. Додає `_form` (id форми),
`_page`, `_title`, `_referrer`, `utm_*`, нормалізує телефон; пастка для ботів —
`_gotcha`. Formspree (лист на пошту, адреса — в `action` форми) — лише РЕЗЕРВ, коли CRM не відповіла (копія з
позначкою «⚠️ НЕ В CRM»); якщо не відповів і резерв — заявка чекає в
`localStorage` (`ltex_pending_leads`) і дошлеться в CRM при наступному
відкритті сайту. Р-306: кожна заявка має `_lid` (один на заявку, той самий у
повторах, черзі й резерві — у темі «⚠️ НЕ В CRM (…, ID …)»); заявка лягає в
чергу ДО відправки й зникає, щойно CRM відповіла; мережа/таймаут/5xx — ще до 2
спроб у CRM (коли сторінку видно, пауза 2–4 с) і лише потім резерв; CRM повтор
з уже прийнятим `_lid` не створює вдруге (`duplicate: true`). Резерв прибрати, коли Штаб скаже (Р-240). Нову форму
підключати так само: `window.ltexSendLead(form, new FormData(form))`, поля
`name`, `phone`, `region` (назва області, як у списку), honeypot.

## Project
Static landing site for L-TEX Bric-a-Brac — wholesale bric-a-brac from UK to Ukraine.

- **Live URL:** https://bricabrac.com.ua
- **Repo:** https://github.com/ltexlutskai-tech/bric-a-brac-landing
- **Deployment:** GitHub Pages (auto-deploy on push to main)
- **Tech:** Pure HTML5 + CSS3 + Vanilla JS (no frameworks)

## IMPORTANT: Read Skills Before Any Task

Skills are stored in `D:\ltex-skills\` (локальні файли власника, у хмарній сесії недоступні). **ALWAYS read the relevant skill BEFORE starting work:**

| Task | Skill to read |
|------|---------------|
| SEO, meta tags, schema, keywords | `D:\ltex-skills\skills\seo-optimization\SKILL.md` |
| Landing page editing, sections, layout | `D:\ltex-skills\skills\bricabrac-landing\SKILL.md` |
| Deploy, git push, GitHub Pages | `D:\ltex-skills\skills\deployment\SKILL.md` |
| Blog posts, content | `D:\ltex-skills\skills\seo-optimization\SKILL.md` + `D:\ltex-skills\skills\bricabrac-landing\SKILL.md` |
| Word documents | `D:\ltex-skills\skills\docx\SKILL.md` |
| Frontend design | `D:\ltex-skills\skills\frontend-design\SKILL.md` |

Also read (локальні файли власника, у хмарній сесії недоступні):
- `D:\ltex-skills\BUSINESS_CONTEXT.md` — company info, products, pricing
- `D:\ltex-skills\CLAUDE.md` — full skill index

## Quick Reference

- **CSS variables:** --green (#4CAF50), --green-dark (#388E3C), --font-display (Bebas Neue), --font-body (Nunito)
- **All CSS/JS inline** — no external files
- **Google Analytics:** G-3KLV760MHV
- **Google Ads:** AW-11017656052
- **Forms:** CRM L-TEX `https://ltex.com.ua/api/public/site-form` (`window.ltexSendLead`); резерв — Formspree (f/mreajbgj, f/xvzbkvvp у каталозі), див. «Керування: Штаб L-TEX»
- **Domain:** bricabrac.com.ua (CNAME file)
- **Content language:** Ukrainian (lang="uk")
