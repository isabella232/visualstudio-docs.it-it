---
title: 'CA1400: I punti di ingresso P-Invoke devono esistere | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 0e5696689d0aa40f4af2e11970c81b47737a3d80
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966113"
---
# <a name="ca1400-pinvoke-entry-points-should-exist"></a>CA1400: I punti di ingresso P/Invoke devono esistere
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeEntryPointsShouldExist|
|CheckId|CA1400|
|Category|Microsoft.Interoperability|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto è contrassegnato con il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>. Non è possibile individuare la libreria non gestita né associare il metodo a una funzione nella libreria. Se la regola non è possibile trovare il nome del metodo esattamente come viene specificato, la ricerca di ANSI o versioni a caratteri wide del metodo aggiungendo il nome del metodo con "A" o "W". Se viene trovata alcuna corrispondenza, la regola tenta di individuare una funzione usando il formato del nome stdcall (_MyMethod@12, dove 12 rappresenta la lunghezza degli argomenti). Se viene trovata alcuna corrispondenza e il nome del metodo inizia con '#', viene cercata la funzione come un riferimento ordinale anziché un riferimento al nome.

## <a name="rule-description"></a>Descrizione della regola
 Nessun controllo in fase di compilazione è disponibile per assicurarsi che i metodi contrassegnati con <xref:System.Runtime.InteropServices.DllImportAttribute> si trovano in cui viene fatto riferimento DLL non gestita. Se nessuna funzione con il nome specificato si trova nella raccolta o gli argomenti al metodo non corrispondono agli argomenti della funzione, common language runtime genera un'eccezione.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, correggere il metodo che presenta il <xref:System.Runtime.InteropServices.DllImportAttribute> attributo. Assicurarsi che la libreria non gestita esista e sia nella stessa directory dell'assembly che contiene il metodo. Se la raccolta è presente e un riferimento corretto, verificare che il nome del metodo, il tipo restituito e la firma dell'argomento corrispondere alla funzione di libreria.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non escludere un avviso da questa regola quando la libreria non gestita è nella stessa directory dell'assembly gestito che vi fa riferimento. Potrebbe essere possibile eliminare un avviso da questa regola nel caso in cui la libreria non gestita non è possibile individuare.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un tipo che viola la regola. Nessuna funzione denominata `DoSomethingUnmanaged` si verifica nel Kernel32. dll.

 [!code-csharp[FxCop.Interoperability.DLLExists#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.DLLExists/cs/FxCop.Interoperability.DLLExists.cs#1)]

## <a name="see-also"></a>Vedere anche
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>
