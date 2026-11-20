# In Cucina con Paolo — GPverse

Ricettario personale in formato unico, installabile come app.

- **Scansiona** un prodotto al supermercato (codice a barre con il lettore integrato di Android/Chrome, o foto della confezione): dati da Open Food Facts, ricette adatte a quel prodotto, mancanti nella lista della spesa
- **Home per sezioni**: Trova un'idea, Aggiungi al ricettario, Spesa, anteprima del ricettario; barra Home / Ricettario / Scansiona / Spesa / Altro
- **Crea** ricette con testo e foto (copertina e foto dei passaggi)
- **Importa** da link: siti di ricette, YouTube (video + descrizione), TikTok (anche link brevi), Instagram (didascalia dalla versione pubblica del post), Facebook — oppure da testo, foto/screenshot o **video salvato** (l'AI lo guarda e prende le foto dei passaggi)
- **Cosa cucino?**: domande guidate che cambiano in base alla portata (base e condimento per i primi, protagonista e taglio per i secondi, tipo e gusto per i dolci, con sotto-domande), occasione, cottura (forno, friggitrice ad aria, microonde…), persone e tempo, richieste, allergie e salute → proposte → tasto + per salvarle nel ricettario
- **Calorie e spesa**: ogni proposta mostra kcal a porzione e costo (€ economica, €€ media, €€€ costosa, con totale stimato e a testa); proposte ordinabili per calorie, prezzo o tempo; stima anche nelle ricette salvate
- **Lista della spesa**: scegli le ricette e le persone per ciascuna, le quantità vengono sommate e ordinate per reparto; spunte, voci libere, condivisione
- **Svuota frigo**: ingredienti, strumenti, tempo e persone → idee, con "Altre idee" e "Fammi la ricetta"
- **Modalità cucina**: un passaggio per schermata, timer, schermo sempre acceso, pulsante "Aiuto!"
- **Nutrizionista**: valori a porzione e per 100 g, % giornaliera, quanto mangiarne (pasto/spuntino), sezione diabetici (carboidrati, indice e carico glicemico), 14 allergeni UE, avvisi e alternative
- **Sostituzioni per intolleranze e allergie**: qualsiasi ricetta mostra accanto a ogni ingrediente cosa usare al suo posto (es. latte → latte senza lattosio, farina → mix senza glutine), con avvisi nei passaggi; la lista della spesa usa già i sostituti; **esigenze di casa** in Altro valide per tutte le ricette
- **Esigenze a tavola** per ogni ricetta: diabete, celiachia, lattosio, vegetariani/vegani, allergie e note sugli ospiti
- **Controllo dosi**: dopo la conversione AI le quantità vengono verificate sul testo originale
- **Raccolte di ricette**: se un link contiene più ricette, scegli quale importare

## Formato di ogni ricetta
1. Scheda: titolo, foto, descrizione, tempi (preparazione / cottura / riposo), difficoltà e campo persone dinamico: scrivi il numero e tutte le dosi (anche nei passaggi) si ricalcolano; persone predefinite in Impostazioni
2. Prima di iniziare: attrezzatura e punti critici ("Occhio a…" con rimedio)
3. Ingredienti: raggruppati per preparazione, in ordine d'uso, con spunta per la mise en place
4. Procedimento: fasi → passaggi con dosi, tempo, temperatura, "è pronto quando…", foto
5. Note e conservazione
6. Valori nutrizionali, allergeni, consigli per diabetici e intolleranti
7. Fonte e diario

## Chiave AI
Le funzioni di conversione, Svuota frigo e Aiuto usano Google Gemini con una chiave gratuita personale
(aistudio.google.com/apikey), salvata solo sul dispositivo. Senza chiave l'app importa comunque dai siti
di ricette che pubblicano i dati in formato standard.

## Dati e sincronizzazione
Le ricette sono salvate nel browser del dispositivo (funziona anche offline). In Altro → Sincronizza tra dispositivi
si accede con Google allo stesso progetto Firebase di GalleggiApp (benzinapp-f4763): ricette in
users/{uid}/incucina_recipes, foto in users/{uid}/incucina_photos (una per documento), lista della spesa,
esigenze di casa e preferenze in users/{uid}/incucina_meta/state. Aggiornamenti in tempo reale, vince la modifica più recente.
Regola Firestore necessaria: `match /users/{userId}/{document=**} { allow read, write: if request.auth != null && request.auth.uid == userId; }`.
Il backup (Altro → Esporta/Importa) resta disponibile come copia di sicurezza.

Versione corrente e cronologia: in cima a `index.html` e in Impostazioni.
`version.json` contiene l'ultima versione pubblicata: l'app lo legge per "Cerca aggiornamenti" (va aggiornato a ogni rilascio insieme ad `APP_VERSION`).
