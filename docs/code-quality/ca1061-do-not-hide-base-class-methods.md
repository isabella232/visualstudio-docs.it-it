---
title: 'CA1061: Non nascondere metodi della classe base'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e0a6db369cea0e242ce5b2b6e169278b1bf17ea2
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928555"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Non nascondere metodi della classe base

|||
|-|-|
|TypeName|DoNotHideBaseClassMethods|
|CheckId|CA1061|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo derivato viene dichiarato un metodo con lo stesso nome e con lo stesso numero di parametri come uno dei relativi metodi di base; uno o più dei parametri sono un tipo di base del parametro corrispondente del metodo base; e tutti i parametri rimanenti sono tipi che sono identici ai parametri corrispondenti nel metodo di base.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo in un tipo di base è nascosto da un metodo denominato in modo identico in un tipo derivato durante la firma di parametro del metodo derivato differisce solo per i tipi che presentano una derivazione più debole rispetto ai tipi corrispondenti nella firma del parametro del metodo di base.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rimuovere o rinominare il metodo o modificare la firma di parametro in modo che il metodo non nasconde il metodo di base.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../code-quality/codesnippet/CSharp/ca1061-do-not-hide-base-class-methods_1.cs)]