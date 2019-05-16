---
title: 'CA2122: Non esporre in modo indiretto metodi con richieste di collegamento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e0b173378194c099b2014093104f814f3454843d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687266"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Non esporre in modo indiretto metodi con richieste di collegamento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un membro pubblico o protetto ha un [richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) e viene chiamato da un membro che non esegue controlli di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
 Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato. Se un membro `X` non effettua richieste alcuna sicurezza dei relativi chiamanti e chiamate di codice protetto da una richiesta di collegamento, un chiamante senza l'autorizzazione necessaria possa usare `X` per accedere al membro protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Aggiungere una protezione [dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o richiesta di collegamento per il membro in modo che non fornisca accesso non protetto non è più al membro protetto dalla richiesta di collegamento.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non concede i chiamanti accesso a operazioni o risorse che possono essere usate in modo distruttivo.

## <a name="example"></a>Esempio
 Gli esempi seguenti mostrano una libreria che viola la regola e un'applicazione che illustra i punti deboli della libreria. La libreria di esempio fornisce due metodi che insieme violano la regola. Il `EnvironmentSetting` metodo è protetto da una richiesta di collegamento per l'accesso illimitato alle variabili di ambiente. Il `DomainInformation` metodo non rende SecurityDemand dei chiamanti prima di chiamare `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Esempio
 La seguente applicazione chiama il membro della libreria non protetto.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Questo esempio produce il seguente output:

 **Valore del membro non protetta: Seattle**
## <a name="see-also"></a>Vedere anche
 [Linee guida per la generazione di codice sicuro](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [collegarle](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
