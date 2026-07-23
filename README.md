# Μικροί Ήρωες (SRD Kids Greek)

Ένα πλήρες, ελληνικό, παιδικό πακέτο παιχνιδιού ρόλων (βασισμένο στο SRD 5.1, χωρίς branding της
Wizards of the Coast): κανόνες, 5 έτοιμους χαρακτήρες, οδηγός Game Master, μια πρώτη
εκστρατεία 5 κεφαλαίων, κάρτες τεράτων & ξορκιών, και τυπώσιμα έντυπα — έτοιμο να τρέξει μια
οικογένεια ή μια ομάδα παιδιών γύρω από το τραπέζι.

Άνοιξε `index.html` για μια πλοηγήσιμη κεντρική σελίδα με όλο το υλικό.

## Δομή Φακέλων

```
index.html              ← κεντρική σελίδα, συνδέει όλο το υλικό (μόνο .html, το κοινό/live site)
CLAUDE.md               ← οδηγίες παραγωγής περιεχομένου για το project
content/
  01-tutorial/           tutorial.html                Οι Βασικοί Κανόνες
  02-campaign/           campaign.html, map.svg,
                         npc-stats.csv                Η Κοιλάδα του Δράκου
  03-monsters/           monsters.html                Οδηγός Τεράτων
                         monster-cards.html           Κάρτες Τεράτων
                         monster-stats.csv            Πλήρη stat blocks
  04-spells/             spells.html                  Οδηγός Ξορκιών
                         spell-cards.html             Κάρτες Ξορκιών
                         spell-stats.csv              Πλήρη στοιχεία ξορκιών
  05-handouts/            handouts.html                Έντυπα & Αντικείμενα
                         item-cards.html, npc-cards.html
                         items-stats.csv              Πλήρη στοιχεία αντικειμένων
  06-dm-guide/            dm-guide.html                Οδηγός Game Master
  07-characters/          characters.html              Έτοιμοι Χαρακτήρες
  08-character-creation/  character-creation.html      Οδηγός Δημιουργίας Χαρακτήρα
  images/                 goblins.png, gryphon-cutout.png, skeleton-cutout.png,
                         monsters/*.png, npcs/*.png   Όλες οι εικόνες που χρησιμοποιούν τα deliverables
llm-reference/            ίδια δομή με content/, αλλά μόνο .md — πηγή/αναφορά για
                         AI-assisted επεξεργασία, ΔΕΝ είναι μέρος του live site
card_generator/          εργαλείο κάρτας (card-generator.html + sample CSVs), ανεξάρτητο εργαλείο
```

Κάθε deliverable ζει πλέον ως ένα `.html` κάτω από `content/NN-name/` — αυτό είναι το μόνο
δημόσιο/shipped format. Η αντίστοιχη πηγή `.md` υπάρχει ξεχωριστά κάτω από `llm-reference/NN-name/`,
με ακριβώς την ίδια αρίθμηση/ονομασία φακέλου, αλλά **δεν** συνδέεται από το `index.html` ή από
καμία live σελίδα — προορίζεται μόνο ως ευανάγνωστο κείμενο-αναφορά για μελλοντική AI-assisted
επεξεργασία περιεχομένου. Αν αλλάξεις κάτι σε ένα `.html`, ενημέρωσε (αν θες) και το αντίστοιχο `.md`
στο `llm-reference/` — δεν υπάρχει generator που να συγχρονίζει το ένα από το άλλο.

Κάθε σελίδα `content/NN-name/*.html` έχει ένα μικρό, ενιαίο link πλοήγησης (`.back-link.screen-only`)
κοντά στην κορυφή — «← Αρχική Σελίδα» στις περισσότερες σελίδες, ή link προς το «αδελφό» βασικό
έγγραφο στις σελίδες-κάρτες (π.χ. `monster-cards.html` → `monsters.html`). Το link κρύβεται στην
εκτύπωση (`@media print`). Νέα deliverables πρέπει να ακολουθούν την ίδια σύμβαση.

Αν χρειαστείς PDF, εξήγαγέ το από το `.html` κατά ζήτηση (δεν παρακολουθούνται `.pdf` στο repo — βλ.
`.gitignore`).

## Χρωματικό Θέμα

Όλα τα `.html` deliverables μοιράζονται ένα ενιαίο, μοντέρνο editorial θέμα: system-font stack,
λευκές/near-white επιφάνειες (όχι πια parchment), μοβ branding (`#5a3e85`) με λεπτά 1px περιγράμματα
και έγχρωμη accent stripe αντί για βαριά έγχρωμα πλαίσια, και ζεστό χρυσό (`#e8a93b`) για τονισμό. Τα
tiers δυσκολίας τεράτων, οι σχολές ξορκιών και οι τάξεις χαρακτήρων κρατούν ξεχωριστά, διαχωρίσιμα
χρώματα (πράσινο/πορτοκαλί/κόκκινο/μοβ κ.ά.) για γρήγορη αναγνώριση. Όλα τα CSS custom properties
ζουν στο `:root` κάθε αρχείου (`--brand`, `--gold`, `--ink`, `--paper`, κ.λπ.) — αλλαγή θέματος
σημαίνει επεξεργασία των ίδιων μεταβλητών σε κάθε `.html`.

## Νομική Συμμόρφωση (OGL / SRD)

Όλο το υλικό είναι Open Game Content βασισμένο στο SRD 5.1 — καμία αναφορά σε "Dungeons & Dragons",
"D&D", "5e" ή σε Product Identity της Wizards of the Coast (κόσμοι, επώνυμα τέρατα/χαρακτήρες)
πουθενά στο repo. Το `OGL.md` στη ρίζα περιέχει το πλήρες, αυτούσιο κείμενο της Open Game License
v1.0a και είναι η πηγή αλήθειας για τη licensing συμμόρφωση. Κάθε deliverable (`.md` και `.html`)
έχει στο footer του μια σύντομη δήλωση που παραπέμπει σε αυτό.

Το `SRD-OGL_V5.1.pdf` στη ρίζα είναι το επίσημο έγγραφο του SRD από το οποίο αντλήθηκε το κείμενο
της άδειας. Δεν παρακολουθείται στο git (μεγάλο binary) — κρατήστε το τοπικά για αναφορά.
