---
title: 'CA1800: Non eseguire il cast inutilmente'
ms.date: 10/26/2017
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1800
- DoNotCastUnnecessarily
helpviewer_keywords:
- DoNotCastUnnecessarily
- CA1800
ms.assetid: b79a010a-6627-421e-8955-6007e32fa808
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- VB
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 1ef6e73812a63fdc4cc4392621ab49b279a32d18
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53822029"
---
# <a name="ca1800-do-not-cast-unnecessarily"></a>CA1800: Non eseguire il cast inutilmente

|||
|-|-|
|TypeName|DoNotCastUnnecessarily|
|CheckId|CA1800|
|Category|Microsoft.Performance|
|Modifica importante|Non sostanziale|

## <a name="cause"></a>Causa
Un metodo esegue i cast duplicati comportano su uno dei relativi argomenti o variabili locali.

Per l'analisi completa da questa regola, l'assembly testata deve essere compilato usando le informazioni di debug e il file di database (con estensione pdb) del programma associato deve essere disponibile.

## <a name="rule-description"></a>Descrizione della regola
I cast duplicati comportano una riduzione delle prestazioni, in particolare quando i cast vengono eseguiti in istruzioni di iterazione compatte. Per le operazioni cast duplicati esplicito, archiviare il risultato del cast in una variabile locale e usare la variabile locale anziché le operazioni cast duplicati.

Se il codice c# `is` operatore viene usato per verificare se il cast sarà completato prima di eseguita il cast effettivo, è consigliabile testare il risultato del `as` operatore invece. Questo offre la stessa funzionalità senza l'operazione di cast implicito che viene eseguita mediante il `is` operatore. In alternativa, in c# 7.0 e versioni successive, usare il `is` operatore con [criteri di ricerca](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) per controllare la conversione del tipo ed eseguire il cast l'espressione a una variabile di quel tipo in un unico passaggio.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione di questa regola, modificare l'implementazione del metodo per ridurre al minimo il numero di operazioni cast.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È sicuro per eliminare un avviso da questa regola o di ignorare completamente la regola se le prestazioni non costituiscono un problema.

## <a name="examples"></a>Esempi
 L'esempio seguente illustra un metodo che viola la regola usando il codice c# `is` operatore. Un secondo metodo soddisfa la regola, sostituendo il `is` operatore con il risultato di un test di `as` operatore, che riduce il numero di operazioni di cast per ogni iterazione da due a uno. Un terzo metodo soddisfa anche la regola usando `is` con [criteri di ricerca](/dotnet/csharp/language-reference/keywords/is#pattern-matching-with-is) per creare una variabile del tipo desiderato se la conversione del tipo potrebbe avere esito positivo.

 [!code-csharp[FxCop.Performance.UnnecessaryCastsAsIs#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_1.cs)]

 Nell'esempio seguente viene illustrato un metodo, `start_Click`, che ha più di cast espliciti duplicati, che viola la regola e un metodo, `reset_Click`, che soddisfa la regola, archiviando il cast in una variabile locale.

 [!code-vb[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/VisualBasic/ca1800-do-not-cast-unnecessarily_2.vb)]
 [!code-csharp[FxCop.Performance.UnnecessaryCasts#1](../code-quality/codesnippet/CSharp/ca1800-do-not-cast-unnecessarily_2.cs)]

## <a name="see-also"></a>Vedere anche

- [As (riferimenti per c#)](/dotnet/csharp/language-reference/keywords/as)
- [Is (riferimenti per c#)](/dotnet/csharp/language-reference/keywords/is)