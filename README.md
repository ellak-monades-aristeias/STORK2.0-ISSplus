# STORK 2.0 ISSplus

## Σκοπός του έργου
Σκοπός είναι η μετατροπή της λειτουργικότητας του συστήματος STORK 2.0 ISS (https://joinup.ec.europa.eu/node/137745) έτσι ώστε 

(i) μία εγκατάστασή του να μπορεί να εξυπηρετήσει ένα οποιοδήποτε αριθμό από Πάροχους Υπηρεσίας - Service Providers (SPs) που υποστηρίζουν διαφορετικές μεθόδους επικοινωνίας με το (υπο)σύστημα STORK2.0 ISS

(ii) να εμπλουτιστεί με ένα monitoring tool που επιτρέπει σε κάθε Πάροχο Υπηρεσίας (SP), που διαθετει τα κατάλληλα credentials, να προσπελάσει πληροφορίες για τις συναλλαγές που είχε με την υποδομή STORK 2.0 μέσω STORK 2.0 ISS (ημερομηνία και ώρα, ταυτότητα Authentication Request – Authentication Response, Requested and Collected Identity Attributes κλπ.).

## Εξυπηρέτηση πολλαπλών πάροχων υπηρεσίας
Οι βασικές αλλαγές και επεκτάσεις που πραγματοποιήθηκαν στον κώδικα είναι τρείς. Καταρχήν έγινε μετατροπή του format του URL request που στέλνεται στο STORK2.0 ISS. Πλέον, εκτός του αναγνωριστικού για τον χρήστη προς αυθεντικοποίηση, το URL περιέχει σαν παράμετρο και το αναγνωριστικό του Παρόχου Υπηρεσίας. Μέσω αυτού του αναγνωριστικού, το STORK2.0 ISS γνωρίζει ποια μέθοδο επικοινωνίας πρέπει να χρησιμοποιήσει για να εξυπηρετήσει την συγκεκριμένη αίτηση.  Η δεύτερη αλλαγή αφορά στα configuration files του STORK2.0 ISS όπου προστέθηκε η πληροφορία της συσχέτισης του αναγνωριστικού κάθε Παρόχου Υπηρεσίας με την μέθοδο επικοινωνίας που προτιμά και υποστηρίζει. Τέλος, δημιουργήθηκαν ορισμένες wrap-around κλάσεις σε Java που αναλαμβάνουν να αναγνωρίσουν την μέθοδο επικοινωνίας που απαιτείται και να ενεργοποιήσουν τον κατάλληλο κώδικα του STORK2.0 ISS.

## Monitoring tool
Ο εμπλουτισμός του ISS με ένα monitoring tool επιτυγχάνεται με δύο βασικές αλλαγές-προσθήκες στον κώδικα του STORK 2.0 ISS. Η πρώτη περιελάμβανει μετατροπές-προσθήκες έτσι ώστε η απαραίτητη πληροφορία για κάθε αίτημα αυθεντικοποίησης να αποθηκεύεται σε ένα dedicated log αρχείο, καθώς κάθε γεγονός που ενδιαφέρει το monitoring tool λαμβάνει χώρα. Η δεύτερη προσθήκη αφορούσε στην ανάπτυξη και υλοποίηση ενός web interface με βάση τεχνολογίες web όπως javascript. Το web interface που ενσωματώθηκε μέσα στο STORK 2.0 ISS, επιτρέπει σε κάποιον χρήστη με τα κατάλληλα credentials να προσπελάσει και να δει με λειτουργικό και ευανάγνωστο τρόπο την πληροφορία που βρίσκεται μέσα στο log αρχείο. Ο χρήστης-SP μπορεί να προσπελάσει πληροφορίες για αιτήσεις αυθεντικοποίησης που έγιναν από εκείνον μόνο. Δεν παρέχονται στο χρήστη-SP πληροφορίες που αποτελούν προσωπικά δεδομένα, παρά μόνο πληροφορίες που αφορούν στην λειτουργία του STORK 2.0 ISS. H διαδικασία αυτή της λειτουργίας του monitoring tool φαίνεται συνοπτικά στην παρακάτω εικόνα.

https://github.com/ellak-monades-aristeias/STORK2.0_ISSplus/blob/master/images/MonitoringTool.png

