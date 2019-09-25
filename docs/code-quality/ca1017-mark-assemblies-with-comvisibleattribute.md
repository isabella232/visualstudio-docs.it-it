---
title: 'CA1017: Contrassegnare gli assembly con ComVisibleAttribute'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1017
- MarkAssembliesWithComVisible
helpviewer_keywords:
- MarkAssembliesWithComVisible
- CA1017
ms.assetid: 4842cb49-8dd8-4e5d-a2d6-ceeaf6c6cf8e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 073332738a01cb299b2b185c6fca20131222f981
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71236262"
---
# <a name="ca1017-mark-assemblies-with-comvisibleattribute"></a>CA1017: Contrassegnare gli assembly con ComVisibleAttribute

|||
|-|-|
|TypeName|MarkAssembliesWithComVisible|
|CheckId|CA1017|
|Category|Microsoft.Design|
|Modifica|Senza interruzioni|

## <a name="cause"></a>Causa
A un assembly non è applicato <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> l'attributo.

## <a name="rule-description"></a>Descrizione della regola
L' <xref:System.Runtime.InteropServices.ComVisibleAttribute> attributo determina il modo in cui i client COM accedono al codice gestito. In una buona progettazione gli assembly devono indicare in modo esplicito la visibilità COM. È possibile impostare la visibilità COM per un intero assembly e quindi eseguirne l'override per i singoli tipi e membri dei tipi. Se l'attributo non è presente, il contenuto dell'assembly è visibile ai client COM.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, aggiungere l'attributo all'assembly. Se non si desidera che l'assembly sia visibile ai client COM, applicare l'attributo e impostarne il valore su `false`.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Se si desidera che l'assembly sia visibile, applicare l'attributo e impostarne il valore `true`su.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un assembly a cui <xref:System.Runtime.InteropServices.ComVisibleAttribute> è applicato l'attributo per impedire che venga visualizzato ai client com.

[!code-cpp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CPP/ca1017-mark-assemblies-with-comvisibleattribute_1.cpp)]
[!code-vb[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/VisualBasic/ca1017-mark-assemblies-with-comvisibleattribute_1.vb)]
[!code-csharp[FxCop.Design.AssembliesCom#1](../code-quality/codesnippet/CSharp/ca1017-mark-assemblies-with-comvisibleattribute_1.cs)]

## <a name="see-also"></a>Vedere anche

- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
- [Qualificazione di tipi .NET per l'interoperabilità](/dotnet/framework/interop/qualifying-net-types-for-interoperation)