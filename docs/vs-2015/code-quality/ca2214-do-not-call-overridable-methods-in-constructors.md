---
title: 'CA2214: Non chiamare metodi sottoponibili a override nei costruttori | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0a2e107429bb48b2bf17a625e25866a19c7781b6
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964179"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Non chiamare metodi sottoponibili a override nei costruttori
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Il costruttore di un tipo unsealed chiama un metodo virtuale definito nella relativa classe.

## <a name="rule-description"></a>Descrizione della regola
 Quando viene chiamato un metodo virtuale, il tipo effettivo che esegue il metodo non è selezionato fino alla fase di esecuzione. Quando un costruttore chiama un metodo virtuale, è possibile che il costruttore per l'istanza che richiama il metodo non è stata eseguita.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, non chiamare metodi virtuali del tipo dall'interno di costruttori del tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Il costruttore deve essere riprogettato per eliminare la chiamata al metodo virtuale.

## <a name="example"></a>Esempio
 L'esempio seguente illustra l'effetto della violazione di questa regola. L'applicazione di test viene creata un'istanza di `DerivedType`, in modo che la classe di base (`BadlyConstructedType`) costruttore per l'esecuzione. `BadlyConstructedType`del costruttore chiama in modo non corretto del metodo virtuale `DoSomething`. Come illustrato nell'output, `DerivedType.DoSomething()` viene eseguito prima del `DerivedType`dell'esecuzione del costruttore.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Questo esempio produce il seguente output:

 **La chiamata a costruttore base.**
**DoSomething derivata viene chiamato - inizializzata? No**
**chiamare il metodo derivato ctor.**
