---
title: 'CA1400: i punti di ingresso P-Invoke devono esistere | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1400
- PInvokeEntryPointsShouldExist
helpviewer_keywords:
- PInvokeEntryPointsShouldExist
- CA1400
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 15b63e49f89e17db631772c48765cc610f47ed29
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85548304"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: I punti di ingresso P/Invoke devono esistere
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft. interoperabilità|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto è contrassegnato con <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> . Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria. Se la regola non riesce a trovare il nome del metodo esattamente come è specificato, Cerca le versioni ANSI o a caratteri wide del metodo eseguendo il suffisso del nome del metodo con "A" o "W". Se non viene trovata alcuna corrispondenza, la regola tenta di individuare una funzione utilizzando il formato del nome del __stdcall ( _MyMethod@12 , dove 12 rappresenta la lunghezza degli argomenti). Se non viene trovata alcuna corrispondenza e il nome del metodo inizia con ' #', la regola cerca la funzione come riferimento ordinale anziché come riferimento a un nome.

## <a name="rule-description"></a>Descrizione della regola
 Non è disponibile alcun controllo in fase di compilazione per assicurarsi che i metodi contrassegnati con <xref:System.Runtime.InteropServices.DllImportAttribute> si trovino nella dll non gestita a cui si fa riferimento. Se nella libreria non è presente alcuna funzione con il nome specificato o se gli argomenti del metodo non corrispondono agli argomenti della funzione, il Common Language Runtime genera un'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere il metodo con l' <xref:System.Runtime.InteropServices.DllImportAttribute> attributo. Verificare che la libreria non gestita esista e si trovi nella stessa directory dell'assembly che contiene il metodo. Se la libreria è presente e viene fatto riferimento correttamente, verificare che il nome del metodo, il tipo restituito e la firma dell'argomento corrispondano alla funzione della libreria.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola quando la libreria non gestita si trova nella stessa directory dell'assembly gestito che vi fa riferimento. Potrebbe essere possibile eliminare un avviso da questa regola nel caso in cui non sia possibile trovare la libreria non gestita.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Nessuna funzione denominata viene `DoSomethingUnmanaged` eseguita nel kernel32.dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
