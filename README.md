

# comp-arch-lab-3
Αναφορά και κώδικας για το τρίτο εργαστήριο του μαθήματος Αρχιτεκτονική Προηγμένων Υπολογιστών.

Authors: Δήμου Μαρία, Μεταλλίδου Νεφέλη

### Βήμα 1

#### Ερώτημα 1


Η επικύρωση του McPAT στο αρχικό paper είχε γίνει ως εξής:
Η κύρια εστίαση του McPAT είναι η ακριβής μοντελοποίηση ισχύος και περιοχής σε αρχιτεκτονικό επίπεδο, όταν ο χρονισμός δίνεται ως κύριος περιορισμός σχεδίασης. Τόσο η σχετική όσο και η απόλυτη ακρίβεια είναι σημαντικές για τη μοντελοποίηση ισχύος σε αρχιτεκτονικό επίπεδο. Σχετική ακρίβεια σημαίνει ότι οι αλλαγές στη μοντελοποιημένη ισχύ ως αποτέλεσμα των τροποποιήσεων της αρχιτεκτονικής θα πρέπει να αντικατοπτρίζουν σε σχετική κλίμακα τις αλλαγές που θα βλέπαμε σε μια πραγματική σχεδίαση. Ενώ η σχετική ακρίβεια είναι κρίσιμη, η απόλυτη ακρίβεια είναι επίσης σημαντική εάν κάποιος θέλει να συγκρίνει τα αποτελέσματα με τα όρια θερμικής ισχύος σχεδιασμού (TDP) ή να τοποθετήσει την εξοικονόμηση ισχύος στον πυρήνα στο πλαίσιο ολόκληρου του επεξεργαστή ή ολόκληρου του συστήματος. Η σχετική ακρίβεια του McPAT διασφαλίζει ότι τα σχετικά βάρη ισχύος των διαφόρων εξαρτημάτων ενός τσιπ έχουν μοντελοποιηθεί σωστά. Η απόλυτη ακρίβεια μεγέθους του McPAT σημαίνει ότι οι αριθμοί ισχύος για τα επιμέρους στοιχεία και η συνολική ισχύς αξιολογούνται σωστά.

Οι επεξεργαστές που είχαν χρησιμοποιηθεί ήταν οι εξής :
* Niagara (90nm, 1.2GHz, 1.2V)
* Niagara2 (65nm, 1.4GHz, 1.1V)
* Xeon (65nm, 3.4GHz, 1.25V)
* Alpha 21364 (180nm, 1.2GHz, 1.5V)

#### Ερώτημα 2
* **Dynamic power**: Τα κυκλώματα καταναλώνουν δυναμική ισχύ όταν φορτίζουν και εκφορτίζουν τα χωρητικά φορτία για να αλλάξουν καταστάσεις. Η δυναμική ισχύς είναι ανάλογη της συνολικής χωρητικότητας του φορτίου, της τάσης τροφοδοσίας, της μεταβολής της τάσης κατά τη διάρκεια της μεταγωγής, της συχνότητας του ρολογιού και του συντελεστή δραστηριότητας. Υπολογίζουμε τη χωρητικότητα φορτίου μιας μονάδας αναλύοντάς την σε βασικά μπλοκ κυκλωμάτων και χρησιμοποιώντας αναλυτικά μοντέλα για κάθε μπλοκ με συσκευές κατάλληλου μεγέθους. Υπολογίζουμε τον παράγοντα δραστηριότητας χρησιμοποιώντας στατιστικά στοιχεία πρόσβασης από την αρχιτεκτονική προσομοίωση μαζί με τις ιδιότητες του κυκλώματος.
* **Short-circuit power**: Υπολογίζουμε την ισχύ βραχυκυκλώματος χρησιμοποιώντας τις εξισώσεις που προκύπτουν από την εργασία των Nose et al. που προβλέπει τις τάσεις για την ισχύ βραχυκυκλώματος. Εάν ο λόγος της τάσης κατωφλίου προς την τάση τροφοδοσίας συρρικνωθεί, η ισχύς βραχυκυκλώματος γίνεται πιο σημαντική. Συνήθως είναι περίπου το 10% της συνολικής δυναμικής ισχύος, ωστόσο σε ορισμένες περιπτώσεις μπορεί να φτάσει και το 25% της δυναμικής ισχύος.
* **Static power**: Η στατική ισχύς καταναλώνεται λόγω του ρεύματος διαρροής μέσω των τρανζίστορ, τα οποία στην πραγματικότητα λειτουργούν ως "ατελείς" διακόπτες.
* **Leakage power**: Το ρεύμα διαρροής εξαρτάται από το πλάτος των τρανζίστορ και την τοπική κατάσταση των διατάξεων. Υπάρχουν δύο μηχανισμοί διαρροής. Η διαρροή κάτω από το κατώφλι εμφανίζεται επειδή ένα μικρό ρεύμα περνάει μεταξύ της πηγής και της αποστράγγισης των τρανζίστορ εκτός κατάστασης. Η διαρροή πύλης είναι το ρεύμα που διαρρέει μέσω του ακροδέκτη πύλης και ποικίλλει σε μεγάλο βαθμό ανάλογα με την κατάσταση της διάταξης. Προσδιορίζουμε το ρεύμα διαρροής της μονάδας χρησιμοποιώντας τα δεδομένα της MASTAR και της Intel.

#### Ερώτημα 3


#### Ερώτημα 4

### Βήμα 2

#### Ερώτημα 1

#### Ερώτημα 2

#### Ερώτημα 3

### Κριτική

Η εργασία αυτή μας φάνηκε πολύ χρήσιμη στο να κατανοήσουμε πώς τρέχουν τα benchmarks και πώς η αλλαγή κάθε παραμέτρου επηρεάζει την απόδοση του συστήματος. Ωστόσο απαιτεί καλή κατανόηση και της θεωρίας.




