---
title: Analisi del codice per gli avvisi del codice gestito
ms.date: 08/31/2020
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8238de0760f300b6fa418a5e3eb47eac3db77272
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509016"
---
# <a name="net-code-analysis-rules"></a>Regole di analisi del codice .NET
Lo strumento di analisi del codice gestito fornisce avvisi che indicano le violazioni delle regole nelle librerie del codice gestito. Gli avvisi sono organizzati in aree di regole, ad esempio progettazione, localizzazione, prestazioni e sicurezza. Ogni avviso indica una violazione di una regola di analisi del codice gestito. Questa sezione fornisce descrizioni dettagliate ed esempi per ogni avviso di analisi del codice gestito.

 La tabella seguente mostra il tipo di informazioni fornite per ogni avviso.

|Elemento|Descrizione|
|----------|-----------------|
|Type|TypeName per la regola.|
|CheckId|Identificatore univoco per la regola. CheckId e Category vengono usati per l'eliminazione di un avviso nell'origine.|
|Category|Categoria dell'avviso.|
|Modifica|Indica se la correzione di una violazione della regola è una modifica importante. Per modifica importante si intende che un assembly che presenta una dipendenza dalla destinazione che ha causato la violazione non verrà ricompilato con la nuova versione corretta o potrebbe non riuscire in fase di esecuzione a causa della modifica. Quando sono disponibili più correzioni e almeno una correzione è una modifica di rilievo e una correzione non è, vengono specificati sia ' interruzioni ' che ' non-interruzioni '.|
|Causa|Codice gestito specifico che ha fatto sì che la regola generasse un avviso.|
|Descrizione|Descrive i problemi alla base dell'avviso.|
|Come correggere le violazioni|Spiega come modificare il codice sorgente per soddisfare la regola e impedire la generazione di un avviso.|
|Esclusione di avvisi|Descrive quando è possibile eliminare un avviso da questa regola.|
|Codice di esempio|Esempi che violano la regola ed esempi corretti che soddisfano la regola.|
|Avvisi correlati|Avvisi correlati.|

## <a name="in-this-section"></a>Contenuto della sezione

|Category|Descrizione|
|-|-|
|[Regole per ID](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Elenca tutte le regole per RuleID|
|[Regole di progettazione](../code-quality/design-warnings.md)|Regole che supportano la progettazione corretta delle librerie come specificato dalle linee guida di progettazione .NET.|
|[Regole della documentazione](../code-quality/documentation-warnings.md)|Regole che supportano un progetto di libreria ben documentato tramite l'utilizzo corretto di commenti di documentazione XML.|
|[Regole di globalizzazione](../code-quality/globalization-warnings.md)|Regole che supportano applicazioni e librerie internazionali.|
|[Regole di manutenibilità](../code-quality/maintainability-warnings.md)|Regole che supportano la manutenzione di applicazioni e librerie.|
|[Regole di denominazione](../code-quality/naming-warnings.md)|Regole che supportano la conformità alle convenzioni di denominazione delle linee guida di progettazione .NET.|
|[Regole di prestazioni](../code-quality/performance-warnings.md)|Regole che supportano applicazioni e librerie ad alte prestazioni.|
|[Regole di portabilità e interoperabilità](../code-quality/interoperability-warnings.md)|Regole che supportano la portabilità tra piattaforme diverse e l'interazione con i client COM.|
|[Regole di pubblicazione](../code-quality/publish-warnings.md)|Regole che supportano la pubblicazione appropriata di applicazioni .NET.|
|[Regole di affidabilità](../code-quality/reliability-warnings.md)|Regole che supportano l'affidabilità di librerie e applicazioni, ad esempio l'utilizzo corretto di memoria e thread.|
|[Regole di sicurezza](../code-quality/security-warnings.md)|Regole che supportano applicazioni e librerie più sicure.|
|[Regole di utilizzo](../code-quality/usage-warnings.md)|Regole che supportano l'utilizzo appropriato di .NET.|
