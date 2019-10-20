---
title: 'CA2108: controllare la sicurezza dichiarativa sui tipi valore | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a05b7098d75d368f893b2504f7663675611bc0ce
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658717"
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
 Un tipo di valore pubblico o protetto è protetto da una richiesta di [dati e di modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) o [collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d).

## <a name="rule-description"></a>Descrizione della regola
 I tipi di valore vengono allocati e inizializzati dai relativi costruttori predefiniti prima dell'esecuzione di altri costruttori. Se un tipo di valore è protetto da una richiesta o da LinkDemand e il chiamante non dispone di autorizzazioni che soddisfano il controllo di sicurezza, qualsiasi costruttore diverso da quello predefinito avrà esito negativo e verrà generata un'eccezione di sicurezza. Il tipo di valore non è deallocato; viene lasciato nello stato impostato dal costruttore predefinito. Non presupporre che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Non è possibile correggere una violazione di questa regola a meno che non si rimuova il controllo di sicurezza dal tipo e si usino i controlli di sicurezza a livello di metodo al suo posto. Si noti che la correzione della violazione in questo modo non impedisce ai chiamanti con autorizzazioni non adeguate di ottenere istanze del tipo di valore. È necessario assicurarsi che un'istanza del tipo di valore, nello stato predefinito, non esponga informazioni riservate e non possa essere utilizzata in modo dannoso.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se un chiamante può ottenere istanze del tipo di valore nello stato predefinito senza rappresentare una minaccia per la sicurezza.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una libreria contenente un tipo di valore che viola questa regola. Si noti che il tipo di `StructureManager` presuppone che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Esempio
 Nell'applicazione seguente viene illustrata la debolezza della libreria.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Questo esempio produce il seguente output:

 **Costruttore personalizzato della struttura: richiesta non riuscita.** 
**nuovi valori SecuredTypeStructure 100 100** 
**nuovi valori SecuredTypeStructure 200 200**
## <a name="see-also"></a>Vedere anche
 [Collegamento](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [di dati e modellazione](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) delle richieste
