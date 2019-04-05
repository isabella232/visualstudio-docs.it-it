---
title: 'CA1800: Non eseguire il cast inutilmente | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d31cc102aae54ef60b8c16742ffe7e4381df5325
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954575"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Non eseguire il cast inutilmente
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
 Un metodo esegue i cast duplicati comportano su uno dei relativi argomenti o variabili locali. Per l'analisi completa da questa regola, l'assembly testata deve essere compilato usando le informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola
 I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte. Per le operazioni cast duplicati esplicito, archiviare il risultato del cast in una variabile locale e usare la variabile locale anziché le operazioni cast duplicati.

 Se il codice c# `is` operatore viene usato per verificare se il cast sarà completato prima di eseguita il cast effettivo, è consigliabile testare il risultato del `as` operatore invece. Questo offre la stessa funzionalità senza l'operazione di cast implicito che viene eseguita mediante il `is` operatore.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'implementazione del metodo per ridurre al minimo il numero di operazioni cast.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È sicuro per eliminare un avviso da questa regola o di ignorare completamente la regola se le prestazioni non costituiscono un problema.

## <a name="example"></a>Esempio
 L'esempio seguente illustra un metodo che viola la regola usando il codice c# `is` operatore. Un secondo metodo soddisfa la regola, sostituendo il `is` operatore con il risultato di un test di `as` operatore, che riduce il numero di operazioni di cast per ogni iterazione da due a uno.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCastsAsIs/cs/FxCop.Performance.UnnecessaryCastsAsIs.cs#1)]

## <a name="example"></a>Esempio
 Nell'esempio seguente viene illustrato un metodo, `start_Click`, che ha più di cast espliciti duplicati, che viola la regola e un metodo, `reset_Click`, che soddisfa la regola, archiviando il cast in una variabile locale.

 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/cs/FxCop.Performance.UnnecessaryCasts.cs#1)]
 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Performance.UnnecessaryCasts/vb/FxCop.Performance.UnnecessaryCasts.vb#1)]

## <a name="see-also"></a>Vedere anche
 [as](http://msdn.microsoft.com/library/a9be126b-cbf4-4990-a70d-d0e1983cad0e) [is](http://msdn.microsoft.com/library/bc62316a-d41f-4f90-8300-c6f4f0556e43)
