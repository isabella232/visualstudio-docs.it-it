---
title: 'CA1711: Gli identificatori non devono contenere il suffisso corretto | Microsoft Docs'
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
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 39e6a0f0019d05a3c93b5473e94eefca26bb8e29
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966457"
---
# <a name="ca1711-identifiers-should-not-have-incorrect-suffix"></a>CA1711: Gli identificatori non devono contenere un suffisso non corretto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectSuffix|
|CheckId|CA1711|
|Category|Microsoft.Naming|
|Modifica importante|Interruzione|

## <a name="cause"></a>Causa
 Un identificatore ha un suffisso non corretto.

## <a name="rule-description"></a>Descrizione della regola
 Per convenzione, solo i nomi dei tipi che estendono determinati tipi di base o implementano determinate interfacce o dei tipi derivati da questi tipi devono terminare con suffissi specifici riservati. Gli altri nomi di tipi non devono utilizzare questi suffissi riservati.

 La tabella seguente elenca i suffissi riservati e i tipi di base e interfacce a cui sono associate.

|Suffisso|Interfaccia di tipo di base|
|------------|--------------------------|
|Attributo|<xref:System.Attribute?displayProperty=fullName>|
|Raccolta|<xref:System.Collections.ICollection?displayProperty=fullName><br /><br /> <xref:System.Collections.IEnumerable?displayProperty=fullName><br /><br /> <xref:System.Collections.Queue?displayProperty=fullName><br /><br /> <xref:System.Collections.Stack?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.ICollection%601?displayProperty=fullName><br /><br /> <xref:System.Data.DataSet?displayProperty=fullName><br /><br /> <xref:System.Data.DataTable?displayProperty=fullName>|
|Dizionario|<xref:System.Collections.IDictionary?displayProperty=fullName><br /><br /> <xref:System.Collections.Generic.IDictionary%602?displayProperty=fullName>|
|EventArgs|<xref:System.EventArgs?displayProperty=fullName>|
|EventHandler|Un delegato del gestore eventi|
|Eccezione|<xref:System.Exception?displayProperty=fullName>|
|Autorizzazioni|<xref:System.Security.IPermission?displayProperty=fullName>|
|Coda|<xref:System.Collections.Queue?displayProperty=fullName>|
|Stack|<xref:System.Collections.Stack?displayProperty=fullName>|
|Flusso|<xref:System.IO.Stream?displayProperty=fullName>|

 Inoltre, i suffissi seguenti dovrebbero **non** utilizzabili:

- delegato

- Enum

- Impl - in alternativa, usare 'Core'

- Ad esempio o il suffisso simile per distinguerlo da una versione precedente dello stesso tipo

  Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente con competenze nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni
 Rimuovere il suffisso dal nome del tipo.

## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi
 Non eliminare un avviso da questa regola a meno che il suffisso abbia un significato ambiguo nel dominio dell'applicazione.

## <a name="related-rules"></a>Regole correlate
 [CA1710: Gli identificatori devono contenere il suffisso corretto](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)

## <a name="see-also"></a>Vedere anche
 [Gli attributi](http://msdn.microsoft.com/library/ee0038ef-b247-4747-a650-3c5c5cd58d8b) [NIB: Eventi e delegati](http://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)
