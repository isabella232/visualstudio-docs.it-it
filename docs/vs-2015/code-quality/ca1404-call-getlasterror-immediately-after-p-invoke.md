---
title: 'CA1404: chiamare GetLastError immediatamente dopo P-Invoke | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
helpviewer_keywords:
- CallGetLastErrorImmediatelyAfterPInvoke
- CA1404
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 2664837c17894f7ca336d650a7e08e21c45d955f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661316"
---
# <a name="ca1404-call-getlasterror-immediately-after-pinvoke"></a>CA1404: Chiamare GetLastError immediatamente dopo P/Invoke
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|
|CheckId|CA1404|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Viene eseguita una chiamata al metodo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName> o alla funzione Win32 `GetLastError` equivalente e la chiamata immediatamente prima non è a un metodo di platform invoke.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo di platform invoke accede a codice non gestito e viene definito tramite la parola chiave `Declare` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. In genere, in caso di errore, le funzioni non gestite chiamano la funzione Win32 `SetLastError` per impostare un codice di errore associato all'errore. Il chiamante della funzione failed chiama la funzione Win32 `GetLastError` per recuperare il codice di errore e determinare la ragione dell'errore. Il codice di errore viene mantenuto per singolo thread e viene sovrascritto dalla chiamata successiva a `SetLastError`. Dopo una chiamata a un metodo di platform invoke non riuscito, il codice gestito può recuperare il codice di errore chiamando il metodo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Poiché il codice di errore può essere sovrascritto da chiamate interne da altri metodi della libreria di classi gestite, il `GetLastError` o il metodo di <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> deve essere chiamato immediatamente dopo la chiamata al metodo di platform invoke.

 La regola ignora le chiamate ai membri gestiti seguenti quando si verificano tra la chiamata al metodo platform invoke e la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>. Questi membri non modificano il codice di errore e sono utili per determinare l'esito positivo di alcune chiamate al metodo platform invoke.

- <xref:System.IntPtr.Zero?displayProperty=fullName>

- <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>

- <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>

- <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, spostare la chiamata a <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> in modo che segua immediatamente la chiamata al metodo platform invoke.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola se il codice tra la chiamata al metodo platform invoke e la chiamata al metodo <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> non può causare la modifica del codice di errore in modo esplicito o implicito.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola e un metodo che soddisfa la regola.

 [!code-csharp[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/cs/FxCop.Interoperability.LastErrorPInvoke.cs#1)]
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.LastErrorPInvoke/vb/FxCop.Interoperability.LastErrorPInvoke.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1060: Spostare P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

 [CA2205: Usare equivalenti gestiti dell'API Win32](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)
