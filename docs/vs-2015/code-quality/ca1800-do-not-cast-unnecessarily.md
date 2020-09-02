---
title: 'CA1800: non eseguire il cast inutilmente | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 757d66ef719b3a1f39a9164dfd50ce1fcf8799db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547797"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Non eseguire il cast inutilmente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft. performance|
|Modifica importante|Senza interruzioni|

## <a name="cause"></a>Causa
 Un metodo esegue cast duplicati su uno degli argomenti o variabili locali. Per un'analisi completa da parte di questa regola, è necessario compilare l'assembly testato utilizzando le informazioni di debug e il file di database di programma (con estensione pdb) associato.

## <a name="rule-description"></a>Descrizione della regola
 I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte. Per le operazioni di cast duplicate esplicite, archiviare il risultato del cast in una variabile locale e usare la variabile locale anziché le operazioni cast duplicate.

 Se l' `is` operatore C# viene usato per verificare se il cast riuscirà prima di eseguire il cast effettivo, provare a testare il risultato dell' `as` operatore. Che fornisce la stessa funzionalità senza l'operazione cast implicita eseguita dall' `is` operatore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'implementazione del metodo per ridurre al minimo il numero di operazioni cast.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola oppure ignorare completamente la regola, se le prestazioni non sono un problema.

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo che viola la regola usando l'operatore C# `is` . Un secondo metodo soddisfa la regola sostituendo l' `is` operatore con un test rispetto al risultato dell' `as` operatore, che riduce il numero di operazioni cast per iterazione da due a uno.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `start_Click` , che dispone di più cast espliciti duplicati, che viola la regola e un metodo, `reset_Click` , che soddisfa la regola archiviando il cast in una variabile locale.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Vedere anche
 [così come](https://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [sono](https://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
