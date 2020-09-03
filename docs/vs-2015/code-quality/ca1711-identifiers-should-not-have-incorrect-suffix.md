---
title: 'CA1711: gli identificatori non devono avere un suffisso errato | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
helpviewer_keywords:
- CA1711
- IdentifiersShouldNotHaveIncorrectSuffix
ms.assetid: a63359ab-386d-44ae-b381-ee3a983aca29
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1e753083e9b4bda1e33553021ccb0027a2af2533
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544014"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Gli identificatori non devono contenere un suffisso non corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Elemento|valore|
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Category|Microsoft. Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un suffisso errato.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo i nomi dei tipi che estendono determinati tipi di base o che implementano determinate interfacce, o tipi derivati da questi tipi, devono terminare con suffissi riservati specifici. Gli altri nomi di tipi non devono utilizzare questi suffissi riservati.

 Nella tabella seguente sono elencati i suffissi riservati e i tipi e le interfacce di base a cui sono associati.

|Suffisso|Tipo di base/interfaccia|
|------------|--------------------------|
|Attributo|<xref:System.Attribute?displayProperty=fullName>|
|Raccolta|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dizionario|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Delegato del gestore eventi|
|Eccezione|<xref:System.Exception?displayProperty=fullName>|
|Autorizzazione|<xref:System.Security.IPermission?displayProperty=fullName>|
|Coda|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|
|Flusso|<xref:System.IO.Stream?displayProperty=fullName>|

 Inoltre, **non** usare i suffissi seguenti:

- Delegato

- Enumerazione

- Impl-USA ' core '

- Suffisso ex o simile per distinguerlo da una versione precedente dello stesso tipo

  Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il suffisso dal nome del tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola a meno che il suffisso abbia un significato ambiguo nel dominio dell'applicazione.

## <a name="related-rules"></a>Regole correlate
 [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Vedere anche
 Pennini [attributi](https://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [: eventi e delegati](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
