---
title: 'CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CPP
- CSharp
- VB
ms.workload:
- multiple
ms.openlocfilehash: 22e62a1e3209399be4b10a3ec28db4afdd6f0f20
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71234678"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. interoperabilità|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Una dichiarazione di metodo platform invoke include <xref:System.Boolean?displayProperty=fullName> un parametro o un valore restituito <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> , ma l'attributo non viene applicato al parametro o al valore restituito.

## <a name="rule-description"></a>Descrizione della regola
Un metodo di Platform invoke accede a codice non gestito e viene definito tramite la `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o. <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> <xref:System.Runtime.InteropServices.MarshalAsAttribute>Specifica il comportamento di marshalling utilizzato per convertire i tipi di dati tra codice gestito e non gestito. Molti tipi di dati semplici, ad <xref:System.Byte?displayProperty=fullName> esempio <xref:System.Int32?displayProperty=fullName>e, dispongono di una sola rappresentazione nel codice non gestito e non richiedono la specifica del comportamento di marshalling; il Common Language Runtime fornisce automaticamente il comportamento corretto.

Il <xref:System.Boolean> tipo di dati ha più rappresentazioni nel codice non gestito. Quando l' <xref:System.Runtime.InteropServices.MarshalAsAttribute> oggetto non è specificato, il comportamento di marshalling predefinito <xref:System.Boolean> per il tipo <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>di dati è. Si tratta di un Integer a 32 bit, che non è appropriato in tutte le circostanze. La rappresentazione booleana richiesta dal metodo non gestito deve essere determinata e corrispondente all'oggetto appropriato <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool è il tipo BOOL Win32, che è sempre di 4 byte. UnmanagedType. U1 deve essere usato per C++ `bool` o altri tipi a 1 byte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, applicare <xref:System.Runtime.InteropServices.MarshalAsAttribute> <xref:System.Boolean> al parametro o al valore restituito. Impostare il valore dell'attributo sull'oggetto appropriato <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, il codice viene gestito più facilmente quando il comportamento viene specificato in modo esplicito.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati Platform Invoke metodi contrassegnati con gli attributi <xref:System.Runtime.InteropServices.MarshalAsAttribute> appropriati.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Regole correlate
[CA1901 Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

[CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)