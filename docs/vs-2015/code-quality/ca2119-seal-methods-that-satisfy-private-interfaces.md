---
title: 'CA2119: Metodi Seal che soddisfano le interfacce private | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: af41fc5576cbcd56589680d99c0cd5c0dfd6e6f1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72664764"
---
# <a name="ca2119-seal-methods-that-satisfy-private-interfaces"></a>CA2119: Impostare come sealed i metodi che soddisfano interfacce private
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|SealMethodsThatSatisfyPrivateInterfaces|
|CheckId|CA2119|
|Category|Microsoft.Security|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un'interfaccia `internal` (`Friend` in Visual Basic).

## <a name="rule-description"></a>Descrizione della regola
 I metodi di interfaccia hanno accessibilità pubblica, che non possono essere modificati dal tipo di implementazione. Un'interfaccia interna crea un contratto che non deve essere implementato all'esterno dell'assembly che definisce l'interfaccia. Un tipo pubblico che implementa un metodo di un'interfaccia interna usando il modificatore `virtual` (`Overridable` in Visual Basic) consente di eseguire l'override del metodo da un tipo derivato esterno all'assembly. Se un secondo tipo nell'assembly di definizione chiama il metodo e prevede un contratto solo interno, il comportamento potrebbe essere compromesso quando, invece, viene eseguito il metodo sottoposto a override nell'assembly esterno. Ciò consente di creare una vulnerabilità di sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impedire che il metodo venga sottoposto a override all'esterno dell'assembly utilizzando uno dei seguenti elementi:

- Creare il tipo dichiarante `sealed` (`NotInheritable` in Visual Basic).

- Modificare l'accessibilità del tipo dichiarante in `internal` (`Friend` in Visual Basic).

- Rimuovere tutti i costruttori pubblici dal tipo dichiarante.

- Implementare il metodo senza usare il modificatore `virtual`.

- Implementare il metodo in modo esplicito.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se, dopo un'attenta revisione, non esistono problemi di sicurezza che potrebbero essere sfruttabili se il metodo viene sottoposto a override all'esterno dell'assembly.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `BaseImplementation`, che viola questa regola.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene sfruttata l'implementazione del metodo virtuale dell'esempio precedente.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Interfacce](https://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [Interfacce](https://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)
