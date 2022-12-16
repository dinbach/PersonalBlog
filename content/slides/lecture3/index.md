---
title: Hands-on Machine Learning - Lecture 3
date: "2019-06-14T02:00:17+02:00"
url: "/slides/lecture3/"
image: "/slides/lecture3/cover.jpg"
description: ""
ratio: "16:9"
buildFuture : true
image: "img/maria3.png"
thumbnail: img/maria3.png
themes:
- apron
- adirondack
- descartes
classes:
- feature-math
- feature-justify
- feature-nohighlight

---
class: title, smokescreen, shelf, no-footer
background-image: url(/img/maria3.png)

# Hands-on Machine Learning
## Lecture 3

---

# Τι είναι η Μηχανική Μάθηση;

Άρθουρ Σάμιουελ (1959)
> Πεδίο σπουδών που δίνει στους υπολογιστές τη δυνατότητα να μαθαίνουν χωρίς να είναι ρητά προγραμματισμένοι.

Τομ Μίτσελ (1998)
>Ένα πρόγραμμα υπολογιστή λέγεται ότι μαθαίνει από την εμπειρία E σε σχέση με κάποια εργασία T και κάποιο μέτρο απόδοσης P, εάν η απόδοσή του στο T, όπως μετράται από το P, βελτιώνεται με την εμπειρία E.
---
class: col-2,roomy

# Πού χρησιμοποιείται η ML;


- Αναγνώριση ομιλίας και γραφής
- Αναγνώριση αντικειμένων και computer vision
- Data Science

--
- Ανίχνευση απάτης
- Ανίχνευση ανεπιθύμητων μηνυμάτων και ιών
- Μηχανές αναζήτησης

--
- Ανάλυση χρηματοοικονομικής αγοράς
- Διαφήμιση

--
- Ιατρική διάγνωση
- Έλεγχος ρομποτικής
- Αυτοματισμός: χρήση ενέργειας, έλεγχος συστημάτων, βιντεοπαιχνίδια, αυτοοδηγούμενα αυτοκίνητα

--
- Φυσικη

---

# Κατηγορίες ML

- .color-dodgerblue[Ταξινόμηση]
	- Στόχος: Πρόβλεψη αποτελεσμάτων σε διακριτές κατηγορίες
	- \\( y = [0, 1] \\) για δυαδική Ταξινόμηση
    - \\( y = [c_1, c_2,...,c_n] \\) για multi-class Ταξινόμηση 

--

- .color-forestgreen[Παλινδρόμηση]
	- Στόχος: Πρόβλεψη μιας αριθμητικής τιμής σε μια συνεχή έξοδο, που σημαίνει ότι προσπαθούμε να αντιστοιχίσουμε μεταβλητές εισόδου σε κάποια συνεχή συνάρτηση
	- \\( y = \text{Πραγματικοί Αριθμοί} \\)

---
class: roomy
# Κατηγορίες ML

- .color-orangered[Cluster Analysis]
	- Στόχος: Οργανώστε παρόμοια αντικείμενα σε ομάδες
	- \\( D = [D_1 ∪ D_2 ∪ D_3 ... ∪ D_k] \\)

--
- .color-goldenrod[Μείωση διαστάσεων]
	- Στόχος: Μείωση του αριθμού των υπό εξέταση μεταβλητών, λαμβάνοντας ένα σύνολο από κύριες μεταβλητές. Βρείτε μια χαμηλών διαστάσεων (λιγότερο σύνθετη) αναπαράσταση των δεδομένων με μια αντιστοίχιση \\( Z = h(x) \\)

---

# Τεχνικές εκμάθησης(Learning techniques)
.color-dodgerblue[**Μάθηση**: εκτίμηση στατιστικού μοντέλου από δεδομένα]

- .color-forestgreen[**Εποπτευόμενη**]
	- Ο στόχος (ποιο μοντέλο προβλέπει) παρέχεται, δηλαδή γνωρίζουμε τη σχέση μεταξύ της εισόδου και της εξόδου
	- Τα δεδομένα είναι "Ετικέτες"
		- Παλινδρόμηση
		- Ταξινόμηση
--

- .color-orangered[**Χωρίς επίβλεψη**]
	- Ο στόχος είναι άγνωστος ή μη διαθέσιμος
	- Tα δεδομένα είναι "Χωρίς ετικέτα"
		- Cluster analysis 
		- Dimensionality reduction

---

class: img-right, compact

# Ορολογία 

![](Samples-Features.png# center ft )
![](Categories.png#  b-10pct r-10pct w-30pct absolute )

.color-forestgreen[**Sample**]: Σειρά, συμβάν, εγγραφή, παράδειγμα… όλα σημαίνουν το ίδιο πράγμα!

.color-orangered[**Variable**]: Στήλες, διάσταση, χαρακτηριστικό… όλα σημαίνουν το ίδιο πράγμα!
  - Τύποι δεδομένων μεταβλητών: Αριθμητικά, κατηγορικά, συμβολοσειρές,…

\\(x_i\\) : .color-deepskyblue[**input**] variables<br>
\\(y_i\\) : .color-navy[**output**] or target variable<br>
\\((x_i, y_i)\\) : training example<br>
\\( \\{ (x_i, y_i); i = 1, . . .,m \\} \\) : .color-darkorchid[**training set**] of `m` examples

---

class: img-right

# Εποπτευόμενη μάθηση - Πώς λειτουργεί;

![](LearningFlowGeneral.png# center )

Στόχος μας είναι, δεδομένου ενός train σετ, να μάθουμε μια λειτουργία .color-darkorchid[**`h`**] :  \\(X \rightarrow Y\\) ώστε .color-darkorchid[**`h(x)`**] είναι καλός προγνωστικός τρόπος για την αντίστοιχη τιμή του .color-limegreen[`y`]. 

.color-darkorchid[**`h(x)`**]  ονομάζεται υπόθεση (μοντέλο)

--

Όταν το .color-limegreen[`y`] είναι συνεχές, το μαθησιακό πρόβλημα είναι πρόβλημα .color-orange[παλινδρόμησης].

---

class: img-right

# Εποπτευόμενη μάθηση - Πώς λειτουργεί;

![](LearningFlowGeneral.png# center )

Στόχος μας είναι, δεδομένου ενός train σετ, να μάθουμε μια λειτουργία .color-darkorchid[**`h`**] :  \\(X \rightarrow Y\\) ώστε .color-darkorchid[**`h(x)`**] είναι καλός προγνωστικός τρόπος για την αντίστοιχη τιμή του .color-limegreen[`y`]. 

.color-darkorchid[**`h(x)`**]  ονομάζεται υπόθεση (μοντέλο)


Όταν το .color-limegreen[`y`] μπορεί να λάβει 2 διακριτές τιμές το πρόβλημα μάθησης είναι ένα πρόβλημα .color-orange[δυαδικής ταξινόμησης].

---

class: img-right

# Εποπτευόμενη μάθηση - Πώς λειτουργεί;

![](LearningFlowGeneral.png# center )

Στόχος μας είναι, δεδομένου ενός train σετ, να μάθουμε μια λειτουργία .color-darkorchid[**`h`**] :  \\(X \rightarrow Y\\) ώστε .color-darkorchid[**`h(x)`**] είναι καλός προγνωστικός τρόπος για την αντίστοιχη τιμή του .color-limegreen[`y`]. 

.color-darkorchid[**`h(x)`**]  ονομάζεται υπόθεση (μοντέλο)


Όταν το .color-limegreen[`y`] μπορεί να λάβει περισσότερες από 2 διακριτές τιμές, το μαθησιακό πρόβλημα είναι ένα πρόβλημα  .color-orange[ταξινόμησης πολλών τάξεων].

---

class: img-right

# Supervised Learning - Example of a model

![](Scatter-withX.png# center )

Lets say you have data of a movie ranking in IMDB and the views of this movie per month on Netflix 

Say you work for Netflix and want to predict the views of a movie if shown with ranking 7.8

---

class: img-right

# Εποπτευόμενη Μάθηση - Παράδειγμα μοντέλου

![](Scatter-withXandLine.png# center )

Ας υποθέσουμε ότι έχετε δεδομένα για την κατάταξη μιας ταινίας στο IMDB και τις προβολές αυτής της ταινίας ανά μήνα στο Netflix

Ας υποθέσουμε ότι εργάζεστε για το Netflix και θέλετε να προβλέψετε τις προβολές μιας ταινίας εάν έχει κατάταξη 7,8

Ένας αλγόριθμος εκμάθησης μπορεί να θέλει να βάλει .color-forestgreen[ευθεία γραμμή] στα δεδομένα

---

class: img-right

# Εποπτευόμενη Μάθηση - Παράδειγμα μοντέλου

![](Scatter-withXandCurve.png# center )

Ας υποθέσουμε ότι έχετε δεδομένα για την κατάταξη μιας ταινίας στο IMDB και τις προβολές αυτής της ταινίας ανά μήνα στο Netflix

Ας υποθέσουμε ότι εργάζεστε για το Netflix και θέλετε να προβλέψετε τις προβολές μιας ταινίας εάν έχει κατάταξη 7,8

Ένας αλγόριθμος εκμάθησης μπορεί να θέλει να βάλει .color-forestgreen[ευθεία γραμμή] στα δεδομένα

Ένας καλύτερος αλγόριθμος μπορεί να ταιριάζει σε αυτά τα δεδομένα μια .color-forestgreen[τετραγωνική συνάρτηση] ή ένα .color-forestgreen[πολυώνυμο δεύτερης-τρίτης τάξης]

---

# Γραμμική παλινδρόμηση

![](bokeh_plot.png# fr h-6)

Ας υποθέσουμε ότι έχετε το training σετ των αποτελεσμάτων ταινιών στο IMDB και τις εκατομμύρια προβολές στο Netflix

Hypothesis: \\(h(x) = \theta_0 + \theta_1 x \\)<br>
\\( \theta_i \\): parameters

.color-red[Ερώτηση]: πώς μπορούμε να επιλέξουμε καλύτερα το  \\( \theta_0, \theta_1 \\) ?

--> Τυπικό πρόβλημα ελαχιστοποίησης

---

class: img-right, compact

# Cost function

![](gradient-descent-2vars.png )

.color-darkgreen[**Απάντηση**]: Επιλέξτε παραμέτρους \\( \theta_0, \theta_1 \\) ώστε η πρόβλεψή μας .color-darkorchid[**`h(x)`**] να είναι όσο το δυνατόν πιο κοντά στις πραγματικές τιμές .color-limegreen[`y`]. 
Μετράμε την ακρίβεια της υπόθεσής μας χρησιμοποιώντας μια συνάρτηση κόστους(cost function).

Ορισμός cost function:  
\\[ 
J(\theta) = \frac{1}{2m} \sum_{i=0}^{m} (h(x_i) - y_i)^2 
\\]
Η Cost function για γραμμική παλινδρόμηση είναι κυρτή

Στόχος: ελαχιστοποίηση \\( J(\theta_0,\theta_1) \\)
---

class: compact
# Cost Functions

![](LossFunctions.png# center h-6)

---
class: compact
# Εποπτευόμενη Μάθηση - Δημιουργία μοντέλου ML

![](FlowWithLoss.png# center h-5)

Οι παράμετροι του μοντέλου προσαρμόζονται κατά τη διάρκεια της εκπαίδευσης του μοντέλου για την αλλαγή της αντιστοίχισης εισόδου-εξόδου.

- Φτιάξτε συνάρτηση με ρυθμιζόμενες παραμέτρους
- Σχεδιάστε μια Loss Function
- Βρείτε τις καλύτερες παραμέτρους που ελαχιστοποιούν τις απώλειες

---
class: compact
# Εποπτευόμενη Μάθηση - Δημιουργία μοντέλου ML

![](FlowWithLoss.png# center h-5)

Οι παράμετροι του μοντέλου προσαρμόζονται κατά τη διάρκεια της εκπαίδευσης του μοντέλου για την αλλαγή της αντιστοίχισης εισόδου-εξόδου.

- Χρησιμοποιήστε ένα σετ εκπαίδευσης με ετικέτα για να υπολογίσετε την απώλεια/σφάλμα
- Προσαρμόστε τις παραμέτρους για να μειώσετε τo σφάλμα
- Επαναλάβετε μέχρι να σταθεροποιηθούν οι παράμετροι
- Υπολογίστε την τελική απόδοση στο τεστ σετ


---
class: img-right,compact

# Ταξινόμηση με γραμμική παλινδρόμηση;;

![](LinRergess1.png# fr)

Training set για μια εργασία ταξινόμησης σήματος και θορύβου σε σχέση με την ακτίνα ενός jet σωματιδίων

Μόνο δύο πιθανές τιμές, 0 ή 1

Η γραμμική παλινδρόμηση προσπαθεί να προσαρμόσει την ευθεία γραμμή στα δεδομένα

\\( h(x) = \theta ^T x \\)

Για προβλέψεις, ο ταξινομητής έχει threshold 0,5:
- \\( h(x) < 0.5 \\) is background (y=0)
- \\( h(x) > 0.5 \\) is signal (y=1)


---
class: img-right,compact

# Ταξινόμηση με γραμμική παλινδρόμηση;;

![](LinRergess2.png# fr)

Η προσθήκη ενός γεγονότος μακριά δείχνει γιατί η γραμμική παλινδρόμηση δεν μπορεί να λειτουργήσει καλά για προβλήματα ταξινόμησης

Η γραμμική παλινδρόμηση προσπαθεί να προσαρμόσει .color-limegreen[μια άλλη γραμμή] στα δεδομένα, αλλά τώρα για το threshold στο 0,5 διαφορετικά συμβάντα επισημαίνονται ως S ή B

Επίσης, είναι περίεργο ότι παρόλο που  \\( y= [0,1] \\) , ο αλγοριθμος μπορεί να δώσει τιμές \\(h(x)>1\\) or \\(h(x)<0\\)

**Χρειάζεστε άλλη συνάρτηση!**

---

class: img-right, compact
# Ταξινόμηση με συνάρτηση σιγμοειδούς

![](Sigmoid.png# fr)

Χρήση σιγμοειδούς συνάρτησης:
\\[ h_{\theta}(x) = g( \theta ^T x) \\]
\\[ z = \theta ^T x\\]
\\[ g(z) = \frac{1}{1+e^{-z} } \\]

g(z) αντιστοιχίζει οποιονδήποτε πραγματικό αριθμό στο (0, 1),
- Χρήσιμο για τη μετατροπή μιας συνάρτησης αυθαίρετης τιμής σε μια συνάρτηση που ταιριάζει καλύτερα στην ταξινόμηση.
- \\( h_\theta(x) \\) δίνει πιθανότητα ότι η έξοδος είναι 1
  - \\( h_\theta(x) = P(y=1 | x;\theta) = 1 - P(y=0 | x;\theta) \\)
  - \\( P(y=0|x;θ)+P(y=1|x;θ)=1 \\)


---
class: compact
# Gradient descent

![](GradDesc.png# fr w-30pct)

Χρειαζόμαστε έναν αλγόριθμο για την ελαχιστοποίηση της συνάρτησης cost function 

Gradient descent: 
>Επαναλάβετε μέχρι σύγκλισης, βήματα ανάλογα με το αρνητικό της κλίσης της συνάρτησης στο τρέχον σημείο και ενημερώστε τις παραμέτρους με τον εξής κανόνα:
\\[
\theta_j := \theta_j - \alpha \frac{\partial}{\partial \theta_j} J(\theta_0,\theta_1,...,\theta_n)
\\]

- j=0,...,n  feature index number
- \\(\alpha\\) είναι ο .color-red[ρυθμός εκμάθησης] και ελέγχει πόσο μεγάλο θα πρέπει να είναι ένα βήμα στη διαδικασία ελαχιστοποίησης. Εάν είναι πολύ μικρό, η ελαχιστοποίηση είναι αργή. Εάν η πολύ μεγάλο μπορεί να υπερβεί το ελάχιστο ή να αποκλίνει.
- Καθώς πλησιάζουμε το τοπικό ελάχιστο, η παράγωγος γίνεται αυτόματα μικρότερη --> gradient descent κάνει μικρότερα βήματα. 

---

class: compact

# (Deep) Neural networks
![](NN_full1.png# center h-20pct)

- Το θεμελιώδες δομικό στοιχείο της Deep Learning είναι το Perceptron που είναι ένας μεμονωμένος νευρώνας σε ένα νευρωνικό δίκτυο.
- Με δεδομένο ένα πεπερασμένο σύνολο m εισόδων, κάθε είσοδος \\( \theta_1\\) ως \\( \theta_m\\) πολλαπλασιάζεται με ένα βάρος και τότε αθροίζουμε τον σταθμισμένο συνδυασμό τους, 
- έλος περάστε τα από μια μη γραμμική συνάρτηση ενεργοποίησης --> παράγει output Y
- Ένα νευρωνικό δίκτυο αποτελείται από τη συνένωση πολλών νευρώνων με τέτοιο τρόπο ώστε το output ενός είναι input για έναν άλλο.

---

class: compact

# Types of activation functions
![](ActivationFunctions.png# r-5 h-6 w-7 absolute )

---

# Feature scaling - Examples

1. Standardization (or Z-score normalization) features will have the properties of a Gaussian distribution with \\(\mu = 0, \sigma =1\\)
\\[
z = x_{norm} = \frac{x - \mu}{\sigma}
\\]
where \\(\mu\\) is the mean and \\( \sigma\\) is the standard deviation

2. Min-max normalization works better if the distribution is not Gaussian or the standard deviation is very small
\\[
x_{\text{norm}} = \frac{x - xmin}{xmax - xmin}
\\]


---


class: compact
# Train/Test μοντέλου - Κατανομή δεδομένων

![](TrainTestVal.png# center)

Διαχωρίστε το σύνολο δεδομένων σε πολλά μέρη

--

.color-deepskyblue[Training set]: Used to fit model parameters

--

.color-darkorange[Validation set]: Used to check performance on independent data and tune hyper parameters

--

.color-limegreen[Test set]:
- final evaluation of performance after all hyper-parameters fixed
- Needed since we tune, or “peek”, performance with validation set

---

# What is Keras ?

![](keras-logo.png# fl w-6 h-5)

https://keras.io/

Python library to build and train neural networks.

Python wrapper around multiple numerical computation libaries, e.g., TensorFlow, Theano,...

Very abstract and modular. Hides most of the low-level configuration sacrificing little functionality for much easier user interface

Officially supported from Google

