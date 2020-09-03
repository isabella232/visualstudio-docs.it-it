---
title: "CA2205: usare equivalenti gestiti dell'API Win32 | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 85e27ab04ca81f5513a0b09bc41548f4a7c2430d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547680"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Usare equivalenti gestiti dell'API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Viene definito un metodo di platform invoke e un metodo con la funzionalità equivalente è presente nella [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] libreria di classi.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo di platform invoke viene usato per chiamare una funzione DLL non gestita e viene definito usando l' <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo o la `Declare` parola chiave in Visual Basic. Un metodo platform invoke definito in modo errato può causare eccezioni in fase di esecuzione a causa di problemi quali una funzione senza nome, un mapping errato di tipi di dati di parametri e valori restituiti e specifiche di campo non corrette, ad esempio la convenzione di chiamata e il set di caratteri. Se disponibile, è in genere più semplice e meno soggetta a errori chiamare il metodo gestito equivalente rispetto alla definizione e alla chiamata diretta del metodo non gestito. La chiamata a un metodo di platform invoke può anche causare problemi di sicurezza aggiuntivi che devono essere risolti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire la chiamata alla funzione non gestita con una chiamata al relativo equivalente gestito.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se il metodo di sostituzione suggerito non fornisce la funzionalità necessaria.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una definizione di metodo platform invoke che viola la regola. Vengono inoltre visualizzate le chiamate al metodo platform invoke e al metodo gestito equivalente.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1404: chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: spostare i P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: i punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: i P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: specificare il marshalling per gli argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
