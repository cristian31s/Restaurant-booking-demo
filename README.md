# Restaurant Bucovina · rezervări online

Demo pentru restaurante: clientul rezervă o masă din telefon, alegând data, numărul de persoane și ora, iar aplicația îi atribuie automat o masă liberă. Restaurantul are o pagină de administrare cu rezervările zilei, planul meselor și posibilitatea de a adăuga rezervări luate la telefon.

**Demo live:** https://restaurant.webwaymedia.com

> Demo cu date fictive. Rezervările se salvează în browser, nu pe un server (vezi „Limitări”).

## Ecrane

| Adresă | Pentru cine | Ce face |
|---|---|---|
| `/` | Client (telefon sau laptop) | Formular de rezervare: dată, persoane (1–8), oră, nume, telefon, email și observații opționale. Rezumat după trimitere. Meniul zilei sub formular. |
| `#admin` | Personalul restaurantului | Statistici, planul meselor pe oră, lista rezervărilor (confirmare, anulare, ștergere), rezervări luate la telefon, date demo |

## Cum funcționează

- **Atribuirea meselor.** Restaurantul are 11 mese (4 de 2 locuri, 4 de 4, 2 de 6 și 1 de 8). La fiecare rezervare, aplicația alege cea mai mică masă liberă care încape grupul.
- **Durata unei rezervări:** 2 ore. Două rezervări care se suprapun nu pot primi aceeași masă, iar rezervările anulate eliberează masa.
- **Program:** luni–vineri 12:00–23:00 și sâmbătă–duminică 11:00–00:00. Orele disponibile se afișează în format 24h, în funcție de ziua aleasă. Se poate rezerva cu până la 3 luni înainte.
- **Fără masă liberă:** dacă nu există o masă potrivită, clientul primește mesaj să aleagă altă oră.
- **Administrare:** vezi rezervările pe zile, planul meselor la ora aleasă, confirmi sau anulezi și adaugi manual rezervări primite la telefon. Butonul „Date demo” umple ziua cu rezervări de test.
- Totul se află într-un singur fișier: `index.html` (HTML, CSS și JavaScript simplu, fără build).
- Interfața e adaptată pentru telefon, iar controalele au culori explicite și `color-scheme: light`, ca să fie lizibile și pe iPhone în dark mode.

## Rulare locală

Deschide `index.html` în browser sau pornește un server local cu `npx serve .`. Pagina de administrare e la `#admin`.

## Limitări (demo)

- **Rezervările se salvează în `localStorage`**, deci rămân doar în browserul în care au fost făcute. Restaurantul nu primește rezervările făcute de alți clienți.
- **PIN-ul de administrare (`1234`) e scris în cod** și nu oferă securitate reală. Oricine poate deschide `#admin` și îl poate citi în sursa paginii.
- Nu se trimit emailuri sau SMS-uri de confirmare.

## Pași spre producție

- [ ] Backend real (de exemplu Supabase): tabel `rezervari` cu reguli RLS, astfel încât oricine să poată crea o rezervare, dar doar adminul să le poată citi și modifica
- [ ] Autentificare reală pentru administrare (email și parolă) în locul PIN-ului
- [ ] Confirmare prin email sau SMS pentru client
- [ ] Notificare pentru restaurant la fiecare rezervare nouă
- [ ] Politică de confidențialitate și acord GDPR pentru datele clienților (nume, telefon)
- [ ] Mese și program editabile din panoul de administrare
- [ ] Hosting pe Cloudflare Pages, pe un subdomeniu al domeniului propriu
