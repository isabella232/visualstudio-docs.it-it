---
title: 'CA1021: Evitare parametri out'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: reference
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f654af804ea48089a3a27e154d70c118b22fecb7
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54957754"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Evitare parametri out

|||
|-|-|
|TypeName|AvoidOutParameters|
|CheckId|CA1021|
|Category|Microsoft.Design|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un metodo pubblico o protetto in un tipo pubblico presenta un `out` parametro.

## <a name="rule-description"></a>Descrizione della regola
 Passaggio di tipi per riferimento (utilizzando `out` o `ref`) richiede esperienza nell'utilizzo dei puntatori, informazioni sulle differiscano tra i tipi di valore e tipi di riferimento e gestione dei metodi con più valori restituiti. Inoltre, la differenza tra `out` e `ref` parametri non è stato ampiamente riconosciuto.

 Quando viene passato un tipo di riferimento "riferimento", il metodo è intenzione di usare il parametro per restituire un'istanza diversa dell'oggetto. Passaggio di un tipo di riferimento per riferimento è noto anche come usando un puntatore, un puntatore a un puntatore o un riferimento indiretto doppio double. Utilizzando la convenzione di chiamata, ovvero il passaggio "dal valore", un parametro che accetta un tipo riferimento già riceve un puntatore all'oggetto. Il puntatore, non l'oggetto a cui fa riferimento, viene passato per valore. Passaggio per valore significa che il metodo non è possibile modificare il puntatore per puntare a una nuova istanza del tipo di riferimento. Tuttavia, è possibile modificare il contenuto dell'oggetto a cui punta. Per la maggior parte delle applicazioni si sia sufficiente e produce il comportamento desiderato.

 Se un metodo deve restituire un'istanza diversa, usare il valore restituito del metodo per eseguire questa operazione. Vedere il <xref:System.String?displayProperty=fullName> classe per un'ampia gamma di metodi che vengono eseguite su stringhe e restituire una nuova istanza di una stringa. Quando viene usato questo modello, il chiamante deve decidere se l'oggetto originale viene mantenuto.

 Sebbene i valori restituiti siano comuni e usati molto, la corretta applicazione delle `out` e `ref` parametri richiede la progettazione intermedi e le competenze di codifica. Libreria gli architetti per un pubblico generico non possono prevedere agli utenti di utilizzare i `out` o `ref` parametri.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Per correggere una violazione della regola che è dovuta a un tipo di valore, dispone del metodo restituisca l'oggetto come relativo valore restituito. Se il metodo deve restituire più valori, riprogettare per la restituzione di una singola istanza di un oggetto che contiene i valori.

 Per correggere una violazione della regola che è dovuta a un tipo riferimento, assicurarsi che il comportamento desiderato deve restituire una nuova istanza del riferimento. Se si tratta, il metodo deve usare il valore restituito corrispondente a tale scopo.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, questa progettazione potrebbe causare problemi di usabilità.

## <a name="example"></a>Esempio
 La libreria seguente illustra due implementazioni di una classe che genera le risposte ai commenti di un utente. La prima implementazione (`BadRefAndOut`) impone all'utente di libreria per gestire tre valori restituiti. L'implementazione di secondo (`RedesignedRefAndOut`) semplifica l'esperienza utente tramite la restituzione di un'istanza di una classe contenitore (`ReplyData`) che gestisce i dati come una singola unità.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_1.cs)]

## <a name="example"></a>Esempio
 L'applicazione seguente illustra l'esperienza dell'utente. La chiamata alla libreria riprogettata (`UseTheSimplifiedClass` (metodo)) è più semplice, e può essere gestite facilmente le informazioni restituite dal metodo. L'output dei due metodi è identico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_2.cs)]

## <a name="example"></a>Esempio
 La libreria di esempio seguente viene illustrato come `ref` parametri per i tipi di riferimento vengono usati e viene illustrato un modo migliore per implementare questa funzionalità.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_3.cs)]

## <a name="example"></a>Esempio
 La seguente applicazione chiama ogni metodo nella libreria per illustrare il comportamento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_4.cs)]

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

## <a name="try-pattern-methods"></a>Provare i metodi del modello

### <a name="description"></a>Descrizione
 I metodi che implementano il **provare\<qualcosa >** modello, ad esempio <xref:System.Int32.TryParse%2A?displayProperty=fullName>, non generano questa violazione. L'esempio seguente illustra una struttura (tipo di valore) che implementa il <xref:System.Int32.TryParse%2A?displayProperty=fullName> (metodo).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.TryPattern#1](../code-quality/codesnippet/CSharp/ca1021-avoid-out-parameters_5.cs)]

## <a name="related-rules"></a>Regole correlate
 [CA1045: Non passare tipi per riferimento](../code-quality/ca1045-do-not-pass-types-by-reference.md)