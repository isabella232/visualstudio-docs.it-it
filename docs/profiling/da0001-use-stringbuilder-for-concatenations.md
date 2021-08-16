---
title: DA0001- Usare StringBuilder per le concatenazioni | Microsoft Docs
description: Le chiamate a System.String.Concat sono una percentuale significativa dei dati di profilatura. Provare a usare la classe System.Text.StringBuilder per costruire stringhe da più segmenti.
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: a2c142579e8006064767a4a95a3c8abc93b8860fddfc583d262a5d6547459a99
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121368825"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Utilizzare StringBuilder per le concatenazioni

|Elemento|valore|
|-|-|
|ID regola|DA0001|
|Category|Uso di .NET Framework|
|Metodi di profilatura|campionamento<br /><br /> Strumentazione|
|Message|Si consiglia di utilizzare StringBuilder per le concatenazioni di stringa.|
|Tipo di messaggio|Avviso|

## <a name="cause"></a>Causa
 Le chiamate a System.String.Concat sono una percentuale significativa dei dati di profilatura. Considerare la possibilità di usare la classe <xref:System.Text.StringBuilder> per costruire stringhe da più segmenti.

## <a name="rule-description"></a>Descrizione della regola
 Un oggetto <xref:System.String> non è modificabile. Pertanto, qualsiasi modifica alla stringa crea un nuovo oggetto stringa e la Garbage Collection dell'originale. Questo comportamento è lo stesso sia in caso di chiamata esplicita a String.Concat sia in caso di uso di operatori di concatenazione di stringhe, ad esempio + oppure +=. Le prestazioni del programma possono diminuire se questi metodi vengono chiamati con frequenza, ad esempio quando vengono aggiunti caratteri a una stringa in un ciclo ridotto.

 La classe StringBuilder è un oggetto modificabile e, a differenza di System. String, la maggior parte dei metodi di StringBuilder che modificano un'istanza della classe restituisce un riferimento a quella stessa istanza. È possibile inserire caratteri o aggiungere testo a un'istanza di StringBuilder e rimuovere o sostituire i caratteri nell'istanza senza dover allocare una nuova istanza ed eliminare l'istanza originale.

## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso
 Fare doppio clic sul messaggio nella finestra **Elenco errori** per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilo di campionamento. Trovare le sezioni del programma che fanno maggior uso della concatenazione di stringhe. Usare la classe StringBuilder per le modifiche di stringa complesse, comprese le operazioni frequenti di concatenazione di stringhe.

 Per altre informazioni sull'uso delle stringhe, vedere la sezione [String Operations](/previous-versions/msp-n-p/ff647790(v=pandp.10)#string-operations) (Operazioni sulle stringhe) in [Chapter 5 - Improving Managed Code Performance](/previous-versions/msp-n-p/ff647790(v=pandp.10)) (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nella libreria Microsoft Patterns and Practices.
