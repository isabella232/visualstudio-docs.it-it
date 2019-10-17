---
title: 'CA1061: Non nascondere i metodi di una classe base'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e52360a68e0ffd4512ba991fd6f4939ebd245359
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72440667"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Non nascondere i metodi di una classe base

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Category|Microsoft. Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un tipo derivato dichiara un metodo con lo stesso nome e con lo stesso numero di parametri di uno dei relativi metodi di base; uno o più parametri è un tipo di base del parametro corrispondente nel metodo di base. e gli eventuali parametri rimanenti hanno tipi identici ai parametri corrispondenti nel metodo di base.

## <a name="rule-description"></a>Descrizione della regola
Un metodo in un tipo di base è nascosto da un metodo con nome identico in un tipo derivato quando la firma del parametro del metodo derivato differisce solo per i tipi che sono derivati in modo più debole rispetto ai tipi corrispondenti nella firma del parametro del metodo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, rimuovere o rinominare il metodo oppure modificare la firma del parametro in modo che il metodo non nasconda il metodo di base.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un metodo che viola la regola.

[!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]
