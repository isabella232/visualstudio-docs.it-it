---
title: 'CA2108: Controllare la sicurezza dichiarativa sui tipi di valori'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb7795b2e1cdcdf8d32578396bb879f4573a45e8
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55003286"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Controllare la sicurezza dichiarativa sui tipi di valori

|||
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Category|Microsoft.Security|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Un tipo valore pubblico o protetto è protetto da un [dati e modellazione](/dotnet/framework/data/index) oppure [linking](/dotnet/framework/misc/link-demands).

## <a name="rule-description"></a>Descrizione della regola

I tipi di valore sono allocati e inizializzati dai relativi costruttori predefiniti prima di eseguire altri costruttori. Se un tipo di valore è protetto da Demand o LinkDemand, e il chiamante non dispone di autorizzazioni per il controllo di sicurezza, un costruttore diverso da quello predefinito avrà esito negativo e verrà generata un'eccezione di sicurezza. Il tipo di valore non viene deallocato; rimarrà nello stato impostato dal costruttore predefinito. Non presupporre che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

È possibile correggere una violazione di questa regola a meno che non si rimuove il controllo di sicurezza dal tipo e controlli di sicurezza a livello di metodo di utilizzo al suo posto. Correzione della violazione in questo modo non impedisce ai chiamanti con autorizzazioni non adeguate dal recupero delle istanze del tipo di valore. È necessario assicurarsi che un'istanza del tipo di valore, nello stato predefinito, non espone informazioni riservate e non può essere utilizzata in modo dannoso.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Se un chiamante qualsiasi possibile ottenere le istanze del tipo di valore nello stato predefinito senza causare una minaccia alla sicurezza, è possibile eliminare un avviso da questa regola.

## <a name="example-1"></a>Esempio 1

Nell'esempio seguente mostra una libreria che contiene un tipo di valore che viola la regola. Il `StructureManager` tipo presuppone che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione per creare o accedere all'istanza.

[!code-csharp[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]

## <a name="example-2"></a>Esempio 2

L'applicazione seguente illustra punti deboli della libreria.

[!code-csharp[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]

Questo esempio produce il seguente output:

```txt
Structure custom constructor: Request failed.
New values SecuredTypeStructure 100 100
New values SecuredTypeStructure 200 200
```

## <a name="see-also"></a>Vedere anche

- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)
