---
title: 'CA2122: Non esporre in modo indiretto metodi con richieste di collegamento'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6850cee67a0dfed4b386eef5ed7cb021d3c76a4d
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71232516"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Non esporre in modo indiretto metodi con richieste di collegamento

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
Un membro pubblico o protetto presenta [richieste di collegamento](/dotnet/framework/misc/link-demands) e viene chiamato da un membro che non esegue alcun controllo di sicurezza.

## <a name="rule-description"></a>Descrizione della regola
Una richiesta di collegamento controlla esclusivamente le autorizzazioni del chiamante immediato. Se un membro `X` non esegue richieste di sicurezza dei chiamanti e chiama il codice protetto da una richiesta di collegamento, un chiamante senza l'autorizzazione necessaria può `X` utilizzare per accedere al membro protetto.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Aggiungere i dati di sicurezza [e la modellazione](/dotnet/framework/data/index) o la richiesta di collegamento al membro in modo che non fornisca più l'accesso non sicuro al membro protetto da richiesta di collegamento.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Per eliminare in modo sicuro un avviso da questa regola, è necessario assicurarsi che il codice non conceda ai chiamanti l'accesso a operazioni o risorse che possono essere utilizzate in modo distruttivo.

## <a name="example-1"></a>Esempio 1
Negli esempi seguenti viene illustrata una libreria che viola la regola e un'applicazione che dimostra la debolezza della libreria. La libreria di esempio fornisce due metodi che insieme violano la regola. Il `EnvironmentSetting` metodo è protetto da una richiesta di collegamento per l'accesso illimitato alle variabili di ambiente. Il `DomainInformation` metodo non esegue alcuna richiesta di sicurezza dei chiamanti prima `EnvironmentSetting`di chiamare.

[!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_1.cs)]

## <a name="example-2"></a>Esempio 2
L'applicazione seguente chiama il membro della libreria non protetta.

[!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../code-quality/codesnippet/CSharp/ca2122-do-not-indirectly-expose-methods-with-link-demands_2.cs)]

Questo esempio produce il seguente output:

```txt
*Value from unsecured member: seattle.corp.contoso.com
```

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)
- [Dati e modellazione](/dotnet/framework/data/index)