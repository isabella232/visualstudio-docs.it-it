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
ms.openlocfilehash: 1f64a7f7c018863e85900da2b09e018d29da4dfe
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922875"
---
# <a name="ca1045-do-not-pass-types-by-reference"></a>CA1045: Non passare i tipi per riferimento

|||
|-|-|
|TypeName|DoNotPassTypesByReference|
|CheckId|CA1045|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta un `ref` parametro che accetta un tipo primitivo, un tipo riferimento o un tipo di valore che non è uno dei tipi incorporati.

## <a name="rule-description"></a>Descrizione della regola
 Passaggio di tipi per riferimento (utilizzando `out` o `ref`) richiede esperienza nell'utilizzo dei puntatori, informazioni sulle differiscano tra i tipi di valore e tipi di riferimento e gestione dei metodi che hanno più valori restituiti. Inoltre, la differenza tra `out` e `ref` parametri non è stato ampiamente riconosciuto.

 Quando viene passato un tipo di riferimento "riferimento", il metodo è intenzione di usare il parametro per restituire un'istanza diversa dell'oggetto. (Passaggio di un tipo di riferimento per riferimento è noto anche come usando un puntatore, un puntatore a un puntatore o un riferimento indiretto doppio doppio.) Usando il valore predefinito di convenzione di chiamata, ovvero il passaggio "dal valore", un parametro che accetta un tipo riferimento già riceve un puntatore all'oggetto. Il puntatore, non l'oggetto a cui fa riferimento, viene passato per valore. Il passaggio per valore significa che il metodo non è possibile modificare il puntatore per puntare a una nuova istanza del riferimento al tipo, ma è possibile modificare il contenuto dell'oggetto a cui punta. Per la maggior parte delle applicazioni si sia sufficiente e produce il comportamento desiderato.

 Se un metodo deve restituire un'istanza diversa, usare il valore restituito del metodo per eseguire questa operazione. Vedere il <xref:System.String?displayProperty=fullName> classe per un'ampia gamma di metodi che vengono eseguite su stringhe e restituire una nuova istanza di una stringa. Usando questo modello, questa viene lasciata al chiamante per decidere se l'oggetto originale viene mantenuto.

 Sebbene i valori restituiti siano comuni e usati molto, la corretta applicazione delle `out` e `ref` parametri richiede la progettazione intermedi e le competenze di codifica. Libreria gli architetti per un pubblico generico non possono prevedere agli utenti di utilizzare i `out` o `ref` parametri.

> [!NOTE]
>  Quando si lavora con i parametri che sono strutture di grandi dimensioni, le risorse aggiuntive necessarie per copiare queste strutture potrebbe causare un effetto sulle prestazioni quando si passa per valore. In questi casi, è possibile considerare l'uso `ref` o `out` parametri.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione della regola che è dovuta a un tipo di valore, dispone del metodo restituisca l'oggetto come relativo valore restituito. Se il metodo deve restituire più valori, riprogettare per la restituzione di una singola istanza di un oggetto che contiene i valori.

 Per correggere una violazione della regola che è dovuta a un tipo riferimento, assicurarsi che il comportamento desiderato deve restituire una nuova istanza del riferimento. Se si tratta, il metodo deve usare il valore restituito corrispondente a tale scopo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, questa progettazione potrebbe causare problemi di usabilità.

## <a name="example"></a>Esempio
 La libreria seguente illustra due implementazioni di una classe che genera le risposte per i commenti e suggerimenti dell'utente. La prima implementazione (`BadRefAndOut`) impone all'utente di libreria per gestire tre valori restituiti. L'implementazione di secondo (`RedesignedRefAndOut`) semplifica l'esperienza utente tramite la restituzione di un'istanza di una classe contenitore (`ReplyData`) che gestisce i dati come una singola unità.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]

## <a name="example"></a>Esempio
 L'applicazione seguente illustra l'esperienza dell'utente. La chiamata alla libreria riprogettata (`UseTheSimplifiedClass` (metodo)) è più semplice, e può essere gestite facilmente le informazioni restituite dal metodo. L'output dei due metodi è identico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]

## <a name="example"></a>Esempio
 La libreria di esempio seguente viene illustrato come `ref` vengono usati i parametri per i tipi di riferimento e viene illustrato un modo migliore per implementare questa funzionalità.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]

## <a name="example"></a>Esempio
 La seguente applicazione chiama ogni metodo nella libreria per illustrare il comportamento.

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