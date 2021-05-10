---
title: Metriche del codice - Complessità tematica
ms.date: 5/7/2021
description: Informazioni sulla metrica di complessità tematica per le metriche del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1798b0faa1b0cf44ae490f5b27571e5466b82ca9
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2021
ms.locfileid: "109682689"
---
# <a name="code-metrics---cyclomatic-complexity"></a>Metriche del codice - Complessità tematica

Quando si lavora con le metriche del codice, uno degli elementi meno compresi sembra essere una complessità tematica. In sostanza, con la complessità tematica, i numeri più alti sono negativi e i numeri più bassi sono buoni. È possibile usare la complessità tematica per avere un'idea della complessità di un determinato codice da testare, gestire o risolvere, nonché per indicare la probabilità che il codice produca errori. A livello elevato, si determina il valore della complessità tematica contando il numero di decisioni prese nel codice sorgente. In questo articolo si inizia con un semplice esempio di complessità tematica per comprendere rapidamente il concetto, quindi si osservano alcune informazioni aggiuntive sull'utilizzo effettivo e sui limiti suggeriti. Infine, è presente una sezione di citazioni che può essere usata per approfondire questo argomento.

## <a name="example"></a>Esempio

La complessità tematica è definita come misurazione della "quantità di logica decisionale in una funzione del codice sorgente" [NIST235.](#nist235) In poche parole, più decisioni devono essere prese nel codice, più complesse saranno le decisioni.

Vediamolo in azione. Creare una nuova applicazione console e calcolare immediatamente le metriche del codice in Analizza > **calcolare le metriche del codice per la soluzione**.

![Esempio di complessità tematica 1](media/cyclomatic-complexity-example-1.png)

Si noti che la complessità tematica è pari a 2 (il valore più basso possibile). Se si aggiunge codice non decisionale, si noti che la complessità non cambia:

![Esempio di complessità tematica 2](media/cyclomatic-complexity-example-2.png)

Se si aggiunge una decisione, il valore di complessità tematica sale di 1:

![Esempio di complessità tematica 3](media/cyclomatic-complexity-example-3.png)

Quando si modifica l'istruzione if in un'istruzione switch con 4 decisioni da prendere, passa dalla versione originale 2 a quella 6:

![Esempio di complessità ciclomatica 4](media/cyclomatic-complexity-example-4.png)

Si esamini una base di codice (ipotetica) più grande.

![Esempio di complessità ciclomatica 5](media/cyclomatic-complexity-example-5.png)

Si noti che la maggior parte degli elementi, mentre si esegue il drill-down nella classe Products_Related, ha un valore pari a 1, ma alcuni di essi hanno una complessità pari a 5. Di per sé, questo potrebbe non essere un problema, ma dato che la maggior parte degli altri membri ha un valore 1 nella stessa classe, è consigliabile esaminare in modo più da vicino questi due elementi e vedere cosa contiene. A tale scopo, fare clic con il pulsante destro del mouse sull'elemento e scegliere Vai al codice **sorgente** dal menu di scelta rapida. Esaminare in dettaglio `Product.set(Product)` :

![Esempio di complessità ciclomatica 6](media/cyclomatic-complexity-example-6.png)

Date tutte le istruzioni if, è possibile vedere perché la complessità tematica è a 5. A questo punto, è possibile decidere che si tratta di un livello accettabile di complessità oppure è possibile eseguire il refactoring per ridurne la complessità.

## <a name="the-magic-number"></a>Il numero magico

Come per molte metriche in questo settore, non esiste un limite esatto di complessità ciclomatica adatto a tutte le organizzazioni. Tuttavia, [NIST235](#nist235) indica che un limite di 10 è un buon punto di partenza:

"Il numero preciso da usare come limite, tuttavia, rimane piuttosto controverso. Il limite originale di 10, come proposto da McCabe, presenta prove di supporto significative, ma sono stati usati anche limiti fino a 15. I limiti oltre 10 devono essere riservati ai progetti che presentano diversi vantaggi operativi rispetto ai progetti tipici, ad esempio personale esperto, progettazione formale, un linguaggio di programmazione moderno, programmazione strutturata, procedure dettagliate sul codice e un piano di test completo. In altre parole, un'organizzazione può scegliere un limite di complessità superiore a 10, ma solo se è sicuro di sapere cosa sta facendo ed è disposto a dedicare il lavoro di test aggiuntivo richiesto dai moduli più complessi." [NIST235](#nist235)

## <a name="cyclomatic-complexity-and-line-numbers"></a>Complessità ciclomatica e numeri di riga

La semplice analisi del numero di righe di codice è, nel migliore dei modi, un predittore molto ampio della qualità del codice. Esiste un'idea di base del fatto che maggiore è il numero di righe di codice in una funzione, maggiore è la probabilità che si siano verificati errori. Tuttavia, quando si combinano complessità tematiche con righe di codice, si ha un quadro molto più chiaro del potenziale di errori.

Come descritto dal Software Assurance Technology Center (SATC) della NASA:

"Il satc ha scoperto che la valutazione più efficace è una combinazione di dimensioni e complessità (tematica). I moduli con una complessità elevata e dimensioni elevate tendono ad avere l'affidabilità più bassa. I moduli con dimensioni ridotte e complessità elevata sono anche un rischio di affidabilità perché tendono a essere codice molto difficile da modificare." [SATC](#satc)

## <a name="code-analysis"></a>Analisi codice

L'analisi del codice include una categoria di regole di manutenibilità. Per altre informazioni, vedere [Regole di manutenibilità.](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings) Quando si usa l'analisi del codice legacy, il set di regole Linee guida per la progettazione estesa contiene un'area di manutenibilità:

![Set di regole delle linee guida per la progettazione della complessità tematica](media/cyclomatic-complexity-design-guidelines.png)

All'interno dell'area di manutenibilità è disponibile una regola per la complessità:

![Regola di gestibilità della complessità tematica](media/cyclomatic-complexity-maintainability-rule.png)

Questa regola elava un avviso quando la complessità tematica raggiunge 25, in modo da evitare una complessità eccessiva. Per altre informazioni sulla regola, vedere [CA1502](/dotnet/fundamentals/code-analysis/quality-rules/ca1502)

## <a name="putting-it-all-together"></a>Mettere tutto insieme

In ultima istanza, un numero di complessità elevato indica una maggiore probabilità di errori con maggiore tempo per la manutenzione e la risoluzione dei problemi. Esaminare in dettaglio tutte le funzioni con un'elevata complessità e decidere se eseguire il refactoring per renderle meno complesse.

## <a name="citations"></a>Citazioni

### <a name="mccabe5"></a>MCCABE5

McCabe, T. e A. Watson (1994), Complessità del software (CrossTalk: The Journal of Defense Software Engineering).

### <a name="nist235"></a>NIST235

Watson, A. H., & McCabe, T. J. (1996). Test strutturati: metodologia di test che usa la metrica di complessità ciclomatica (pubblicazione speciale NIST 500-235). Recuperato il 14 maggio 2011 dal sito Web McCabe Software: [http://www.mccabe.com/pdf/mccabe-nist235r.pdf](http://www.mccabe.com/pdf/mccabe-nist235r.pdf)

### <a name="satc"></a>SATC

Rosenberg, L., Hammer, T., Shaw, J. (1998). Metriche software e affidabilità (Proceedings of IEEE International Symposium on Software Reliability Engineering). Recuperato il 14 maggio 2011 dal sito Web della Penn State University: [http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.104.4041&rep=rep1&type=pdf)