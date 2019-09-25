---
title: 'CA1045: Non passare i tipi per riferimento'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CA1045
- DoNotPassTypesByReference
helpviewer_keywords:
- CA1045
- DoNotPassTypesByReference
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6a8fda526647a1a9f7f999928cb08978a61bd04
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2019
ms.locfileid: "71235774"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Non passare i tipi per riferimento

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Category|Microsoft.Design|
|Modifica|Interruzione|

## <a name="cause"></a>Causa
Un metodo pubblico o protetto in un tipo pubblico dispone di `ref` un parametro che accetta un tipo primitivo, un tipo di riferimento o un tipo di valore che non è uno dei tipi incorporati.

## <a name="rule-description"></a>Descrizione della regola
Il passaggio di tipi per riferimento `out` ( `ref`tramite o) richiede l'utilizzo di puntatori, la comprensione della differenza tra tipi di valore e tipi di riferimento e la gestione di metodi che hanno più valori restituiti. Inoltre, la differenza tra `out` i `ref` parametri e non è ampiamente riconosciuta.

Quando un tipo di riferimento viene passato "per riferimento", il metodo intende utilizzare il parametro per restituire un'istanza diversa dell'oggetto. Il passaggio di un tipo di riferimento per riferimento è noto anche come utilizzo di un puntatore doppio, puntatore a un puntatore o doppio riferimento indiretto. Utilizzando la convenzione di chiamata predefinita, che viene passata "per valore", un parametro che accetta un tipo di riferimento riceve già un puntatore all'oggetto. Il puntatore, non l'oggetto a cui fa riferimento, viene passato per valore. Il passaggio per valore significa che il metodo non può modificare il puntatore in modo che punti a una nuova istanza del tipo di riferimento, ma può modificare il contenuto dell'oggetto a cui punta. Per la maggior parte delle applicazioni questo è sufficiente e produce il comportamento desiderato.

Se un metodo deve restituire un'istanza diversa, usare il valore restituito del metodo per eseguire questa operazione. Vedere la <xref:System.String?displayProperty=fullName> classe per un'ampia gamma di metodi che operano sulle stringhe e restituiscono una nuova istanza di una stringa. Utilizzando questo modello, viene lasciato al chiamante di decidere se l'oggetto originale viene conservato.

Sebbene i valori restituiti siano comuni e utilizzati molto spesso, l'applicazione `out` corretta `ref` di parametri e richiede competenze di progettazione e codifica intermedie. Gli architetti di librerie che progettano per i destinatari generali non dovrebbero prevedere agli `out` utenti `ref` di usare i parametri o.

> [!NOTE]
> Quando si utilizzano parametri di grandi dimensioni, le risorse aggiuntive necessarie per copiare queste strutture possono causare un effetto sulle prestazioni quando si passa per valore. In questi casi, è possibile prendere in `ref` considerazione `out` l'uso di parametri o.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
Per correggere una violazione di questa regola causata da un tipo di valore, fare in modo che il metodo restituisca l'oggetto come valore restituito. Se il metodo deve restituire più valori, riprogettarlo per restituire una singola istanza di un oggetto che include i valori.

Per correggere una violazione di questa regola causata da un tipo di riferimento, assicurarsi che il comportamento desiderato sia quello di restituire una nuova istanza del riferimento. In tal caso, il metodo deve usare il valore restituito per eseguire questa operazione.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi
È possibile eliminare un avviso da questa regola in modo sicuro; Tuttavia, questo progetto potrebbe causare problemi di usabilità.

## <a name="example"></a>Esempio
La libreria seguente mostra due implementazioni di una classe che genera risposte ai commenti e suggerimenti dell'utente. La prima implementazione (`BadRefAndOut`) forza l'utente della libreria a gestire tre valori restituiti. La seconda implementazione (`RedesignedRefAndOut`) semplifica l'esperienza utente restituendo un'istanza di una classe contenitore (`ReplyData`) che gestisce i dati come una singola unità.

[!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Esempio
Nell'applicazione seguente viene illustrata l'esperienza dell'utente. La chiamata alla libreria riprogettata (`UseTheSimplifiedClass` metodo) è più semplice e le informazioni restituite dal metodo sono facilmente gestibili. L'output dei due metodi è identico.

[!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Esempio
Nella libreria di esempio seguente viene illustrata la modalità `ref` di utilizzo dei parametri per i tipi di riferimento e viene illustrato un modo migliore per implementare questa funzionalità.

[!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Esempio
L'applicazione seguente chiama ogni metodo nella libreria per illustrare il comportamento.

[!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]

Questo esempio produce il seguente output:

```txt
Changing pointer - passed by value:
12345
12345
Changing pointer - passed by reference:
12345
12345 ABCDE
Passing by return value:
12345 ABCDE
```

## <a name="related-rules"></a>Regole correlate
[CA1021: Evitare parametri out](../code-quality/ca1021-avoid-out-parameters.md)