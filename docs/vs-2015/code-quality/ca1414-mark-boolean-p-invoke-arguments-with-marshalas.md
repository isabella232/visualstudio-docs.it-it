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
ms.openlocfilehash: 783f7fad05cad18efea2f83b6d76c4c9e644f119
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548382"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft. interoperabilità|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Una dichiarazione di metodo platform invoke include un <xref:System.Boolean?displayProperty=fullName> parametro o un valore restituito <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> , ma l'attributo non viene applicato al parametro o al valore restituito.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo di platform invoke accede a codice non gestito e viene definito tramite la `Declare` parola chiave in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . <xref:System.Runtime.InteropServices.MarshalAsAttribute>Specifica il comportamento di marshalling utilizzato per convertire i tipi di dati tra codice gestito e non gestito. Molti tipi di dati semplici, ad esempio <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName> , dispongono di una sola rappresentazione nel codice non gestito e non richiedono la specifica del comportamento di marshalling; il Common Language Runtime fornisce automaticamente il comportamento corretto.

 Il <xref:System.Boolean> tipo di dati ha più rappresentazioni nel codice non gestito. Quando l'oggetto <xref:System.Runtime.InteropServices.MarshalAsAttribute> non è specificato, il comportamento di marshalling predefinito per il <xref:System.Boolean> tipo di dati è <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . Si tratta di un Integer a 32 bit, che non è appropriato in tutte le circostanze. La rappresentazione booleana richiesta dal metodo non gestito deve essere determinata e corrispondente all'oggetto appropriato <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> . UnmanagedType. bool è il tipo BOOL Win32, che è sempre di 4 byte. UnmanagedType. U1 deve essere usato per C++ `bool` o altri tipi a 1 byte. Per altre informazioni, vedere [marshalling predefinito per i tipi booleani](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, applicare <xref:System.Runtime.InteropServices.MarshalAsAttribute> al <xref:System.Boolean> parametro o al valore restituito. Impostare il valore dell'attributo sull'oggetto appropriato <xref:System.Runtime.InteropServices.UnmanagedType> .

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, il codice viene gestito più facilmente quando il comportamento viene specificato in modo esplicito.

## <a name="example"></a>Esempio
 Nell'esempio seguente vengono illustrati due platform invoke metodi contrassegnati con gli <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributi appropriati.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1901: le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>[Marshalling predefinito per i tipi booleani](https://msdn.microsoft.com/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) che [interagiscono con codice non gestito](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
