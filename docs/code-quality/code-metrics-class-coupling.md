---
title: Metriche del codice - Accoppiamento di classi
ms.date: 1/8/2021
description: Informazioni sulla metrica di accoppiamento della classe per le metriche del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0853b807d3287eb584e76d9640ac98f930edb1a7
ms.sourcegitcommit: cc66c898ce82f9f1159bd505647f315792cac9fc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2021
ms.locfileid: "109666809"
---
# <a name="code-metrics---class-coupling"></a>Metriche del codice - Accoppiamento di classi

L'accoppiamento di classi viene anche chiamato Coupling Between Objects (CBO) come originariamente definito [da CK94.](#ck94) In pratica, l'accoppiamento di classi è una misura del numero di classi utilizzate da una singola classe. Un numero elevato non è valido e un numero basso è in genere valido con questa metrica. L'accoppiamento di classi ha dimostrato di essere un predittore accurato degli errori software e recenti studi hanno dimostrato che un valore limite superiore pari a 9 è il valore [S2010](#s2010)più efficiente.

Secondo la documentazione Microsoft, l'accoppiamento di classi "misura l'accoppiamento a classi univoche tramite parametri, variabili locali, tipi restituiti, chiamate al metodo, istanze generiche o modello, classi di base, implementazioni di interfaccia, campi definiti su tipi esterni e decorazione di attributi. Una buona progettazione software impone che i tipi e i metodi debbano avere un'elevata coerenza e un accoppiamento basso. L'accoppiamento elevato indica una progettazione difficile da riutilizzare e mantenere a causa delle numerose interdipendenze su altri tipi."

I concetti di accoppiamento e di coerenza sono chiaramente correlati. Per mantenere questa discussione sull'argomento, non si apprendono più in profondità con la coerenza se non per fornire una breve definizione di [KKLS2000:](#kkls2000)

"La coerenza dei moduli è stata introdotta da Yourdon e Constantine come "quanto strettamente legati o correlati gli elementi interni di un modulo sono gli uni agli altri" [YC79.](#yc79) Un modulo ha una forte coerenza se rappresenta esattamente un'attività [...], e tutti i relativi elementi contribuiscono a questa singola attività. Descrivono la coerenza come un attributo di progettazione, anziché come codice, e un attributo che può essere usato per stimare la riutilizzabilità, la manutenibilità e la modificabilità."

## <a name="class-coupling-example"></a>Esempio di accoppiamento tra classi

Diamo un'occhiata all'accoppiamento delle classi in azione. Prima di tutto, creare una nuova applicazione console e creare una nuova classe denominata Person con alcune proprietà, quindi calcolare immediatamente le metriche del codice:

![Esempio di accoppiamento di classi 1](media/class-coupling-example-1.png)

Si noti che l'accoppiamento della classe è 0 perché questa classe non usa altre classi. Creare ora un'altra classe denominata PersonStuff con un metodo che crea un'istanza di Person e imposta i valori della proprietà. Calcolare di nuovo le metriche del codice:

![Esempio di accoppiamento di classi 2](media/class-coupling-example-2.png)

Vedere come sale il valore di accoppiamento della classe? Si noti anche che, indipendentemente dal numero di proprietà impostate, il valore di accoppiamento della classe è solo di 1 e non di un altro valore. L'accoppiamento di classi misura ogni classe una sola volta per questa metrica, indipendentemente dalla quantità usata. Inoltre, si può vedere che `DoSomething()` ha 1, ma il `PersonStuff()` costruttore, , ha 0 per il relativo valore? Attualmente nel costruttore non è presente codice che usa un'altra classe.

Cosa succede se si mette nel costruttore il codice che usa un'altra classe? Ecco cosa si ottiene:

![Esempio di accoppiamento di classi 3](media/class-coupling-example-3.png)

Ora il costruttore ha chiaramente il codice che usa un'altra classe e la metrica di accoppiamento della classe mostra questo fatto. Anche in questo caso, è possibile vedere che l'accoppiamento complessivo delle classi per è 1 ed è anche 1 per mostrare che viene usata una sola classe esterna indipendentemente dalla quantità di codice interno che la `PersonStuff()` `DoSomething()` usa.

Creare quindi un'altra nuova classe. Assegnare un nome a questa classe e creare alcune proprietà al suo interno:

![Esempio di accoppiamento di classi - Aggiungere una nuova classe](media/class-coupling-example-add-new-class.png)

Utilizzare ora la classe nel metodo `DoSomething()` all'interno della `PersonStuff` classe e calcolare nuovamente le metriche del codice:

![Esempio di accoppiamento di classi 4](media/class-coupling-example-4.png)

Come si può vedere, l'accoppiamento di classe per la classe PersonStuff arriva fino a 2 e, se si esegue il drill-down nella classe, si può vedere che il metodo contiene il maggior numero di accoppiamenti, ma il costruttore usa ancora solo `DoSomething()` 1 classe.  Usando queste metriche, è possibile visualizzare il numero massimo complessivo per una determinata classe ed eseguire il drill-down dei dettagli per ogni membro.

## <a name="the-magic-number"></a>Il numero magico

Come per la complessità ciclomatica, non esiste alcun limite adatto a tutte le organizzazioni. Tuttavia, [S2010](#s2010) indica che un limite di 9 è ottimale:

"Pertanto, si considerano i valori soglia [...] come il più efficace. Questi valori soglia (per un singolo membro) sono CBO = 9[...]." (aggiunta dell'enfasi)

## <a name="code-analysis"></a>Analisi codice

L'analisi del codice include una categoria di regole di manutenibilità. Per altre informazioni, vedere [Regole di manutenibilità](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Quando si usa l'analisi del codice legacy, il set di regole Extended Design Guideline contiene un'area di manutenibilità:

![Regole della guida alla progettazione estesa per l'accoppiamento di classi](media/class-coupling-extended-design-guideline-rules.png)

All'interno dell'area di manutenibilità è disponibile una regola per l'accoppiamento di classi:

![Regola di accoppiamento delle classi](media/class-coupling-maintainability-area-rules.png)

Questa regola elava un avviso quando l'accoppiamento della classe è eccessivo. Per altre informazioni, vedere [CA1506: Evitare un accoppiamento eccessivo tra classi](/dotnet/fundamentals/code-analysis/quality-rules/ca1506).

## <a name="citations"></a>Citazioni

### <a name="ck94"></a>CK94

Chidamber, S. R. & Kemerer, C. F. (1994). A Metrics Suite for Object Oriented Design (IEEE Transactions on Software Engineering, Vol. 20, No. 6). Recuperata il 14 maggio 2011 dal sito Web dell'Università di Lah: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="kkls2000"></a>KKLS2000

Kabaili, H., Keller, R.,Cupman, F. e Saint-Saint, G. (2000). Class Evase Revisited: An Empirical Study on Industrial Systems (Studio empirico sui sistemi industriali) (Proceedings of the Workshop on Quantitative Approaches in Object-Oriented Software Engineering). Recuperata il 20 maggio 2011 dal sito Web Di Montréal [http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf](http://www.iro.umontreal.ca/~sahraouh/qaoose/papers/Kabaili.pdf)

### <a name="sk2003"></a>SK2003

Subramanyam, R. & Krishnan, M. S. (2003). Analisi empirica delle metriche CK per Object-Oriented complessità della progettazione: implicazioni per i difetti del software (transazioni IEEE in ingegneria del software, Vol. 29, n. 4). Recuperata il 14 maggio 2011 dal sito Web della University of Campuss Dart site [http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf](http://moosehead.cis.umassd.edu/cis580/readings/OO_Design_Complexity_Metrics.pdf)

### <a name="s2010"></a>S2010

Shatnawi, R. (2010). A Quantitative Investigation of the Acceptable Risk Levels of Object-Oriented Metrics in Open-Source Systems (IEEE Transactions on Software Engineering, Vol. 36, No. 2).

### <a name="yc79"></a>YC79

Edward Yourdon e Edward L. Constantine. Struttura strutturata. Prentice Hall, Englewood Clubs, N.J., 1979.