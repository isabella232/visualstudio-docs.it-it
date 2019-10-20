---
title: 'CA1802: usare i valori letterali laddove appropriato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: bbcf83772a7a4031cf2e27abe7e8f4c08e21c11c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671519"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Utilizza valori letterali dove appropriato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un campo viene dichiarato `static` e `readonly` (`Shared` e `ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) e viene inizializzato con un valore calcolabile in fase di compilazione.

## <a name="rule-description"></a>Descrizione della regola
 Il valore di un campo `static``readonly` viene calcolato in fase di esecuzione quando viene chiamato il costruttore statico per il tipo dichiarante. Se il campo `static``readonly` viene inizializzato quando viene dichiarato e un costruttore statico non è dichiarato in modo esplicito, il compilatore genera un costruttore statico per inizializzare il campo.

 Il valore di un campo `const` viene calcolato in fase di compilazione e archiviato nei metadati, che aumenta le prestazioni di runtime quando viene confrontato con un campo di `static``readonly`.

 Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un campo `const` in modo che il valore venga calcolato in fase di compilazione anziché in fase di esecuzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire i modificatori `static` e `readonly` con il modificatore `const`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola o disabilitare la regola se le prestazioni non sono di alcun interesse.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `UseReadOnly`, che viola la regola e un tipo, `UseConstant`, che soddisfa la regola.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]
