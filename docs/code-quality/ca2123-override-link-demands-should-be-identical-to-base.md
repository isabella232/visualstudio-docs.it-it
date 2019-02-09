---
title: 'CA2123: Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA2123
- OverrideLinkDemandsShouldBeIdenticalToBase
helpviewer_keywords:
- OverrideLinkDemandsShouldBeIdenticalToBase
- CA2123
ms.assetid: 4538ecd5-fc6f-4480-ab00-90b2ce4730db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 52959279bca5aa0f86722050f6118f64997a901d
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945300"
---
# <a name="ca2123-override-link-demands-should-be-identical-to-base"></a>CA2123: Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base

|||
|-|-|
|TypeName|OverrideLinkDemandsShouldBeIdenticalToBase|
|CheckId|CA2123|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico esegue l'override di un metodo o implementa un'interfaccia e non hanno gli stessi [richieste di collegamento](/dotnet/framework/misc/link-demands) dell'interfaccia o un metodo virtuale.

## <a name="rule-description"></a>Descrizione della regola
 Questa regola associa un metodo al relativo metodo di base che può essere un'interfaccia o un metodo virtuale in un altro tipo, quindi confronta le richieste di collegamento in ognuno. Se il metodo o il metodo di base dispone di una richiesta di collegamento e l'altra non avviene, viene segnalata una violazione.

 Se questa regola viene violata, un chiamante dannoso può ignorare la richiesta di collegamento chiamando semplicemente il metodo non sicuro.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, applicare la stessa richiesta di collegamento per il metodo di override o implementazione. Se questo non è possibile, contrassegnare il metodo con una richiesta completa oppure rimuovere completamente l'attributo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra vari le violazioni di questa regola.

 [!code-csharp[FxCop.Security.OverridesAndSecurity#1](../code-quality/codesnippet/CSharp/ca2123-override-link-demands-should-be-identical-to-base_1.cs)]

## <a name="see-also"></a>Vedere anche

- [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)
- [Richieste di collegamento](/dotnet/framework/misc/link-demands)