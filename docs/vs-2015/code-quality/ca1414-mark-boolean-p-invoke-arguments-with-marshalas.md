---
title: 'CA1414: Contrassegnare gli argomenti P-Invoke booleani con MarshalAs | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
helpviewer_keywords:
- CA1414
- MarkBooleanPInvokeArgumentsWithMarshalAs
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7f8378d2b3f498146fc960e57d1d3562827fe347
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49918402"
---
# <a name="ca1414-mark-boolean-pinvoke-arguments-with-marshalas"></a>CA1414: Contrassegnare gli argomenti P/Invoke booleani con MarshalAs
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|
|CheckId|CA1414|
|Category|Microsoft.Interoperability|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un platform invoke (metodo) dichiarazione include un' <xref:System.Boolean?displayProperty=fullName> valore restituito o parametro, ma il <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName> attributo non viene applicato al valore restituito o parametro.

## <a name="rule-description"></a>Descrizione della regola
 Una piattaforma di richiamare codice non gestito accede a metodo e viene definito tramite il `Declare` parola chiave in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] o il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. <xref:System.Runtime.InteropServices.MarshalAsAttribute> Specifica il comportamento di marshalling che viene usato per convertire i tipi di dati tra codice gestito e gestito. Molti tipi di dati semplici, ad esempio <xref:System.Byte?displayProperty=fullName> e <xref:System.Int32?displayProperty=fullName>, associata una sola rappresentazione in codice non gestito e non richiedono la specifica del relativo comportamento di marshalling; common language runtime fornisce automaticamente il comportamento corretto.

 Il <xref:System.Boolean> tipo di dati sono disponibili più rappresentazioni nel codice non gestito. Quando la <xref:System.Runtime.InteropServices.MarshalAsAttribute> viene omesso, il comportamento di marshalling predefinito di <xref:System.Boolean> tipo di dati è <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. Si tratta di un numero intero a 32 bit che non è appropriato in qualsiasi circostanza. La rappresentazione booleana richiesto dal metodo non gestito deve essere determinata e corrispondente appropriata <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>. UnmanagedType. bool è del tipo BOOL Win32, che corrisponde sempre a 4 byte. UnmanagedType. U1 deve essere utilizzato per C++ `bool` o altri tipi di 1 byte. Per altre informazioni, vedere [marshalling predefinito per i tipi Boolean](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, si applicano <xref:System.Runtime.InteropServices.MarshalAsAttribute> per il <xref:System.Boolean> parametro o valore restituito. Impostare il valore dell'attributo appropriati <xref:System.Runtime.InteropServices.UnmanagedType>.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola. Anche se il comportamento di marshalling predefinito è appropriato, il codice più facilmente viene mantenuto quando viene specificato in modo esplicito il comportamento.

## <a name="example"></a>Esempio
 L'esempio seguente illustra due metodi sono contrassegnati con l'appropriato PInvoke <xref:System.Runtime.InteropServices.MarshalAsAttribute> attributi.

 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cpp/FxCop.Interoperability.BoolMarshalAs.cpp#1)]
 [!code-csharp[FxCop.Interoperability.BoolMarshalAs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/cs/FxCop.Interoperability.BoolMarshalAs.cs#1)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.BoolMarshalAs/vb/FxCop.Interoperability.BoolMarshalAs.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1901: Le dichiarazioni P/Invoke devono essere portabili](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)

 [CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> [Marshalling predefinito per i tipi Boolean](http://msdn.microsoft.com/en-us/d4c00537-70f7-4ca6-8197-bfc1ec037ff9) [interoperabilità con codice non gestito](http://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)



