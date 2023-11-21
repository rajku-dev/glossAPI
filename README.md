# Στόχος αυτού του έργου είναι η ανάπτυξη ενός Ελληνικού γλωσσικού μοντέλου ανοιχτού λογισμικού "Greek OSS LLM".


:rocket: **Τρέχουσα δράση: Καταγραφή - αποτίμηση ανοιχτών πηγών κειμένου στα Ελληνικά**

Συμβουλευτείτε το CONTRIBUTING.md για να συνεισφέρετε στην :dart: συγκέντρωση και προτεραιοποίηση συνόλων κειμενικών δεδομένων στα Ελληνικά.

# Εισαγωγικό σημείωμα στα γλωσσικά μοντέλα

Τα γλωσσικά μοντέλα είναι στην ουσία νευρωνικά δίκτυα εκπαιδευμένα σε μεγάλα σύνολα δεδομένων.
Η εντυπωσιακή τους επίδοση οφείλεται στην διαμόρφωση αφηρημένων εσωτερικών αναπαραστάσεων της γλώσσας, που τους επιτρέπει να επιδόνται με επιτυχία σε σειρά έργων.

Επομένως η κρίσιμη συνθήκη για την εκπαίδευση ενός τέτοιου μοντέλου στα Ελληνικά είναι η έκθεσή του σε κατάλληλο αριθμό κειμενικών παραδειγμάτων στην ελληνική γλώσσα.
Σκοπός αυτής της εκπαίδευσης είναι να αποκτήσει το μοντέλο ανάλογη ευελιξία στην ελληνική γλώσσα με αυτήν που επιδεικνύει στα αγγλικά.
Σε αυτό πρέπει να ληφθεί υπόψη η ιστορικότητα της ελληνικής γλώσσας και οι διάφορες ποικιλίες που εμφανίζονται συγχρονικά ή διαχρονικά.

# Επισκόπηση των διαθέσιμων μοντέλων και δεδομένων στα Ελληνικά

Προέχει με συστηματικό τρόπο να αξιολογηθούν τα διαθέσιμα μοντέλα [huggingface](https://huggingface.co/search/full-text?q=greek&type=model) και τα δεδομένα [huggingface-dataset](https://huggingface.co/search/full-text?q=greek&type=dataset).

Η προεκπαίδευση στα ελληνικά είναι σημαντική αλλά δεν πρέπει να είναι από μόνη της κριτήριο.
Το είδος της προεκπαίδευσης που μας ωφελεί είναι εκείνο που μας ανακουφίζει από το υπολογιστικό και χρονικό κόστος.
Προτιμάμε ένα μοντέλο που ήδη καταλαβαίνει κάποια ελληνικά, αλλά για να δούμε αξιόλογες επιδόσεις σε έργα με μικρά περιθώρια λάθους, θα πρέπει το υπό εξέταση μοντέλο να έχει επιπλέον, τόσο ευρεία σημασιολογική γνώση, όσο και απαρτιωμένη αντίληψη διαγλωσσικών παραμέτρων.

Επιπλέον, αυτός είναι ο λόγος που προτιμούμε να βαθμονομήσουμε ένα μοντέλο από το να αναπτύξουμε ένα από το μηδέν.

Πρέπει να ληφθεί υπόψη ότι και για τις δοκιμές θα πρέπει να συστηθεί μια αποτελεσματική ομάδα έργου με ικανούς πόρους στη διάθεσή της, όπως εκείνους που παρέχονται από το [HPC](https://hpc.grnet.gr/).

# Συγκέντρωση, διαλογή, καθαρισμός και επισημείωση διαθέσιμων σωμάτων δεδομένων

Όπως αναφέρθηκε οι γλωσσικές ποικιλίες της ελληνικής γλώσσας, καθώς και τα εξειδικευμένα λεξιλόγιά της, οι επιστημονικές ορολογίες, οι διαφορετικοί τόνοι (επίσημος, ανεπίσημος, γραπτός, προφορικός, κλπ), θα πρέπει να εκπροσωπούνται με συστηματικό τρόπο στα δεδομένα εκπαίδευσης.

Επιπλέον τα δεδομένα αυτά θα πρέπει να παρουσιαστούν με δομημένο τρόπο στα προγράμματα εκπαίδευσης των νευρωνικών δικτύων, και μάλιστα με τέτοια αναπαράσταση που να μην επιβαρύνει άσκοπα τους υπολογιστικούς πόρους.

Πρόκειται επομένως για ένα αρκετά απαιτητικό έργο διαχείρισης δεδομένων, το οποίο όσο καλύτερα γίνει τόσο πιο εντυπωσιακά αναμένεται να είναι τα αποτελέσματα της εκπαίδευσης.

Πρέπει ακόμα να ληφθεί υπόψη ότι αντιμετωπίζουμε μία πληθώρα επιλογών σε μία συγκυρία ραγδαίων εξελίξεων.
Προκύπτει επομένως ότι θα πρέπει να δοκιμαστούν και να αξιολογηθούν διαφορετικά μοντέλα.
Εξ ού προκύπτει με τη σειρά της η ανάγκη ανάπτυξης πρότυπων συνόλων δεδομένων προς διασταύρωση της επίδοσης των εναλλακτικών μοντέλων σε δοσμένα έργα-ορόσημα όπως η ταξινόμηση κείμένου, η συμπλήρωση κενών, κλπ

Αυτό συνεπάγεται αρκετή ανθρωποπροσπάθεια σε συνεργατική ανάπτυξη μοναδιαίων τεστ κώδικα, αλλά και επισημείωση και επαλήθευση των δεδομένων.


# Βαθμονόμηση των μοντέλων στην Ελληνική γλώσσα
    
Απαραίτητο βήμα για να πάμε σε εξειδικευμένα έργα είναι να διδάξουμε στο μοντέλο καλύτερα ελληνικά.

Τα μοντέλα φέρουν ήδη σημασιολογική και πραγματολογική γνώση, καθώς και αφαιρέσεις στατιστικών κανονικοτήτων που διατρέχουν πολλές γλώσσες. 
Αυτό δίνει ένα προβάδιμα, για τη σκοποθεσία μας, στα προεκπαιδευμένα μοντέλα, αφού εκπαιδεύοντας ένα νευρωνικό δίκτυο από το μηδέν στις γλωσσικές ποικιλίες της ελληνικής, χάνουμε όλη αυτήν την γνώση υποβάθρου αλλά και τις διαγλωσσικές συστηματικότητες που τα προεκπαιδευμένα μοντέλα ήδη κατέχουν.

Με αυτόν το τρόπο, αναμένουμε, η έκθεση σε ικανό αριθμό καλά δομημένων παραδειγμάτων στην ελληνική γλώσσα, θα επιτρέψει στο μοντέλο να αποκτήσει ευελιξία με αυτήν, πράγμα που είμαστε σε προνομιακή θέση να επιτύχουμε, αλλά η επιτυχία αυτή θα εξαρτηθεί από τον όγκο, την ποιότητα, και την αντιπροσωπευτικότητα των δεδομένων εκπαίδευσης.

Απαραίτητη σε αυτό το στάδιο είναι η εξασφάλιση υπολογιστικών πόρων, από το HPC, τα πανεπιστήμια, τα ερευνητικά κέντρα, αλλά και η εξέταση των κατανεμημένων πρωτοκόλλων εκπαίδευσης γλωσσικών μοντέλων.
Η κατανεμημένη εκπαίδευση θα επέτρεπε λχ να ασχολούνται διαφορετικές ερευνητικές ομάδες με διαφορετικά υποσύνολα των δεδομένων εκπαίδευσης, και να ενημερώνουν τις παραμέτρους ενός κεντρικού, απομακρυσμένου μοντέλου.

Φυσικά αυτή η λύση απαιτεί αποτελεσματικότατη διαχείριση έργου, και ισχυρές σχέσεις συνεργασίας ανάμεσα σε διαφορετικούς οργανισμούς και ομάδες, που ίσως πρέπει να οικοδομηθεί με τις κατάλληλες ενέργειες, όπως εργαστήρια, συναντήσεις εργασίας, και άλλα δρώμενα.


# Βαθμονόμηση των ελληνοποιημένων μοντέλων σε ειδικά έργα και ανταπόκριση σε οδηγίες

Σε αυτό το στάδιο εκπαιδεύουμε τα μοντέλα, τα οποία ήδη θα έχουμε φέρει σε ένα επίπεδο κατανόησης της ελληνικής γλώσσας, έτσι ώστε να ακολουθούν οδηγίες και να επιτελούν συγκεκριμένα έργα, όπως

- μετάφραση
- περίληψη
- παραγωγή κειμένου
- απάντηση σε ερωτήσεις
- ανάκτηση πληροφοριών
- ταξιμόνηση και επισημείωση κειμένου

Για τα έργα αυτά θα πρέπει να καταρτιστούν ειδικά σύνολα δεδομένων εκπαίδευσης που να αντανακλούν τη δομή του ζητούμενου έργου, και να επιτρέπουν την ποσοτική και ποιοτική αξιολόγηση της επίδοσης.
Και εδώ ισχύουν όσα αναφέρθηκαν για τη συγκέντρωση και διαλογή δεδομένων.

Η ποιότητα και αυτών των δεδομένων εκπαίδευσης, η οποία μπορεί επιπλέον να είναι η ίδια μια ανατροφοδοτούμενη διαδικασία με κύκλους εκπαίδευσης, αξιολόγησης, αναθεώρησης του συνόλου δεδομένων εκπαίδευσης, των παραμέτρων του μοντέλου, και επανεκπαίδευσής του.

Αυτό προϋποθέτει την συνέχεια της απασχόλησης των εμπλεκομένων ατόμων στο έργο, και καλές πρακτικές διακυβέρνησης των γνωσιακών βάσεων, του πηγαίου κώδικα, και των βάσεων δεδομένων του έργου.

# Αξιολόγηση της επίδοσης και βαθμονόμηση παραμέτρων

Εκτός από την αναθεώρηση και την διακυβέρνηση των δεδομένων εκπαίδευσης, θα πρέπει να επιτηρούμε στενά και τις παραμέτρους εκπαίδευσης του μοντέλου, όπως το ρυθμό μάθησης, τα μεγέθη κατατεμαχισμού των δεδομένων, τους αριθμούς επαναλήψεων, και άλλων τεχνικών όψεων, για τις οποίες καθ᾽ ύλην αρμόδιοι είναι οι ειδικοί μηχανικής μάθησης, και ιδίως των νευρωνικών δικτύων.

Και εδώ είναι σημαντική η κατάρτιση πρότυπων έλεγχων επίδοσης για τα επιμέρους έργα που να παρουσιάζονται με ευσύνοπτο συστηματικό τρόπο.

Τα αποτελέσματα θα πρέπει να παρουσιάζονται στη διοίκηση του έργου με τους καθιερωμένους τρόπους και τις μετρικές με τις οποίες αξιολογείται η ποιότητα προσαρμογής και η επίδοση του μοντέλου σε διαφορετικές όψεις του έργου, έτσι ώστε το κρίσιμο αυτό στάδιο της εκπαίδευσης να οδηγήσει σε ένα αξιόπιστης επίδοσης, γενικεύσιμο μοντέλο, που να μπορεί να έχει πραγματικές χρήσεις σε διαφορετικούς τομείς.


# Αυτοτροφοδοτούμενη μάθηση με ανθρώπινη επίβλεψη

Με τις τεχνικές του reinforcement learning μπορεί να τελειοποιηθεί η επίδοση του μοντέλου, έτσι ώστε να προσαρμοστεί σε μια συνεχιζόμενη ανατροφοδότηση που θα λαμβάνει από ανθρώπινους δοκιμαστές, όπως πχ μέσα από την αξιολόγηση των απαντήσεών του ως ικανοποιητικών ή μη.

Αυτό προυποθέτει την ανάπτυξη ενός συστήματος ανατροφοδότησης της επίδοσης και την διεπαφή αξιολόγησης από τους δοκιμαστικούς χρήστες.

Καθ᾽υλην αρμόδιοι για αυτό είναι οι ειδικοί μηχανικής μάθησης, κατά προτίμηση με εμπειρία στο reinforcement learning, και ειδικοί στην ανάπτυξη διεπαφών χρήστη για γλωσσικά μοντέλα που ακολουθούν οδηγίες.

# Χρήση του μοντέλου σε διαφορετικούς τομείς και επαναξιολόγηση

Εφόσον το μοντέλο αποκτήσει ικανοποιητική, γενική και ειδική, επίδοση μπορεί να χρησιμοποιηθεί σε διαφορετικά έργα, ή να ανοιχτεί ως API, και να συγκεντρωθούν επιπλέον στοιχεία για την συνεχιζόμενη βελτίωση της επίδοσής του.

Αυτό προϋποθέτει τις απαραίτητες υποδομές για να φιλοξενηθεί και να μπορεί να εξυπηρετεί πολλαπλά αιτήματα χεηστών.
Πρέπει να ληφθεί υπόψη ότι η επιτυχής εκπαίδευση ενός τέτοιου έργου στα ελληνικά θα αξιοποιηθεί ευρέως από κάθε είδους εφαρμογές, και μπορεί να προεξοφληθεί ότι οι απαιτήσεις φιλοξενίας επίσης μπορεί να μην είναι αμελητέες.

# Ενδεικτικά, μια τέτοια ομάδα θα μπορούσε να αποτελείται από:

- Μηχανικούς τεχνητής νοημοσύνης και γνωσιακής επιστήμης
- Μηχανικούς NLP και υπολογιστικής γλωσσολογίας
- Αναλυτές δεδομένων
- Ειδικούς πληροφοριακών συστημάτων
- Ειδικούς σε μεταδεδομένα, οντολογίες, ελεγχόμενα λεξιλόγια
- Ειδικούς κοινωνικής γλωσσολογίας
- Ειδικούς ποιοτικής ανάλυσης περιεχομένου
- Κατά τομέα ειδικούς πχ νομικά


# Αρθρογραφία μας για ένα Ανοιχτό Ελληνικό LLM

[Νευρωνικά Δίκτυα και Μηχανική Μάθηση](https://edu.ellak.gr/2023/04/11/nevronika-diktia-ke-michaniki-mathisi/)

[Ανοιχτός Κώδικας και Προηγμένα Γλωσσικά Νευρωνικά Δίκτυα](https://openstandards.ellak.gr/2023/10/26/anichtos-kodikas-ke-proigmena-glossika-nevronika-diktia/)


