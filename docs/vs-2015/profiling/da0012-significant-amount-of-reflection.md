---
title: 'DA0012: Uso elevato della reflection | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 458f1bc74d8660e640139bff2f379a66eafa2919
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525821"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Utilizzo elevato della reflection
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [DA0012: quantità significativa di Reflection](https://docs.microsoft.com/visualstudio/profiling/da0012-significant-amount-of-reflection).  
  
Id regola | DA0012 |  
| Categoria di |. Utilizzo di NET Framework |  
| Metodi di profilatura | Campionamento |  
| Messaggio | Si usi la Reflection in modo eccessivo. È un'operazione costosa. |  
| Tipo di regola | Avviso |  
  
## <a name="cause"></a>Causa  
 Le chiamate ai metodi System.Reflection, ad esempio InvokeMember e GetMember, o ai metodi Type, ad esempio MemberInvoke, costituiscono una percentuale significativa dei dati di profilatura. Quando è possibile, è consigliabile sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.  
  
## <a name="rule-description"></a>Descrizione della regola  
 La reflection è una funzionalità flessibile di .NET Framework che può essere usata per eseguire l'associazione tardiva dell'applicazione a un assembly di runtime dipendente oppure per creare ed eseguire dinamicamente nuovi tipi durante il runtime. Tuttavia, queste tecniche possono ridurre le prestazioni se vengono usate frequentemente o chiamate in cicli ridotti.  
  
 Per altre informazioni, vedere la sezione [Reflection and Late Binding](http://go.microsoft.com/fwlink/?LinkId=177826) (Reflection e associazione tardiva) in Chapter 5 - Improving Managed Code Performance (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nel volume Improving .NET Application Performance and Scalability (Miglioramento delle prestazioni e della scalabilità delle applicazioni .NET) della libreria Microsoft Patterns and Practices in MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilatura. Esaminare le funzioni chiamanti del metodo System.Type o System.Reflection per trovare le sezioni del programma che fanno maggior uso delle API Reflection di .NET. Evitare di usare metodi che restituiscono metadati. Quando le prestazioni dell'applicazione sono di importanza fondamentale potrebbe essere necessario evitare l'uso dell'associazione tardiva e la creazione dinamica di tipi durante il runtime.



