---
title: 'CA1707: Gli identificatori non devono contenere caratteri di sottolineatura'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ba9e8dda927edca08565b088cbde90d63443908
ms.sourcegitcommit: 3e94d9fb6dc56fa8b23fbacd5d11cf8d6e7e18f1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/10/2019
ms.locfileid: "72252579"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Gli identificatori non devono contenere caratteri di sottolineatura

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Category|Microsoft.Naming|
|Modifica|Suddivisione in caso di generazione di assembly<br /><br /> Senza interruzioni: quando viene generato un parametro di tipo|

## <a name="cause"></a>Causa

Il nome di un identificatore contiene il carattere di sottolineatura (\_).

## <a name="rule-description"></a>Descrizione della regola

Per convenzione, i nomi degli identificatori non contengono il carattere di sottolineatura (\_). La regola controlla gli spazi dei nomi, i tipi, i membri e i parametri.

Le convenzioni di denominazione forniscono un aspetto comune per le librerie destinate al Common Language Runtime. In questo modo si riduce la curva di apprendimento necessaria per le nuove librerie software e si aumenta la fiducia dei clienti che la libreria è stata sviluppata da un utente esperto nello sviluppo di codice gestito.

## <a name="how-to-fix-violations"></a>Come correggere le violazioni

Rimuovere tutti i caratteri di sottolineatura dal nome.

## <a name="when-to-suppress-warnings"></a>Quando escludere gli avvisi

Non escludere gli avvisi per il codice di produzione. Tuttavia, è possibile evitare di visualizzare questo avviso per il codice di test. È possibile eliminare gli avvisi da questa regola impostando la [gravità](use-roslyn-analyzers.md#rule-severity) su **None**. 

## <a name="related-rules"></a>Regole correlate

- [CA1709: La combinazione di maiuscole e minuscole degli identificatori deve essere corretta @ no__t-0
- [CA1708: Gli identificatori devono differire più del caso @ no__t-0
