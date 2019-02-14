---
title: 'DA0012: Uso elevato della reflection | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.performance.rules.DAReflection
- vs.performance.12
- vs.performance.rules.DA0012
- vs.performance.DA0011
ms.assetid: c92a1d76-21fa-426e-8b1b-a3c08e9bcbca
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ae0f361d4bbfe48b3133e50c360f66387d555814
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54770773"
---
# <a name="da0012-significant-amount-of-reflection"></a>DA0012: Utilizzo elevato della reflection
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Id regola | DA0012 |  
| Categoria di |. Utilizzo di NET Framework |  
| Metodi di profilatura | Campionamento |  
| Messaggio | Si usi la Reflection in modo eccessivo. L'operazione è dispendiosa.  
| Tipo di regola | Avviso |  
  
## <a name="cause"></a>Causa  
 Le chiamate ai metodi System.Reflection, ad esempio InvokeMember e GetMember, o ai metodi Type, ad esempio MemberInvoke, costituiscono una percentuale significativa dei dati di profilatura. Quando è possibile, è consigliabile sostituire questi metodi con associazione anticipata ai metodi di assembly dipendenti.  
  
## <a name="rule-description"></a>Descrizione della regola  
 La reflection è una funzionalità flessibile di .NET Framework che può essere usata per eseguire l'associazione tardiva dell'applicazione a un assembly di runtime dipendente oppure per creare ed eseguire dinamicamente nuovi tipi durante il runtime. Tuttavia, queste tecniche possono ridurre le prestazioni se vengono usate frequentemente o chiamate in cicli ridotti.  
  
 Per altre informazioni, vedere la sezione [Reflection and Late Binding](http://go.microsoft.com/fwlink/?LinkId=177826) (Reflection e associazione tardiva) in Chapter 5 - Improving Managed Code Performance (Capitolo 5 - Miglioramento delle prestazioni del codice gestito) nel volume Improving .NET Application Performance and Scalability (Miglioramento delle prestazioni e della scalabilità delle applicazioni .NET) della libreria Microsoft Patterns and Practices in MSDN.  
  
## <a name="how-to-investigate-a-warning"></a>Come esaminare un avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare alla [visualizzazione Dettagli funzione](../profiling/function-details-view.md) dei dati di profilatura. Esaminare le funzioni chiamanti del metodo System.Type o System.Reflection per trovare le sezioni del programma che fanno maggior uso delle API Reflection di .NET. Evitare di usare metodi che restituiscono metadati. Quando le prestazioni dell'applicazione sono di importanza fondamentale potrebbe essere necessario evitare l'uso dell'associazione tardiva e la creazione dinamica di tipi durante il runtime.
