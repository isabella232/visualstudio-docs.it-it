---
title: 'CA1710: gli identificatori devono contenere il suffisso corretto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7dc0ed72ddab39bda5f3de9b978f4d55dc2358ba
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669160"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Gli identificatori devono contenere il suffisso corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore non ha il suffisso corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce, o tipi derivati da questi tipi, hanno un suffisso associato al tipo o all'interfaccia di base.

 Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

 Nella tabella seguente sono elencati i tipi di base e le interfacce con suffissi associati.

|Tipo di base/interfaccia|Suffisso|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attributo|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Eccezione|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dizionario|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.Queue?displayProperty=fullName>|Raccolta o coda|
|<xref:System.Collections.Stack?displayProperty=fullName>|Raccolta o stack|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dizionario|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Raccolta o DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Flusso|
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorizzazioni|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condizione|
|Delegato del gestore eventi.|EventHandler|

 I tipi che implementano <xref:System.Collections.ICollection> e sono un tipo generalizzato di struttura di dati, ad esempio un dizionario, uno stack o una coda, sono nomi consentiti che forniscono informazioni significative sull'utilizzo previsto del tipo.

 I tipi che implementano <xref:System.Collections.ICollection> e sono una raccolta di elementi specifici hanno nomi che terminano con la parola ' Collection '. Ad esempio, una raccolta di oggetti <xref:System.Collections.Queue> avrebbe il nome ' QueueCollection '. Il suffisso ' Collection ' indica che i membri della raccolta possono essere enumerati usando l'istruzione `foreach` (`For Each` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]).

 I tipi che implementano <xref:System.Collections.IDictionary> hanno nomi che terminano con la parola ' Dictionary ' anche se il tipo implementa anche <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>. Le convenzioni di denominazione dei suffissi "Collection" e "Dictionary" consentono agli utenti di distinguere tra i due modelli di enumerazione seguenti.

 I tipi con il suffisso ' Collection ' seguono questo modello di enumerazione.

```
foreach(SomeType x in SomeCollection) { }
```

 I tipi con il suffisso ' Dictionary ' seguono questo modello di enumerazione.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

 Un oggetto <xref:System.Data.DataSet> è costituito da una raccolta di oggetti <xref:System.Data.DataTable>, che sono costituiti da raccolte di oggetti <xref:System.Data.DataColumn?displayProperty=fullName> e <xref:System.Data.DataRow?displayProperty=fullName>, tra gli altri. Queste raccolte implementano <xref:System.Collections.ICollection> tramite la classe di base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName>.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rinominare il tipo in modo da consentirne il suffisso con il termine corretto.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Se il tipo è una struttura di dati generalizzata che può essere estesa o che conterrà un set arbitrario di elementi diversi, è possibile evitare l'eliminazione di un avviso per l'utilizzo del suffisso ' Collection '. In questo caso, può essere utile un nome che fornisce informazioni significative sull'implementazione, sulle prestazioni o su altre caratteristiche della struttura dei dati, ad esempio BinaryTree. Nei casi in cui il tipo rappresenta una raccolta di un tipo specifico (ad esempio, StringCollection), non eliminare un avviso da questa regola perché il suffisso indica che il tipo può essere enumerato usando un'istruzione `foreach`.

 Per gli altri suffissi, non eliminare un avviso da questa regola. Il suffisso consente all'utilizzo previsto di essere evidente dal nome del tipo.

## <a name="related-rules"></a>Regole correlate
 [CA1711: Gli identificatori non devono contenere un suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Vedere anche
 Pennini [attributi](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [: eventi e delegati](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
