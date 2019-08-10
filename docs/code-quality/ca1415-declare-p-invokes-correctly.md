---
title: 'CA1415: Dichiarare correttamente i P/Invoke'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5cc12d5d0a62f8d2530f13fcf860aba4e118ca4
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68921847"
---
# <a name="ca1415-declare-pinvokes-correctly"></a>CA1415: Dichiarare correttamente i P/Invoke

|||
|-|-|
|TypeName|DeclarePInvokesCorrectly|
|CheckId|CA1415|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni: se il P/Invoke che dichiara il parametro non è visibile all'esterno dell'assembly. Interruzioni: se il P/Invoke che dichiara il parametro può essere visualizzato all'esterno dell'assembly.|

## <a name="cause"></a>Causa
Un metodo di platform invoke è dichiarato in modo errato.

## <a name="rule-description"></a>Descrizione della regola
Un metodo di Platform invoke accede a codice non gestito e viene definito tramite la `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o. <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attualmente questa regola cerca Platform Invoke dichiarazioni di metodo destinate a funzioni Win32 che hanno un puntatore a un parametro di struttura sovrapposta e il parametro gestito corrispondente non è un puntatore a <xref:System.Threading.NativeOverlapped?displayProperty=fullName> una struttura.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, dichiarare correttamente il metodo platform invoke.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola.

## <a name="example"></a>Esempio
Nell'esempio seguente vengono illustrati platform invoke metodi che violano la regola e soddisfano la regola.

[!code-csharp[FxCop.Interoperability.DeclarePInvokes#1](../code-quality/codesnippet/CSharp/ca1415-declare-p-invokes-correctly_1.cs)]

## <a name="see-also"></a>Vedere anche
[Interoperabilità con codice non gestito](/dotnet/framework/interop/index)