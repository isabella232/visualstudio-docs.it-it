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
ms.openlocfilehash: 55c58f098616a5c3c2d6ad72f56e8eda51f689be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62796845"
---
# <a name="ca2200-rethrow-to-preserve-stack-details"></a>CA2200: Eseguire il rethrow per mantenere i dettagli dello stack

|||
|-|-|
|TypeName|RethrowToPreserveStackDetails|
|CheckId|CA2200|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa

Viene nuovamente generata un'eccezione e l'eccezione viene specificato in modo esplicito nel `throw` istruzione.

## <a name="rule-description"></a>Descrizione della regola

Una volta che viene generata un'eccezione, parte delle informazioni in essa contenute è l'analisi dello stack. L'analisi dello stack è un elenco della gerarchia di chiamata di metodo che inizia con il metodo che genera l'eccezione e termina con il metodo che intercetta l'eccezione. Se un'eccezione viene generata nuovamente specificando un'eccezione nel `throw` istruzione, l'analisi dello stack viene riavviato in corrispondenza del metodo corrente e l'elenco di chiamate al metodo tra il metodo originale che ha generato l'eccezione e il metodo corrente viene perso. Per mantenere le informazioni di traccia dello stack originale con l'eccezione, usare il `throw` istruzione senza specificare l'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Per correggere una violazione di questa regola, generare di nuovo l'eccezione senza specificare in modo esplicito l'eccezione.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio

Nell'esempio seguente viene illustrato un metodo, `CatchAndRethrowExplicitly`, che viola la regola e un metodo, `CatchAndRethrowImplicitly`, che soddisfa la regola.

[!code-csharp[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/CSharp/ca2200-rethrow-to-preserve-stack-details_1.cs)]
[!code-vb[FxCop.Usage.Rethrow#1](../code-quality/codesnippet/VisualBasic/ca2200-rethrow-to-preserve-stack-details_1.vb)]