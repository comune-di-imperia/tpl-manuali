# tpl-manuali

Manuali d'uso della sperimentazione di trasporto pubblico locale **a guida
autonoma** del Comune di Imperia: quelli per i passeggeri in cinque lingue, la
guida per il personale di bordo e la locandina per le fermate.

> **Provenienza.** Documentazione redatta nell'ambito della Direzione dei
> Lavori affidata all'Ing. Carlo Capacci per la sperimentazione autorizzata con
> decreto PCM/DTD n. 94/2026. Il servizio a cui si riferiscono e'
> `app-tpl.comune.imperia.it`.

## Che cosa c'e'

| Cartella | Contenuto |
|---|---|
| `html/` | manuali e informative per i passeggeri, nelle cinque lingue |
| `pdf/` | gli stessi documenti impaginati, piu' la guida di bordo e la locandina |

Le **informative** sono due documenti in uno: quella sui rischi e sulle
modalita' della sperimentazione, ai sensi del D.M. 28 febbraio 2018 n. 70, e
quella sul trattamento dei dati personali ai sensi dell'articolo 13 del GDPR.
Il testo che fa fede e' l'italiano; le altre lingue portano in apertura
l'avviso che la traduzione e' di cortesia.

I documenti in `html/` non sono una versione ridotta dei PDF: **sono la stessa
cosa**. I PDF nascono da questi file, e la resa a schermo e quella stampata si
distinguono per un solo foglio di stile.

## Come sono fatti

Ogni manuale e' un unico documento HTML senza dipendenze: nessun framework,
nessun caricamento da rete, nessuno script. Si apre facendo doppio clic.

I fogli di stile sono tre:

- `stile.css` — l'impaginato: copertina, passi numerati, riquadri, tabelle.
  E' misurato in **millimetri**, perche' nasce per il foglio A4;
- `piede_<lingua>.css` — la sola riga a pie' di pagina, tradotta;
- `schermo.css` — tutto racchiuso in `@media screen`: ricostruisce la pagina A4
  come colonna centrata e, sotto gli 800 px, manda le figure a capo sotto il
  testo. Chi compone il PDF non lo vede.

Le figure stanno in `img/` per l'italiano e in `img_<lingua>/` per le altre:
i richiami hanno gli stessi nomi in tutte le lingue, e senza cartelle separate
la versione tedesca mostrerebbe le schermate italiane.

## Rigenerare i PDF

```
weasyprint -s stile.css -s piede_de.css html/manuale-de.html manuale-de.pdf
```

Per l'italiano il piede e' gia' dentro `stile.css` e il secondo `-s` non serve.

## Che cosa dicono i documenti, e perche' cambia

I manuali seguono l'applicazione, e l'applicazione cambia. Due revisioni
recenti, chieste dal Responsabile della protezione dei dati del Comune:

- della persona si conserva la sola **fascia d'eta'** — 6-13, 14-30, 31-65,
  oltre 65 — e non piu' la data di nascita, che non viene nemmeno chiesta;
  all'operatore, alla salita, compaiono soltanto nome e cognome;
- la **casella del consenso sta prima dei campi**, non dopo, e si sblocca solo
  dopo aver premuto *Ho letto l'informativa*: il consenso precede la raccolta.

Chi aggiorna questi documenti guardi prima l'applicazione in esercizio: un
manuale che mostra pulsanti diversi da quelli veri confonde piu' di quanto
aiuti.

## Rifare le figure

Le schermate sono riprese dall'applicazione **in esercizio**, forzando la
lingua con `?lang=<codice>`. Vanno rifatte quando l'interfaccia cambia: un
manuale che mostra pulsanti diversi da quelli veri confonde piu' di quanto
aiuti.

Due avvertenze imparate a spese nostre:

- il **campo della data di nascita** lo disegna il browser secondo le
  impostazioni del telefono, non l'applicazione: su una macchina senza lingue
  installate esce nel formato americano in tutti i manuali;
- la figura del **messaggio di conferma** va ricostruita, non fotografata da
  una casella vera: si pubblicherebbero l'indirizzo di chi ha fatto la prova e
  la grafica del suo programma di posta.

## Licenza

**EUPL-1.2** — European Union Public Licence, la stessa degli altri depositi
del Comune. Vedi [`LICENSE`](LICENSE).
