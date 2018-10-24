---
title: ': Ca2119 impostare i metodi che soddisfano interfacce private | Microsoft Docs'
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
- SealMethodsThatSatisfyPrivateInterfaces
- CA2119
helpviewer_keywords:
- CA2119
- SealMethodsThatSatisfyPrivateInterfaces
ms.assetid: 483d02e1-cfaf-4754-a98f-4116df0f3509
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c6d3e102cde1fc010f777006d629fa2d19add894
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825394"
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
 Un tipo pubblico ereditabile fornisce un'implementazione di metodo sottoponibile a override di un `internal` (`Friend` in Visual Basic) dell'interfaccia.

## <a name="rule-description"></a>Descrizione della regola
 I metodi di interfaccia avere accessibilità pubblica, non può essere modificato dal tipo di implementazione. Un'interfaccia interna consente di creare un contratto che non può essere implementato all'esterno dell'assembly che definisce l'interfaccia. Un tipo pubblico che implementa un metodo di un'interfaccia interna usando le `virtual` (`Overridable` in Visual Basic) modificatore consente al metodo da sottoporre a override da un tipo derivato è all'esterno dell'assembly. Se un secondo tipo nell'assembly di definizione viene chiamato il metodo e prevede un contratto solo interni, comportamento può essere compromessi quando, invece, viene eseguito il metodo sottoposto a override nell'assembly esterno. In questo modo viene creata una vulnerabilità di sicurezza.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, impedire il metodo da sottoporre a override all'esterno dell'assembly usando uno dei seguenti:

-   Impostare il tipo dichiarante `sealed` (`NotInheritable` in Visual Basic).

-   Modificare l'accessibilità per il tipo dichiarante `internal` (`Friend` in Visual Basic).

-   Rimuovere tutti i costruttori pubblici dal tipo dichiarante.

-   Implementare il metodo senza usare il `virtual` modificatore.

-   Implementare il metodo in modo esplicito.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se, dopo un attento esame, nessun problema di sicurezza che potrebbero essere sfruttabile se viene eseguito l'override di metodo all'esterno dell'assembly.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo, `BaseImplementation`, che violano questa regola.

 [!code-cpp[FxCop.Security.SealMethods1#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cpp/FxCop.Security.SealMethods1.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/cs/FxCop.Security.SealMethods1.cs#1)]
 [!code-vb[FxCop.Security.SealMethods1#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods1/vb/FxCop.Security.SealMethods1.vb#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente sfrutta l'implementazione del metodo virtuale dell'esempio precedente.

 [!code-cpp[FxCop.Security.SealMethods2#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cpp/FxCop.Security.SealMethods2.cpp#1)]
 [!code-csharp[FxCop.Security.SealMethods2#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/cs/FxCop.Security.SealMethods2.cs#1)]
 [!code-vb[FxCop.Security.SealMethods2#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Security.SealMethods2/vb/FxCop.Security.SealMethods2.vb#1)]

## <a name="see-also"></a>Vedere anche
 [Le interfacce](http://msdn.microsoft.com/library/2feda177-ce11-432d-81b4-d50f5f35fd37) [interfacce](http://msdn.microsoft.com/library/61b06674-12c9-430b-be68-cc67ecee1f5b)



