---
title: Metriche del codice-accoppiamento della classe
ms.date: 1/8/2021
description: Informazioni sulla metrica di accoppiamento della classe per la metrica del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: db1308843cb3c4fe8fb0a4aa32300e545e5e3a7c
ms.sourcegitcommit: b1f7e7d7a0550d5c6f46adff3bddd44bc1d6ee1c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/11/2021
ms.locfileid: "98069627"
---
# <a name="code-metrics---class-coupling"></a>Metriche del codice-accoppiamento della classe

L'accoppiamento tra le classi viene inoltre eseguito in base al nome abbinato tra oggetti (linea di base) come originariamente definito da [CK94](#ck94). Fondamentalmente, l'accoppiamento di classi è una misura del numero di classi utilizzate da una singola classe. Un numero elevato non è valido e un numero basso è generalmente valido con questa metrica. L'accoppiamento tra le classi è stato indicato come un predittore accurato di errori software e negli studi recenti è stato dimostrato che un valore limite superiore pari a 9 è il [S2010](#s2010)più efficiente.

Secondo la documentazione Microsoft, l'accoppiamento delle classi "misura l'accoppiamento a classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, creazioni di istanze generiche o di modello, classi base, implementazioni di interfacce, campi definiti su tipi esterni e decorazione di attributi. Una buona progettazione software impone che i tipi e i metodi abbiano una coesione elevata e un accoppiamento basso. Un accoppiamento elevato indica una progettazione difficile da riutilizzare e gestire a causa delle numerose interdipendenze di altri tipi ".

I concetti di accoppiamento e coesione sono chiaramente correlati. Per tener conto di questa discussione, non verrà approfondita la coesione, oltre a fornire una breve definizione da [KKLS2000](#kkls2000):

"La coesione del modulo è stata introdotta da Yourdon e da Constantine come" il modo in cui gli elementi interni di un modulo sono strettamente associati o correlati " [YC79](#yc79)". Un modulo ha una solida coesione se rappresenta esattamente un'attività [...] e tutti i relativi elementi contribuiscono a questa singola attività. Descrivono la coesione come un attributo di progettazione, anziché codice, e un attributo che può essere usato per stimare la riusabilità, la gestibilità e la modificabilità ".

## <a name="class-coupling-example"></a>Esempio di accoppiamento della classe

Esaminiamo l'accoppiamento della classe in azione. Prima di tutto, creare una nuova applicazione console e creare una nuova classe denominata Person con alcune proprietà, quindi calcolare immediatamente la metrica del codice:

![Esempio di accoppiamento della classe 1](media/class-coupling-example-1.png)

Si noti che l'accoppiamento della classe è 0 perché questa classe non usa altre classi. A questo punto, creare un'altra classe denominata PersonStuff con un metodo che crea un'istanza di Person e imposta i valori della proprietà. Calcolare nuovamente la metrica del codice:

![Esempio di accoppiamento della classe 2](media/class-coupling-example-2.png)

Scopri come viene visualizzato il valore di accoppiamento della classe? Si noti anche che, indipendentemente dal numero di proprietà impostate, il valore di accoppiamento della classe viene semplicemente impostato su 1 e non su un altro valore. L'accoppiamento della classe misura ogni classe una sola volta per questa metrica indipendentemente dalla quantità utilizzata. Inoltre, è possibile vedere che `DoSomething()` ha 1 ma il costruttore, `PersonStuff()` , ha un valore 0 per il relativo valore? Attualmente non è presente alcun codice nel costruttore che usa un'altra classe.

Cosa accade se si inserisce il codice nel costruttore che ha usato un'altra classe? Ecco cosa si ottiene:

![Esempio di accoppiamento della classe 3](media/class-coupling-example-3.png)

A questo punto, il costruttore dispone chiaramente di codice che usa un'altra classe e la metrica di accoppiamento della classe ne mostra questo fatto. Anche in questo caso, è possibile osservare che l'accoppiamento generale della classe per `PersonStuff()` è 1 ed `DoSomething()` è anche 1 per indicare che è in uso una sola classe esterna indipendentemente dalla quantità di codice interno utilizzata.

Successivamente, creare un'altra nuova classe. Assegnare a questa classe un nome e creare alcune proprietà al suo interno:

![Esempio di accoppiamento della classe-Aggiungi nuova classe](media/class-coupling-example-add-new-class.png)

Utilizzare ora la classe nel `DoSomething()` metodo all'interno della `PersonStuff` classe e calcolare nuovamente la metrica del codice:

![Esempio di accoppiamento della classe 4](media/class-coupling-example-4.png)

Come si può notare, l'accoppiamento della classe per la classe PersonStuff passa a 2 e, se si esegue il drill-through della classe, è possibile osservare che il `DoSomething()` metodo ha il massimo accoppiamento, ma il costruttore usa ancora una classe.  Usando queste metriche, è possibile visualizzare il numero massimo complessivo per una determinata classe ed eseguire il drill-down nei dettagli in base ai singoli membri.

## <a name="the-magic-number"></a>Numero magico

Come per la complessità di ciclomatica, non esiste alcun limite che soddisfi tutte le organizzazioni. Tuttavia, [S2010](#s2010) indica che un limite di 9 è ottimale:

"Consideriamo pertanto i valori di soglia [...] come il più efficace. Questi valori di soglia (per un singolo membro) sono di 9 [...] ". (enfasi aggiunta)

## <a name="code-analysis"></a>Analisi codice

L'analisi del codice include una categoria di regole di gestibilità. Per altre informazioni, vedere [regole di gestibilità](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Quando si usa l'analisi del codice legacy, il set di regole delle linee guida per la progettazione estesa contiene un'area di manutenzione:

![Regole delle linee guida di progettazione estese delle classi](media/class-coupling-extended-design-guideline-rules.png)

All'interno dell'area di gestione è una regola per l'accoppiamento della classe:

![Regola di accoppiamento della classe](media/class-coupling-maintainability-area-rules.png)

Questa regola genera un avviso quando l'accoppiamento della classe è eccessivo. Per altre informazioni, vedere [CA1506: evitare un accoppiamento di classe eccessiva](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

Per una descrizione di questa regola, vedere il post di Blog relativo all'analisi del codice archiviato: [metrica del codice come criterio di archiviazione](/archive/blogs/codeanalysis/code-metrics-as-check-in-policy) e la descrizione della soglia di *avviso sopra 80 per la classe e sopra 30 per un metodo*.  Questi valori sembrano eccessivamente elevati, ma almeno forniscono un limite superiore estremo. Se si raggiunge questo avviso, qualcosa è quasi certamente errato.

## <a name="citations"></a>Citazioni

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). Una suite di metriche per la progettazione orientata a oggetti (transazioni IEEE su Software Engineering, vol. 20, no. 6). Recuperato il 14 maggio 2011, dal sito Web della University of Pittsburgh: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R., Lustt, F. e Saint-Denis, G. (2000). Coesione di classe rivisitata: uno studio empirico sui sistemi industriali (procedimenti del workshop sugli approcci quantitativi in Object-Oriented ingegneria del software). Recuperato il 20 maggio 2011, dal sito Web Université de Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Per l'&, R. Krishnan, M. S. (2003). Analisi empirica delle metriche CK per la complessità della progettazione Object-Oriented: implicazioni per i difetti software (transazioni IEEE sulla progettazione software, vol. 29, no. 4). Recuperato il 14 maggio 2011, dal sito Web della University of Massachusetts Dartmouth [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). Analisi quantitativa dei livelli di rischio accettabili di Object-Oriented metrica nei sistemi di Open-Source (transazioni IEEE sulla progettazione software, vol. 36, no. 2).

### <a name="yc79"></a>YC79

Edward Yourdon e Larry L. Constantine. Progettazione strutturata. Prentice Hall, Englewood Cliffs, NJ, 1979.