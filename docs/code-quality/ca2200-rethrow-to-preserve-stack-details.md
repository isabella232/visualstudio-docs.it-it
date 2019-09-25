---
title: 'CA2200: Eseguire il rethrow per mantenere i dettagli dello stack'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- RethrowToPreserveStackDetails
- CA2200
helpviewer_keywords:
- CA2200
- RethrowToPreserveStackDetails
ms.assetid: 046e1b98-c4dc-4515-874f-9c0de2285621
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 5cf7fc6e31b9250392fc3ea447a5b91225640a50
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71231901"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Eseguire il rethrow per mantenere i dettagli dello stack

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft.Usage|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa

Viene nuovamente generata un'eccezione e l'eccezione viene specificata in modo esplicito nell' `throw` istruzione.

## <a name="rule-description"></a>Descrizione della regola

Una volta generata un'eccezione, parte delle informazioni che contiene è la traccia dello stack. La traccia dello stack è un elenco della gerarchia di chiamata del metodo che inizia con il metodo che genera l'eccezione e termina con il metodo che rileva l'eccezione. Se un'eccezione viene generata di nuovo specificando l'eccezione nell' `throw` istruzione, l'analisi dello stack viene riavviata nel metodo corrente e l'elenco di chiamate al metodo tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso. Per memorizzare le informazioni originali della traccia dello stack con l'eccezione, `throw` utilizzare l'istruzione senza specificare l'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, generare nuovamente l'eccezione senza specificare in modo esplicito l'eccezione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo `CatchAndRethrowExplicitly`,, che viola la regola e un metodo, `CatchAndRethrowImplicitly`, che soddisfa la regola.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]