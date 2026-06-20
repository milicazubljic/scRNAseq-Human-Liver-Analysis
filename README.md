# Analiza ćelijskog sastava ljudske jetre primenom single-cell RNA-seq metode

## Opis projekta

Cilj ovog projekta je klasifikacija različitih tipova ćelija ljudske jetre i analiza povezanosti između gena primenom metoda za pronalaženje pravila pridruživanja, na osnovu podataka o genskoj ekspresiji dobijenih primenom
single-cell RNA sequencing (scRNA-seq) tehnologije.

U radu su primenjene različite metode mašinskog učenja kako bi se ispitala
mogućnost automatske identifikacije ćelijskih populacija na osnovu njihovih
profila genske ekspresije. Takođe su primenjene različite metode istraživanja
i izdvajanja pravila pridruživanja radi identifikacije obrazaca zajedničke ekspresije gena.

## Skup podataka

Korišćen je [skup podataka](https://www.ncbi.nlm.nih.gov/geo/query/acc.cgi?acc=GSE115469) koji sadrži informacije o genskoj ekspresiji
pojedinačnih ćelija ljudske jetre.

Skup podataka nakon obrade sadrži:

- **8444 ćelije**
- **2000 gena** nakon selekcije atributa
- više različitih tipova ćelija jetre

Matrica genske ekspresije je spojena sa tabelom anotacija ćelija pomoću
jedinstvenog identifikatora ćelije (`CellName`), čime je svakoj ćeliji
dodeljen odgovarajući tip (`CellType`).

## Pretprocesiranje podataka

Pre početka rada nad podacima izvršeni su sledeći koraci obrade:

- uklanjanje gena koji su eksprimirani u manje od 5% ćelija
- izbor najvarijabilnijih gena
- uklanjanje uticaja ekstremnih vrednosti primenom outlier clipping metode
- transponovanje matrice genske ekspresije

Pre primene algoritama mašinskog učenja izvršeni su dodatni koraci:

- kodiranje ciljnih klasa numeričkim vrednostima
- podela podataka na skup za treniranje i testiranje
- skaliranje atributa za modele kojima je to potrebno

Pre primene algoritama za analizu pravila pridruživanja izvršeni su dodatni koraci:

- binarizacija
- uklanjanje previše retkih/čestih gena

## Korišćeni modeli

Za klasifikaciju tipova ćelija testirani su sledeći algoritmi:

- Random Forest
- Gradient Boosting
- XGBoost
- Logistic Regression
- Support Vector Machine (SVM)

Performanse modela procenjene su pomoću:

- tačnosti (*Accuracy*)
- preciznosti (*Precision*)
- odziva (*Recall*)
- Macro F1-score metrike
- matrice konfuzije
- klasifikacionog izveštaja

Za analizu pravila pridruživanja testirani su sledeći algoritmi:

- Apriori
- FP-Growth
- Association Rules
- CHARM

Pravila su izdvajana pomoću:

- podrške (*Support*)
- poverenja (*Confidence*)
- lift mere

## Vizualizacije

U projektu su prikazane:

- matrice konfuzije za sve modele
- poređenje performansi modela
- analiza značajnosti gena
- grafici najvažnijih gena
- PCA projekcija ćelija

## Korišćene tehnologije

- Python
- Pandas
- NumPy
- Scikit-learn
- Matplotlib
- MLxtend
- PAMI


Sve potrebne biblioteke se mogu instalirati komandom

```bash
pip install requirements.txt
```

Preporučeno je pokretati kodove u Jupyter Notebook/Lab okruženju.
