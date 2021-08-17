---
title: Metriche del codice - Complessità ciclomatica
ms.date: 5/7/2021
description: Informazioni sulla metrica di complessità ciclomatica per le metriche del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: b8de7119eb232afb904896cfedbbece9bbf2f8d5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122129974"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Metriche del codice - Complessità ciclomatica

Quando si lavora con le metriche del codice, uno degli elementi meno compresi sembra essere una complessità tematica. In sostanza, con complessità complessa, i numeri più alti sono negativi e i numeri inferiori sono buoni. È possibile usare la complessità ciclomatica per capire quanto può essere difficile testare, gestire o risolvere i problemi di un determinato codice, nonché un'indicazione della probabilità che il codice produca errori. A livello elevato, si determina il valore della complessità ciclomatica contando il numero di decisioni prese nel codice sorgente. In questo articolo si inizia con un semplice esempio di complessità ciclomatica per comprendere rapidamente il concetto, quindi si osservano alcune informazioni aggiuntive sull'utilizzo effettivo e sui limiti suggeriti. Infine, è presente una sezione di citazioni che può essere usata per approfondire questo argomento.

## <a name="example"></a>Esempio

La complessità ciclomatica è definita come misurazione della "quantità di logica decisionale in una funzione del codice sorgente" [NIST235](#nist235). In poche parole, più decisioni devono essere prese nel codice, più è complesso.

Vediamolo in azione. Creare una nuova applicazione console e calcolare immediatamente le metriche del codice andando ad Analizzare > **calcolare le metriche del codice per la soluzione**.

![Esempio di complessità ciclomatica 1](media/cyclomatic-complexity-example-1.png)

Si noti che la complessità ciclomatica è pari a 2 (il valore più basso possibile). Se si aggiunge codice non decisionale, si noti che la complessità non cambia:

![Esempio di complessità ciclomatica 2](media/cyclomatic-complexity-example-2.png)

Se si aggiunge una decisione, il valore di complessità ciclomatica sale di 1:

![Esempio di complessità ciclomatica 3](media/cyclomatic-complexity-example-3.png)

Quando si modifica l'istruzione if in un'istruzione switch con 4 decisioni da prendere, l'istruzione passa da 2 a 6 originale:

![Esempio di complessità ciclomatica 4](media/cyclomatic-complexity-example-4.png)

Si esamini una base di codice (ipotetica) più grande.

![Esempio di complessità ciclomatica 5](media/cyclomatic-complexity-example-5.png)

Si noti che la maggior parte degli elementi, mentre si esegue il drill-down nella classe Products_Related, ha un valore pari a 1, ma due hanno una complessità pari a 5. Di per sé, questo potrebbe non essere un problema, ma dato che la maggior parte degli altri membri ha un valore 1 nella stessa classe, è consigliabile esaminare in modo più da vicino questi due elementi e vedere cosa contiene. A tale scopo, fare clic con il pulsante destro del mouse sull'elemento e scegliere Vai al codice **sorgente** dal menu di scelta rapida. Esaminare in dettaglio `Product.set(Product)` :

![Esempio di complessità ciclomatica 6](media/cyclomatic-complexity-example-6.png)

Date tutte le istruzioni if, è possibile vedere perché la complessità tematica è a 5. A questo punto, è possibile decidere che si tratta di un livello accettabile di complessità oppure è possibile eseguire il refactoring per ridurne la complessità.

## <a name="the-magic-number"></a>Il numero magico

Come per molte metriche in questo settore, non esiste un limite esatto di complessità ciclomatica adatto a tutte le organizzazioni. Tuttavia, [NIST235](#nist235) indica che un limite di 10 è un buon punto di partenza:

"Il numero preciso da usare come limite, tuttavia, rimane piuttosto controverso. Il limite originale di 10, come proposto da McCabe, ha una prova di supporto significativa, ma sono stati usati anche limiti fino a 15. I limiti oltre 10 devono essere riservati ai progetti che presentano diversi vantaggi operativi rispetto ai progetti tipici, ad esempio personale esperto, progettazione formale, un linguaggio di programmazione moderno, programmazione strutturata, procedure dettagliate sul codice e un piano di test completo. In altre parole, un'organizzazione può scegliere un limite di complessità maggiore di 10, ma solo se è sicuro di sapere cosa sta facendo ed è disposto a dedicare il lavoro di test aggiuntivo richiesto dai moduli più complessi." [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Complessità ciclomatica e numeri di riga

La semplice analisi del numero di righe di codice è, nel migliore dei modi, un predittore molto ampio della qualità del codice. Esiste un'idea di base dell'idea che più righe di codice in una funzione sono presenti, più è probabile che si siano verificati errori. Tuttavia, quando si combina una complessità complessa complessa con righe di codice, si ha un quadro molto più chiaro del potenziale di errori.

Come descritto dal Software Assurance Technology Center (SATC) della NASA:

"Il SATC ha rilevato che la valutazione più efficace è una combinazione di dimensioni e complessità (ciclomatica). I moduli con una complessità elevata e dimensioni elevate tendono ad avere la più bassa affidabilità. Anche i moduli con dimensioni ridotte e complessità elevata sono un rischio di affidabilità perché tendono a essere codice molto complesso, difficile da modificare o modificare." [SATC](#satc)

## <a name="code-analysis"></a>Analisi codice

L'analisi del codice include una categoria di regole di manutenibilità. Per altre informazioni, vedere [Regole di manutenibilità.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Quando si usa l'analisi del codice legacy, il set di regole Linee guida per la progettazione estesa contiene un'area di manutenibilità:

![Set di regole linee guida per la progettazione di complessità ciclomatica](media/cyclomatic-complexity-design-guidelines.png)

All'interno dell'area di manutenibilità è disponibile una regola per la complessità:

![Regola di gestibilità della complessità ciclomatica](media/cyclomatic-complexity-maintainability-rule.png)

Questa regola elava un avviso quando la complessità ciclomatica raggiunge 25, in modo da evitare un'eccessiva complessità. Per altre informazioni sulla regola, vedere [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Mettere tutto insieme

La linea di fondo è che un numero di complessità elevato indica una maggiore probabilità di errori con maggiore tempo per la manutenzione e la risoluzione dei problemi. Esaminare in dettaglio le funzioni con un'elevata complessità e decidere se eseguire il refactoring per renderle meno complesse.

## <a name="citations"></a>Citazioni

### <a name="mccabe5"></a>MCCABE5

McCabe, T. e A. Watson (1994), Complessità del software (CrossTalk: The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Test strutturati: metodologia di test che usa la metrica di complessità ciclomatica (pubblicazione speciale NIST 500-235). Recuperato il 14 maggio 2011 dal sito Web McCabe Software: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., Hammer, T., Shaw, J. (1998). Metriche software e affidabilità (Proceedings of IEEE International Symposium on Software Reliability Engineering). Recuperato il 14 maggio 2011 dal sito Web della Penn State University: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)