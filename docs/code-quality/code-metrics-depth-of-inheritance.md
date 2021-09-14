---
title: Metriche del codice - Profondità dell'ereditarietà
ms.date: 1/8/2021
description: Informazioni sulla metrica di ereditarietà per le metriche del codice in Visual Studio.
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: c08a35a622eeb30a51b4dea2ab4914b0105b01cd
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126632064"
---
# <a name="code-metrics---depth-of-inheritance-dit"></a>Metriche del codice - Profondità dell'ereditarietà (DIT)

Questo articolo illustra una delle metriche progettate in modo specifico per l'analisi orientata agli oggetti: Profondità dell'ereditarietà. La profondità dell'ereditarietà, detta anche profondità dell'albero di ereditarietà (DIT), è definita come "la lunghezza massima dal nodo alla radice dell'albero" [CK.](#ck) È possibile vedere questo esempio con un semplice esempio. Creare un nuovo progetto libreria di classi e, prima di scrivere codice, calcolare le metriche del codice scegliendo Analizza > Calcola metriche **codice per la soluzione**.

![Esempio di profondità dell'ereditarietà 1](media/depth-of-inheritance-example-1.png)

Poiché tutte le classi ereditano da `System.Object` , la profondità è attualmente 1. Se si eredita da questa classe ed esamina la nuova classe, è possibile visualizzare il risultato:

![Esempio di profondità dell'ereditarietà 2](media/depth-of-inheritance-example-2.png)

Si noti che più basso è il nodo nell'albero ( `Class2` in questo caso), maggiore è la profondità dell'ereditarietà. È possibile continuare a creare elementi figlio e aumentare il livello di profondità desiderato.

## <a name="assumptions"></a>Presupposti

La profondità dell'ereditarietà è basata su tre presupposti [fondamentali:](#ck)

1. Più è profonda una classe nella gerarchia, maggiore è il numero di metodi che probabilmente erediterà, il che rende più difficile stimarne il comportamento.

2. Gli alberi più profondi comportano una maggiore complessità di progettazione poiché sono coinvolti più classi e metodi.

3. Le classi più profonde nell'albero hanno un potenziale maggiore per il riutilizzo dei metodi ereditati.

I presupposti 1 e 2 indicano che avere un numero più elevato per la profondità non è valido. Se è il punto in cui è terminata, si sarebbe in buona forma; Tuttavia, il presupposto 3 indica che un numero più elevato per la profondità è valido per il potenziale riutilizzo del codice.

## <a name="analysis"></a>Analisi

Ecco come si legge la metrica di profondità:

- Numero basso per la profondità

  Un numero basso per la profondità implica una minore complessità, ma anche la possibilità di un minor riutilizzo del codice tramite ereditarietà.

- Numero elevato per la profondità

  Un numero elevato di profondità implica un maggiore potenziale di riutilizzo del codice tramite ereditarietà, ma anche una maggiore complessità con una maggiore probabilità di errori nel codice.

## <a name="code-analysis"></a>Analisi codice

L'analisi del codice include una categoria di regole di manutenibilità. Per altre informazioni, vedere [Regole di manutenibilità](/dotnet/fundamentals/code-analysis/quality-rules/maintainability-warnings). Quando si usa l'analisi del codice legacy, il set di regole Extended Design Guideline contiene un'area di manutenibilità:

![Set di regole delle linee guida per la progettazione dell'ereditarietà](media/depth-of-inheritance-design-guidelines.png)

All'interno dell'area di manutenibilità è disponibile una regola per l'ereditarietà:

![Regola di manutenibilità di profondità dell'ereditarietà](media/depth-of-inheritance-maintainability-rule.png)

Questa regola elava un avviso quando la profondità dell'ereditarietà raggiunge 6 o superiore, quindi è una regola buona per evitare un'ereditarietà eccessiva. Per altre informazioni sulla regola, vedere [CA1501](/dotnet/fundamentals/code-analysis/quality-rules/ca1501).

## <a name="putting-it-all-together"></a>Mettere tutto insieme

I valori elevati per DIT significano che anche il potenziale di errori è elevato, i valori bassi riducono il potenziale di errori. I valori elevati per DIT indicano un maggiore potenziale di riutilizzo del codice tramite ereditarietà, i valori bassi suggeriscono meno riutilizzo del codice anche se l'ereditarietà da sfruttare. A causa della mancanza di dati sufficienti, non esiste uno standard attualmente accettato per i valori DIT. Anche gli studi effettuati di recente non hanno trovato dati sufficienti per determinare un numero valido che potrebbe essere usato come numero standard per questa metrica [Shatnawi.](#shatnawi) Anche se non esistono evidenze empiriche per supportarlo, diverse risorse suggeriscono che un DIT di circa 5 o 6 dovrebbe essere un limite massimo. Ad esempio, vedere [http://www.devx.com/architect/Article/45611](http://www.devx.com/architect/Article/45611) .

## <a name="citations"></a>Citazioni

### <a name="ck"></a>CK

Chidamber, S. R. & Kemerer, C. F. (1994). Suite di metriche per la progettazione orientata agli oggetti (transazioni IEEE per progettazione software, vol. 20, n. 6). Recuperato il 14 maggio 2011 dal sito Web dell'Università di Pittsburgh: [http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf](http://www.pitt.edu/~ckemerer/CK%20research%20papers/MetricForOOD_ChidamberKemerer94.pdf)

### <a name="krishnan"></a>Krishnan

Subramanyam, R. & Krishnan, M. S. (2003). Analisi empirica delle metriche CK per Object-Oriented complessità della progettazione: implicazioni per i difetti software (transazioni IEEE sulla progettazione software, vol. 29, n. 4). Recuperato il 14 maggio 2011, originariamente ottenuto dal sito Web di University of Massachusetts Dartshire [https://ieeexplore.ieee.org/abstract/document/1191795](https://ieeexplore.ieee.org/abstract/document/1191795)

### <a name="shatnawi"></a>Shatnawi

Shatnawi, R. (2010). Analisi quantitativa dei livelli di rischio accettabili delle metriche di Object-Oriented in Open-Source Systems (transazioni IEEE per la progettazione software, vol. 36, n. 2).