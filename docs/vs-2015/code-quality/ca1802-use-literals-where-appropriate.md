---
title: 'CA1802: Utilizza valori letterali dove appropriato | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseLiteralsWhereAppropriate
- CA1802
helpviewer_keywords:
- UseLiteralsWhereAppropriate
- CA1802
ms.assetid: 2515e4cd-9e61-486d-b067-58ba1a743ce4
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 25b9c521d55b16cef885c50138bff84c3000e1b3
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49940086"
---
# <a name="ca1802-use-literals-where-appropriate"></a>CA1802: Utilizza valori letterali dove appropriato
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseLiteralsWhereAppropriate|
|CheckId|CA1802|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un campo viene dichiarato `static` e `readonly` (`Shared` e `ReadOnly` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) e viene inizializzata con un valore calcolabile in fase di compilazione.

## <a name="rule-description"></a>Descrizione della regola
 Il valore di un `static``readonly` campo viene calcolato in fase di esecuzione quando viene chiamato il costruttore statico per il tipo dichiarante. Se il `static``readonly` campo viene inizializzato quando viene dichiarata e un costruttore statico non è dichiarato in modo esplicito, il compilatore genera un costruttore statico per inizializzare il campo.

 Il valore di una `const` campo viene calcolato in fase di compilazione e archiviato nei metadati, cosa che aumenta le prestazioni di runtime se confrontata a una `static``readonly` campo.

 Poiché il valore assegnato al campo di destinazione è calcolabile in fase di compilazione, modificare la dichiarazione in un `const` campo in modo che il valore viene calcolato in fase di compilazione anziché in fase di esecuzione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire il `static` e `readonly` modificatori con i `const` modificatore.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È opportuno eliminare un avviso da questa regola, o disabilitare la regola, se non riguarda le prestazioni.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `UseReadOnly`, che viola la regola e un tipo, `UseConstant`, che soddisfa la regola.

 [!code-csharp[FxCop.Performance.UseLiterals#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/cs/FxCop.Performance.UseLiterals.cs#1)]
 [!code-vb[FxCop.Performance.UseLiterals#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UseLiterals/vb/FxCop.Performance.UseLiterals.vb#1)]



