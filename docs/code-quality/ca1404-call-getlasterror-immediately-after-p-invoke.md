---
title: 'CA1404: Chiamare GetLastError immediatamente dopo P/Invoke'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 03add1625c4d59bb180f9f0f08692e67bee8047b
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/09/2019
ms.locfileid: "68922072"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Chiamare GetLastError immediatamente dopo P/Invoke

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa

Viene eseguita una chiamata al <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> metodo o alla funzione Win32 `GetLastError` equivalente e la chiamata immediatamente prima non è a un metodo platform invoke.

## <a name="rule-description"></a>Descrizione della regola
Un metodo di Platform invoke accede a codice non gestito e viene definito tramite la `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> nell'attributo. In genere, in caso di errore, le funzioni non gestite `SetLastError` chiamano la funzione Win32 per impostare un codice di errore associato all'errore. Il chiamante della funzione failed chiama la funzione Win32 `GetLastError` per recuperare il codice di errore e determinare la sua origine. Il codice di errore viene mantenuto per singolo thread e viene sovrascritto dalla chiamata successiva a `SetLastError`. Dopo una chiamata a un metodo di Platform Invoke non riuscito, il codice gestito può recuperare il codice di <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> errore chiamando il metodo. Poiché il codice di errore può essere sovrascritto da chiamate interne da altri metodi di libreria di classi `GetLastError` gestite <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> , il metodo o deve essere chiamato immediatamente dopo la chiamata al metodo platform invoke.

La regola ignora le chiamate ai membri gestiti seguenti quando si verificano tra la chiamata al metodo platform invoke e la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Questi membri non modificano il codice di errore e sono utili per determinare l'esito positivo di alcune chiamate al metodo platform invoke.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, spostare la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> in modo che segua immediatamente la chiamata al metodo platform invoke.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola se il codice tra la chiamata al metodo Platform Invoke e la <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> chiamata al metodo non può causare la modifica del codice di errore in modo esplicito o implicito.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato un metodo che viola la regola e un metodo che soddisfa la regola.

[!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
[!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]

## <a name="related-rules"></a>Regole correlate
[CA1060 Sposta P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

[CA1400 I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

[CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

[CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

[CA2205: Usare equivalenti gestiti dell'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)