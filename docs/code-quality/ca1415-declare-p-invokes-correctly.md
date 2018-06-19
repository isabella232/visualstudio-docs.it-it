---
title: 'CA1415: Dichiarare richiama P correttamente'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1415
- DeclarePInvokesCorrectly
helpviewer_keywords:
- CA1415
- DeclarePInvokesCorrectly
ms.assetid: 42a90796-0264-4460-bf97-2fb4a093dfdc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 6a690baeb804d3722d442c30077cc07d260a8952
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915763"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Dichiarare correttamente i P/Invoke
|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale - Se P/Invoke che dichiara il parametro non è visibile all'esterno dell'assembly. Sostanziale - Se P/Invoke che dichiara il parametro è visibile all'esterno dell'assembly.|

## <a name="cause"></a>Causa
 Un metodo di PInvoke è dichiarato in modo non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Un platform invoke (metodo) accede al codice non gestito e viene definito utilizzando il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Attualmente, questa regola viene ricercato platform invoke per le dichiarazioni di metodo che le funzioni Win32 che dispone di un puntatore a un parametro di struttura OVERLAPPED e il cui parametro gestito corrispondente non è un puntatore a un <xref:System.Threading.NativeOverlapped?displayProperty=fullName> struttura.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, dichiarare correttamente il platform invoke (metodo).

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
 L'esempio seguente illustra i metodi che violano la regola e soddisfano la regola di platform invoke.

 [!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Vedere anche
 [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)