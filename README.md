# Piramide

>## Consegna prova

Il tuo compito oggi è scrivere un programma che calcoli l'altezza massima di una piramide (in piani) dato un certo numero di cubi di pietra.

Ipotizzando che:

- i piani della piramide siano quadrati
- la piramide da costruire sia compatta, cioè non ci siano cavità al suo interno. 
- ogni piano è quadrato, con una lunghezza laterale inferiore di due rispetto a quella sottostante.
- il primo piano è sempre di un mattone

Esempi:

- il primo piano ha un mattone, il secondo 9 mattoni, il terzo 25 e così via
- con 1 mattone la piramide è alta 1 piano
- con 84 mattoni la piramide è alta 4 piani

Va bene se hai blocchi rimanenti, purché tu costruisca una piramide completa.

Sviluppare:

- il metodo int Piani( int mattoni ) che torna il numero di piani
- il metodo int Rimanenti( int mattoni ) che torna il numero di mattoni rimasti dopo la costruzione

>## Codice
```c#

namespace Piramide{
public class Piramide{
    public static int Piani(int mattoni) {
        int piani = 0;
        while (mattoni >= (2 * piani + 1) * (2 * piani)) {
            piani++;
            mattoni -= (2 * piani - 1) * (2 * piani - 1);
        }
        return piani;
    }
    public static int Rimanenti(int mattoni) {
        int piani = Piani(mattoni);
        int mattoniUtilizzati = 0;
        for (int i = 1; i <= piani; i++) {
            mattoniUtilizzati += (2 * i - 1) * (2 * i - 1);
        }
        return mattoni - mattoniUtilizzati;
        }
    }
}
```

>## Spiegazione codice
Questo codice definisce una classe statica chiamata "Piramide" con due metodi statici all'interno: "Piani" e "Rimanenti".

Il metodo "Piani" prende un intero "mattoni" come parametro, che rappresenta il numero di mattoni di pietra disponibili per costruire la piramide, e restituisce un intero che rappresenta il numero di piani massimo che è possibile costruire con il numero di mattoni disponibili.

Il metodo utilizza un ciclo "while" per incrementare il valore di "piani" finché è possibile aggiungere un piano con il numero di mattoni disponibili. La condizione del ciclo "while" verifica che il numero di mattoni disponibili sia maggiore o uguale al quadrato dell'area del piano successivo, che ha una lunghezza laterale inferiore di due rispetto al piano sottostante.

All'interno del ciclo "while", il valore di "piani" viene incrementato di uno e il numero di mattoni utilizzati viene sottratto dalla quantità di mattoni disponibili. Questo viene fatto utilizzando la formula (2 * piani - 1) * (2 * piani - 1) per calcolare il numero di mattoni utilizzati per costruire il piano corrente.

Il metodo "Rimanenti" prende un intero "mattoni" come parametro e restituisce un intero che rappresenta il numero di mattoni rimanenti dopo la costruzione della piramide.

Il metodo utilizza il metodo "Piani" per calcolare il numero di piani massimo che è possibile costruire con il numero di mattoni disponibili. Successivamente, utilizza un ciclo "for" per calcolare il numero di mattoni utilizzati per costruire tutti i piani costruiti, sommandoli alla variabile "mattoniUtilizzati". Alla fine, il metodo restituisce la differenza tra il numero di mattoni disponibili e il numero di mattoni utilizzati.
