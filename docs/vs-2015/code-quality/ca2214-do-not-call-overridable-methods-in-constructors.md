---
title: 'CA2214: non chiamare metodi sottoponibili a override nei costruttori | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662902"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Non chiamare metodi sottoponibili a override nei costruttori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il costruttore di un tipo non sealed chiama un metodo virtuale definito nella relativa classe.

## <a name="rule-description"></a>Descrizione della regola
 Quando viene chiamato un metodo virtuale, il tipo effettivo che esegue il metodo non viene selezionato fino alla fase di esecuzione. Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non sia stato eseguito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, non chiamare i metodi virtuali di un tipo all'interno dei costruttori del tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Il costruttore deve essere riprogettato per eliminare la chiamata al metodo virtuale.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato l'effetto della violazione di questa regola. L'applicazione di test crea un'istanza di `DerivedType`, che determina l'esecuzione del costruttore della relativa classe di base (`BadlyConstructedType`). il costruttore di `BadlyConstructedType` chiama erroneamente il metodo virtuale `DoSomething`. Come illustrato nell'output, `DerivedType.DoSomething()` viene eseguito ed esegue questa operazione prima che venga eseguito il costruttore di `DerivedType`.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Questo esempio produce il seguente output:

 **Chiamata a ctor di base.** 
**DoSomething derivato viene chiamato inizializzato? Nessun** 
 la**chiamata a ctor derivato.**
