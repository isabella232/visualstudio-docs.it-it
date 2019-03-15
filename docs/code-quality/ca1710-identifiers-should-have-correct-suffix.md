---
title: 'CA1710: Gli identificatori devono contenere il suffisso corretto'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- CA1710
- IdentifiersShouldHaveCorrectSuffix
helpviewer_keywords:
- IdentifiersShouldHaveCorrectSuffix
- CA1710
ms.assetid: 2b8e6dce-b4e8-4a66-ba9a-6b79be5bfe8c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 65ac417476752da832e5e9ebe693f6c83a5c1cfe
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/14/2019
ms.locfileid: "57868075"
---
# <a name="ca1710-identifiers-should-have-correct-suffix"></a>CA1710: Gli identificatori devono contenere il suffisso corretto

|||
|-|-|
|TypeName|IdentifiersShouldHaveCorrectSuffix|
|CheckId|CA1710|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa

Un identificatore non è il suffisso corretto.

Per impostazione predefinita, questa regola solo esamina gli identificatori visibili esternamente, ma si tratta [configurabile](#configurability).

## <a name="rule-description"></a>Descrizione della regola

Per convenzione, i nomi dei tipi che estendono determinati tipi di base o implementano determinate interfacce o dei tipi derivati da questi tipi hanno un suffisso che è associato il tipo di base o interfaccia.

Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

Nella tabella seguente sono elencati i tipi di base e interfacce che sono associati i suffissi.

|Interfaccia di tipo di base|Suffisso|
|--------------------------|------------|
|<xref:System.Attribute?displayProperty=fullName>|Attributo|
|<xref:System.EventArgs?displayProperty=fullName>|EventArgs|
|<xref:System.Exception?displayProperty=fullName>|Eccezione|
|<xref:System.Collections.ICollection?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.IDictionary?displayProperty=fullName>|Dizionario|
|<xref:System.Collections.IEnumerable?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.Queue?displayProperty=fullName>|Raccolta o una coda|
|<xref:System.Collections.Stack?displayProperty=fullName>|Raccolta o dello Stack|
|<xref:System.Collections.Generic.ICollection%601?displayProperty=fullName>|Raccolta|
|<xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|Dizionario|
|<xref:System.Data.DataSet?displayProperty=fullName>|DataSet|
|<xref:System.Data.DataTable?displayProperty=fullName>|Insieme o DataTable|
|<xref:System.IO.Stream?displayProperty=fullName>|Flusso|
|<xref:System.Security.IPermission?displayProperty=fullName>|Autorizzazioni|
|<xref:System.Security.Policy.IMembershipCondition?displayProperty=fullName>|Condizione|
|Un delegato del gestore eventi.|EventHandler|

I tipi che implementano <xref:System.Collections.ICollection> e sono un tipo generalizzato della struttura di dati, ad esempio un dizionario, stack o coda, sono consentiti nomi che forniscono informazioni significative relative all'utilizzo previsto del tipo.

I tipi che implementano <xref:System.Collections.ICollection> e sono una raccolta di elementi specifici hanno nomi che terminano con la parola 'Collection'. Ad esempio, una raccolta di <xref:System.Collections.Queue> oggetti sarebbe necessario il nome "QueueCollection". Il suffisso 'Collection' indica che i membri della raccolta possono essere enumerati usando il `foreach` (`For Each` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) istruzione.

I tipi che implementano <xref:System.Collections.IDictionary> presentano nomi che terminano con la parola 'Dizionario' anche se il tipo implementa inoltre <xref:System.Collections.IEnumerable> o <xref:System.Collections.ICollection>. Le convenzioni di denominazione suffisso 'Collection' e 'Dizionario' consentono agli utenti di distinguere tra i seguenti due modelli di enumerazione.

Tipi con il suffisso 'Collection' seguono questo modello di enumerazione.

```
foreach(SomeType x in SomeCollection) { }
```

I tipi con il suffisso 'Dizionario' seguono questo modello di enumerazione.

```
foreach(SomeType x in SomeDictionary.Values) { }
```

Oggetto <xref:System.Data.DataSet> oggetto è costituito da una raccolta di <xref:System.Data.DataTable> oggetti, costituiti da raccolte di <xref:System.Data.DataColumn?displayProperty=fullName> e <xref:System.Data.DataRow?displayProperty=fullName> oggetti, tra gli altri. Questi insiemi implementano <xref:System.Collections.ICollection> tramite la base <xref:System.Data.InternalDataCollectionBase?displayProperty=fullName> classe.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rinominare il tipo in modo da utilizzare come suffisso con il termine corretto.

## <a name="when-to-suppress-warnings"></a>Soppressione degli avvisi

È possibile eliminare un avviso da usare il suffisso 'Collection' se il tipo è una struttura di dati generalizzata che può essere estesa o che conterrà un set arbitrario di elementi diversi. In questo caso, un nome che fornisce informazioni significative sull'implementazione, prestazioni o altre caratteristiche della struttura dei dati potrebbe BinaryTree (ad esempio,). Nei casi in cui il tipo rappresenta una raccolta di un tipo specifico (ad esempio, StringCollection), non escludere un avviso da questa regola poiché il suffisso indica che il tipo può essere enumerato usando un `foreach` istruzione.

Per altri suffissi, non escludere un avviso da questa regola. Il suffisso consente l'utilizzo previsto sia evidente dal nome del tipo.

## <a name="configurability"></a>Configurabilità

Se si esegue la regola dai [analizzatori FxCop](install-fxcop-analyzers.md) (e non tramite analisi statica del codice), è possibile configurare quali parti della codebase per l'esecuzione di questa regola, in base i criteri di accesso. Ad esempio, per specificare che la regola deve essere eseguito solo per la superficie dell'API non pubblici, aggiungere la coppia chiave-valore seguente a un file con estensione editorconfig nel progetto:

```
dotnet_code_quality.ca1710.api_surface = private, internal
```

È possibile configurare questa opzione per questa regola, per tutte le regole o per tutte le regole in questa categoria (denominazione). Per altre informazioni, vedere [analizzatori FxCop configurare](configure-fxcop-analyzers.md).

## <a name="related-rules"></a>Regole correlate

[CA1711: Gli identificatori non devono contenere il suffisso non corretto](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)

## <a name="see-also"></a>Vedere anche

- [Attributi](/dotnet/standard/design-guidelines/attributes)
- [La gestione e generazione di eventi](/dotnet/standard/events/index)