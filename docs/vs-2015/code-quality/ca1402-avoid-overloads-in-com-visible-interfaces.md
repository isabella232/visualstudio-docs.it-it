---
title: 'CA1402: Evitare gli overload nelle interfacce visibili a COM | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
helpviewer_keywords:
- AvoidOverloadsInComVisibleInterfaces
- CA1402
ms.assetid: 2724c1f9-d5d3-4704-b124-21c4d398e5df
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: ece9a444ac308003c56da1bd4f2ecf4433e2b4a9
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589198"
---
# <a name="ca1402-avoid-overloads-in-com-visible-interfaces"></a>CA1402: Evitare gli overload nelle interfacce visibili a COM
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA1402: evitare gli overload nelle interfacce visibili a COM](https://docs.microsoft.com/visualstudio/code-quality/ca1402-avoid-overloads-in-com-visible-interfaces).

|||
|-|-|
|TypeName|AvoidOverloadsInComVisibleInterfaces|
|CheckId|CA1402|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un modello COM (Component Object) visibile interfaccia dichiara i metodi di overload.

## <a name="rule-description"></a>Descrizione della regola
 Quando i metodi sottoposti a overload vengono esposti ai client COM, solo il primo overload di metodo conserva il proprio nome. Gli overload successivi vengono rinominati in modo univoco aggiungendo al nome un carattere di sottolineatura '_' e un numero intero che corrisponde all'ordine di dichiarazione dell'overload. Si consideri ad esempio i metodi seguenti.

```
void SomeMethod(int valueOne);
void SomeMethod(int valueOne, int valueTwo, int valueThree);
void SomeMethod(int valueOne, int valueTwo);
```

 Questi metodi vengono esposti ai client COM come indicato di seguito.

```
void SomeMethod(int valueOne);
void SomeMethod_2(int valueOne, int valueTwo, int valueThree);
void SomeMethod_3(int valueOne, int valueTwo);
```

 I client COM Visual Basic 6 non possono implementare i metodi di interfaccia con un carattere di sottolineatura nel nome.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, rinominare i metodi di overload in modo che i nomi siano univoci. In alternativa, rendere l'interfaccia invisibili a COM modificando l'accessibilità `internal` (`Friend` nel [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]) oppure applicando il <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> attributo impostato su `false`.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un'interfaccia che viola la regola e un'interfaccia che soddisfa la regola.

 [!code-csharp[FxCop.Interoperability.OverloadsInterface#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/cs/FxCop.Interoperability.OverloadsInterface.cs#1)]
 [!code-vb[FxCop.Interoperability.OverloadsInterface#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.OverloadsInterface/vb/FxCop.Interoperability.OverloadsInterface.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1413: Evitare i campi non pubblici nei tipi valore visibili a COM](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)

 [CA1407: Evitare i membri statici nei tipi visibili a COM](../code-quality/ca1407-avoid-static-members-in-com-visible-types.md)

 [CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) [tipo di dati Long](http://msdn.microsoft.com/library/b4770c34-1804-4f8c-b512-c10b0893e516)



