---
title: 'CA1061: Non nascondere metodi della classe base | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1061
- DoNotHideBaseClassMethods
helpviewer_keywords:
- DoNotHideBaseClassMethods
- CA1061
ms.assetid: 0bda9dc8-87b4-4038-ab9d-563298387466
caps.latest.revision: 11
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e932b2c948493c4703e8edd5edb37818e80f0253
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58967742"
---
# <a name="ca1061-do-not-hide-base-class-methods"></a>CA1061: Non nascondere i metodi di una classe base
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola.

 [!code-csharp[FxCop.Design.HideBaseMethod#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.HideBaseMethod/cs/FxCop.Design.HideBaseMethod.cs#1)]
