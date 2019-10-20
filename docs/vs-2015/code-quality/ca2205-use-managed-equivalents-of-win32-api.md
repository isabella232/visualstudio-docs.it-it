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
ms.openlocfilehash: 931b1e5099bf221fefc7a8f4a19524d2531a4418
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72609482"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizzare equivalenti gestiti dell'API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Category|Microsoft. Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Viene definito un metodo di platform invoke e nella libreria di classi [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] esiste un metodo con la funzionalità equivalente.

## <a name="rule-description"></a>Descrizione della regola
 Un metodo di platform invoke viene usato per chiamare una funzione DLL non gestita e viene definito usando l'attributo <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o la parola chiave `Declare` in Visual Basic. Un metodo di platform invoke definito in modo non corretto può causare eccezioni di runtime a causa di problemi quali una funzione senza nome, un mapping errato di tipi di dati di parametri e valori restituiti e specifiche di campo non corrette, ad esempio la convenzione di chiamata e il carattere set. Se disponibile, è in genere più semplice e meno soggetta a errori chiamare il metodo gestito equivalente rispetto alla definizione e alla chiamata diretta del metodo non gestito. La chiamata a un metodo di platform invoke può anche causare problemi di sicurezza aggiuntivi che devono essere risolti.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire la chiamata alla funzione non gestita con una chiamata al relativo equivalente gestito.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se il metodo di sostituzione suggerito non fornisce la funzionalità necessaria.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrata una definizione di metodo platform invoke che viola la regola. Vengono inoltre visualizzate le chiamate al metodo platform invoke e al metodo gestito equivalente.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Spostare P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)
