---
title: 'CA1414: contrassegnare gli argomenti P-Invoke booleani con marshalling | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 588e16a6b21b320ad7012bd20d79a62d027679e3
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652695"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una dichiarazione di metodo platform invoke include un parametro <xref:System.Boolean?displayProperty=fullName> o un valore restituito, ma l'attributo <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> non viene applicato al parametro o al valore restituito.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo di platform invoke accede a codice non gestito e viene definito tramite la parola chiave `Declare` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> specifica il comportamento di marshalling utilizzato per convertire i tipi di dati tra codice gestito e non gestito. Molti tipi di dati semplici, ad esempio <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, hanno una sola rappresentazione nel codice non gestito e non richiedono la specifica del comportamento di marshalling; il Common Language Runtime fornisce automaticamente il comportamento corretto.

 Il tipo di dati <xref:System.Boolean> ha più rappresentazioni nel codice non gestito. Quando il <xref:System.Runtime.InteropServices.MarshalAsAttribute> non viene specificato, il comportamento di marshalling predefinito per il tipo di dati <xref:System.Boolean> è <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Si tratta di un Integer a 32 bit, che non è appropriato in tutte le circostanze. La rappresentazione booleana richiesta dal metodo non gestito deve essere determinata e abbinata al <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> appropriato. UnmanagedType. bool è il tipo BOOL Win32, che è sempre di 4 byte. È necessario utilizzare UnmanagedType. U1 per C++ `bool` o altri tipi a 1 byte. Per altre informazioni, vedere [marshalling predefinito per i tipi booleani](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, applicare <xref:System.Runtime.InteropServices.MarshalAsAttribute> al parametro <xref:System.Boolean> o al valore restituito. Impostare il valore dell'attributo sull'<xref:System.Runtime.InteropServices.UnmanagedType> appropriato.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, il codice viene gestito più facilmente quando il comportamento viene specificato in modo esplicito.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due platform invoke metodi contrassegnati con gli attributi di <xref:System.Runtime.InteropServices.MarshalAsAttribute> appropriati.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> il [marshalling predefinito per i tipi booleani](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) che [interagiscono con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
