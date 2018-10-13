---
title: 'CA1021: Evitare parametri out | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1021
- AvoidOutParameters
helpviewer_keywords:
- AvoidOutParameters
- CA1021
ms.assetid: 970f2304-842c-4fb7-9734-f3871da8d479
caps.latest.revision: 21
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: d29d80ea45735925a500b1c0b552697644a88d52
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49258752"
---
# <a name="ca1021-avoid-out-parameters"></a>CA1021: Evitare parametri out
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 È possibile eliminare un avviso da questa regola. Tuttavia, questa progettazione potrebbe causare problemi di usabilità.

## <a name="example"></a>Esempio
 La libreria seguente illustra due implementazioni di una classe che genera le risposte ai commenti di un utente. La prima implementazione (`BadRefAndOut`) impone all'utente di libreria per gestire tre valori restituiti. L'implementazione di secondo (`RedesignedRefAndOut`) semplifica l'esperienza utente tramite la restituzione di un'istanza di una classe contenitore (`ReplyData`) che gestisce i dati come una singola unità.

 [!code-csharp[FxCop.Design.NoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NoRefOrOut/cs/FxCop.Design.NoRefOrOut.cs#1)]

## <a name="example"></a>Esempio
 L'applicazione seguente illustra l'esperienza dell'utente. La chiamata alla libreria riprogettata (`UseTheSimplifiedClass` (metodo)) è più semplice, e può essere gestite facilmente le informazioni restituite dal metodo. L'output dei due metodi è identico.

 [!code-csharp[FxCop.Design.TestNoRefOrOut#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestNoRefOrOut/cs/FxCop.Design.TestNoRefOrOut.cs#1)]

## <a name="example"></a>Esempio
 La libreria di esempio seguente viene illustrato come `ref` parametri per i tipi di riferimento vengono usati e viene illustrato un modo migliore per implementare questa funzionalità.

 [!code-csharp[FxCop.Design.RefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.RefByRefNo/cs/FxCop.Design.RefByRefNo.cs#1)]

## <a name="example"></a>Esempio
 La seguente applicazione chiama ogni metodo nella libreria per illustrare il comportamento.

 [!code-csharp[FxCop.Design.TestRefByRefNo#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TestRefByRefNo/cs/FxCop.Design.TestRefByRefNo.cs#1)]

 Questo esempio produce il seguente output:

 **Puntatore di modifica - passati per valore:**
**12345**
**12345**
**puntatore Changing - passato per riferimento:** 
 ** 12345**
**ABCDE 12345**
**passando dal valore restituito:**
**ABCDE 12345**
## <a name="try-pattern-methods"></a>Provare i metodi del modello

### <a name="description"></a>Descrizione
 I metodi che implementano il **provare\<qualcosa >** modello, ad esempio <xref:System.Int32.TryParse%2A?displayProperty=fullName>, non generano questa violazione. L'esempio seguente illustra una struttura (tipo di valore) che implementa il <xref:System.Int32.TryParse%2A?displayProperty=fullName> (metodo).

### <a name="code"></a>Codice
 [!code-csharp[FxCop.Design.TryPattern#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.TryPattern/cs/FxCop.Design.TryPattern.cs#1)]

## <a name="related-rules"></a>Regole correlate
 [CA1045: Non passare i tipi per riferimento](../code-quality/ca1045-do-not-pass-types-by-reference.md)



