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
ms.openlocfilehash: 1a06197278c61a25c4baad15888f818ed1e1f673
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55955883"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un platform invoke (metodo) dichiarazione include un' <xref:System.Boolean?displayProperty=fullName> valore restituito o parametro, ma il <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> attributo non viene applicato al valore restituito o parametro.

## <a name="rule-description"></a>Descrizione della regola
 Una piattaforma di richiamare codice non gestito accede a metodo e viene definito tramite il `Declare` parola chiave in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] o il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Specifica il comportamento di marshalling che viene usato per convertire i tipi di dati tra codice gestito e gestito. Molti tipi di dati semplici, ad esempio <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, associata una sola rappresentazione in codice non gestito e non richiedono la specifica del relativo comportamento di marshalling; common language runtime fornisce automaticamente il comportamento corretto.

 Il <xref:System.Boolean> tipo di dati sono disponibili più rappresentazioni nel codice non gestito. Quando la <xref:System.Runtime.InteropServices.MarshalAsAttribute> viene omesso, il comportamento di marshalling predefinito di <xref:System.Boolean> tipo di dati è <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Si tratta di un numero intero a 32 bit che non è appropriato in qualsiasi circostanza. La rappresentazione booleana richiesto dal metodo non gestito deve essere determinata e corrispondente appropriata <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool è del tipo BOOL Win32, che corrisponde sempre a 4 byte. UnmanagedType. U1 deve essere utilizzato per C++ `bool` o altri tipi di 1 byte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, si applicano <xref:System.Runtime.InteropServices.MarshalAsAttribute> per il <xref:System.Boolean> parametro o valore restituito. Impostare il valore dell'attributo appropriati <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, il codice più facilmente viene mantenuto quando viene specificato in modo esplicito il comportamento.

## <a name="example"></a>Esempio

L'esempio seguente illustra i metodi contrassegnati con l'appropriato di platform invoke <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributi.

 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]

## <a name="related-rules"></a>Regole correlate
 [CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vedere anche

- <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>
- [Interoperabilità con codice non gestito](/dotnet/framework/interop/index)