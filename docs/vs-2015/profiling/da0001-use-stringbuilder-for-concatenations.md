---
title: 'DA0001: Utilizzare StringBuilder per le concatenazioni | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.DA0001
- vs.performance.rules.DAUseStringBuilder
- vs.performance.1
- vs.performance.rules.DA0001
ms.assetid: a7cc7613-ad5f-48c8-bd2b-56372cc12dfc
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5e2e52b0688f69fd154425887077c40fc3e6c265
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531404"
---
# <a name="da0001-use-stringbuilder-for-concatenations"></a>DA0001: Utilizzare StringBuilder per le concatenazioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio, vedere [DA0001: usare StringBuilder per le concatenazioni](/visualstudio/profiling/da0001-use-stringbuilder-for-concatenations).  
  
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
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilo di campionamento. Trovare le sezioni del programma che fanno maggior uso della concatenazione di stringhe. Usare la classe StringBuilder per le modifiche di stringa complesse, comprese le operazioni frequenti di concatenazione di stringhe.  
  
 Per altre informazioni sull'uso delle stringhe, vedere la sezione [String Operations](https://msdn.microsoft.com/library/ms998547.aspx#scalenetchapt05_topic26) (Operazioni sulle stringhe) in [Chapter 5 - Improving Managed Code Performance](https://msdn.microsoft.com/library/ms998547.aspx) (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nella libreria Microsoft Patterns and Practices.
