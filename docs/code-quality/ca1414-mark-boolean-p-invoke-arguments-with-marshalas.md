---
title: 'CA1414: Contrassegnare argomenti P-Invoke booleani con MarshalAs'
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
ms.openlocfilehash: 0f8140e78d1ee3340e9ee5441e183b55d4c5111c
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444178"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. interoperabilità|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Una dichiarazione di metodo platform invoke include un parametro @no__t 0 o un valore restituito, ma l'attributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> non viene applicato al parametro o al valore restituito.

## <a name="rule-description"></a>Descrizione della regola
Un metodo di platform invoke accede a codice non gestito e viene definito utilizzando la parola chiave `Declare` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> specifica il comportamento di marshalling utilizzato per convertire i tipi di dati tra codice gestito e non gestito. Molti tipi di dati semplici, ad esempio <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, hanno una sola rappresentazione nel codice non gestito e non richiedono la specifica del comportamento di marshalling; il Common Language Runtime fornisce automaticamente il comportamento corretto.

Il tipo di dati <xref:System.Boolean> ha più rappresentazioni nel codice non gestito. Quando il <xref:System.Runtime.InteropServices.MarshalAsAttribute> non viene specificato, il comportamento di marshalling predefinito per il tipo di dati <xref:System.Boolean> è <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Si tratta di un Integer a 32 bit, che non è appropriato in tutte le circostanze. La rappresentazione booleana richiesta dal metodo non gestito deve essere determinata e abbinata al <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> appropriato. UnmanagedType. bool è il tipo BOOL Win32, che è sempre di 4 byte. È necessario utilizzare UnmanagedType. U1 per C++ `bool` o altri tipi a 1 byte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola, applicare <xref:System.Runtime.InteropServices.MarshalAsAttribute> al parametro <xref:System.Boolean> o al valore restituito. Impostare il valore dell'attributo sull'<xref:System.Runtime.InteropServices.UnmanagedType> appropriato.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, il codice viene gestito più facilmente quando il comportamento viene specificato in modo esplicito.

## <a name="example"></a>Esempio

Nell'esempio seguente vengono illustrati platform invoke metodi contrassegnati con gli attributi <xref:System.Runtime.InteropServices.MarshalAsAttribute> appropriati.

[!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
[!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
[!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Regole correlate
[CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901.md)

[CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)
