# 🎲🐉 D&D για Μικρούς Ήρωες (SRD Kids Greek)

Ένα πλήρες, ελληνικό, παιδικό πακέτο Dungeons & Dragons: κανόνες, οδηγός Game Master, μια πρώτη
εκστρατεία 5 κεφαλαίων, κάρτες τεράτων & ξορκιών, και τυπώσιμα handouts — έτοιμο να τρέξει μια
οικογένεια ή μια ομάδα παιδιών γύρω από το τραπέζι.

Άνοιξε `index.html` για μια πλοηγήσιμη κεντρική σελίδα με όλο το υλικό.

## Δομή Φακέλων

```
index.html              ← κεντρική σελίδα, συνδέει όλο το υλικό
CLAUDE.md               ← οδηγίες παραγωγής περιεχομένου για το project
files/
  01_tutorial/   tutorial.md/html/pdf            Οι Βασικοί Κανόνες
  02_campaign/   campaign.md/html/pdf, map.svg   Η Κοιλάδα του Δράκου
  03_monsters/   monsters.md/html/pdf            Οδηγός Τεράτων
                 monster-cards.md/html/pdf       Κάρτες Τεράτων
                 monster-stats.csv               Πλήρη stat blocks
  04_spells/     spells.md/html/pdf              Οδηγός Ξορκιών
                 spell-cards.md/html/pdf         Κάρτες Ξορκιών
  05_handouts/   handouts.md/html/pdf            Handouts & Props
  06_dm_notes/   dm-notes.md/html/pdf            Οδηγός Game Master
```

Κάθε deliverable υπάρχει σε τρεις μορφές:
- **`.md`** — η πηγή, εύκολη για επεξεργασία
- **`.html`** — μορφοποιημένη έκδοση, έτοιμη για εκτύπωση (A4)
- **`.pdf`** — τελικό εξαγόμενο αρχείο (δεν παρακολουθείται στο git — βλ. `.gitignore`, αναπαράγεται από το html)

Τα `.md` και `.html` κάθε deliverable κρατιούνται σε sync σκόπιμα — αν αλλάξεις το ένα, ενημέρωσε και το άλλο.

## Γνωστό Κενό

Λείπει ακόμα το deliverable **"Έτοιμοι Χαρακτήρες"** (4–6 pre-generated ήρωες με όνομα, στατιστικά,
ικανότητες και προσωπικότητα) που προβλέπεται στο `CLAUDE.md`. Επισημαίνεται ως placeholder card στο
`index.html`.

## Σχετικά με το SRD-OGL

Το `SRD-OGL_V5.1.pdf` στη ρίζα είναι το επίσημο έγγραφο άδειας (Open Gaming License) του SRD στο οποίο
βασίζεται το υλικό. Δεν παρακολουθείται στο git (μεγάλο binary) — κρατήστε το τοπικά για αναφορά.
