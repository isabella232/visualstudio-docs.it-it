---
title: 'CA2108: Controllare la sicurezza dichiarativa sui tipi di valore | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f6a17bf57f00923cfd31bd477f211ba66169672a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65687360"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Controllare la sicurezza dichiarativa sui tipi di valori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un tipo valore pubblico o protetto è protetto da un [dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oppure [linking](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descrizione della regola
 I tipi di valore sono allocati e inizializzati dai relativi costruttori predefiniti prima di eseguire altri costruttori. Se un tipo di valore è protetto da Demand o LinkDemand, e il chiamante non dispone di autorizzazioni per il controllo di sicurezza, un costruttore diverso da quello predefinito avrà esito negativo e verrà generata un'eccezione di sicurezza. Il tipo di valore non viene deallocato; rimarrà nello stato impostato dal costruttore predefinito. Non presupporre che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 È possibile correggere una violazione di questa regola a meno che non si rimuove il controllo di sicurezza dal tipo e controlli di sicurezza a livello di metodo di utilizzo al suo posto. Si noti che la correzione della violazione in questo modo non impedirà i chiamanti con autorizzazioni non adeguate dal recupero delle istanze del tipo di valore. È necessario assicurarsi che un'istanza del tipo di valore, nello stato predefinito, non espone informazioni riservate e non può essere utilizzata in modo dannoso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Se un chiamante qualsiasi possibile ottenere le istanze del tipo di valore nello stato predefinito senza causare una minaccia alla sicurezza, è possibile eliminare un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente mostra una libreria che contiene un tipo di valore che viola la regola. Si noti che il `StructureManager` tipo presuppone che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione seguente illustra punti deboli della libreria.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Questo esempio produce il seguente output:

 **Costruttore personalizzato struttura: Richiesta non riuscita.**
**Nuovi valori SecuredTypeStructure 100 100**
**nuovi valori SecuredTypeStructure 200 200**
## <a name="see-also"></a>Vedere anche
 [Le richieste di collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
