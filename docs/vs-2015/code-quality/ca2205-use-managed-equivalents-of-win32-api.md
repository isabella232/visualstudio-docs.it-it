---
title: "CA2205: Usare gestite equivalenti dell'API Win32 | Microsoft Docs"
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
helpviewer_keywords:
- UseManagedEquivalentsOfWin32Api
- CA2205
ms.assetid: 1c65ab59-3e50-4488-a727-3969c7f6cbe4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 98c32eb197bb644d0e540bccea10603217342642
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589963"
---
# <a name="ca2205-use-managed-equivalents-of-win32-api"></a>CA2205: Utilizzare equivalenti gestiti dell'API Win32
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [CA2205: uso di API Win32 equivalenti gestiti](https://docs.microsoft.com/visualstudio/code-quality/ca2205-use-managed-equivalents-of-win32-api).

|||
|-|-|
|TypeName|UseManagedEquivalentsOfWin32Api|
|CheckId|CA2205|
|Category|Microsoft.Usage|
|Modifica importante|Non importante|

## <a name="cause"></a>Causa
 Un platform invoke metodo è definito e un metodo con la funzionalità equivalente si trova il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] libreria di classi.

## <a name="rule-description"></a>Descrizione della regola
 Un platform invoke (metodo) viene usato per chiamare una funzione DLL non gestita e viene definita utilizzando il <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> attributo, o `Declare` parola chiave in Visual Basic. Metodo di richiamo una piattaforma definita in modo errato può causare eccezioni di runtime a causa di problemi, ad esempio una funzione di nome non corretto, mapping dei tipi di dati di valore di parametro e restituire e specifiche di campo corretto, ad esempio la convenzione di chiamata e il carattere errato set. Se disponibile, si tratta generalmente di errore più semplice e meno soggetto a chiamare il metodo gestito equivalente a to definire e chiamare direttamente il metodo non gestito. La chiamata a una piattaforma di richiamo metodo possono causare problemi di sicurezza aggiuntive che devono essere risolte.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, sostituire la chiamata alla funzione non gestita con una chiamata nel relativo equivalente gestito.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Eliminare un avviso da questa regola se il metodo di sostituzione suggerita non fornisce le funzionalità necessarie.

## <a name="example"></a>Esempio
 L'esempio seguente mostra un platform invoke definizione del metodo che viola la regola. Inoltre, le chiamate alla piattaforma invoke (metodo) e il metodo equivalente gestito vengono visualizzati.

 [!code-csharp[FxCop.Usage.ManagedEquivalents#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/cs/FxCop.Usage.ManagedEquivalents.cs#1)]
 [!code-vb[FxCop.Usage.ManagedEquivalents#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.ManagedEquivalents/vb/FxCop.Usage.ManagedEquivalents.vb#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1404: Chiamare GetLastError immediatamente dopo P/Invoke](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)

 [CA1060: Spostare P/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)

 [CA1400: I punti di ingresso P/Invoke devono esistere](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)

 [CA1401: I P/Invoke non devono essere visibili](../code-quality/ca1401-p-invokes-should-not-be-visible.md)

 [CA2101: Specificare il marshalling per argomenti di stringa P/Invoke](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)



