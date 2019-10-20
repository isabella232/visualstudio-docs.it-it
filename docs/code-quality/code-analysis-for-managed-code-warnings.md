---
title: Analisi del codice per gli avvisi del codice gestito
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vc.project.vcfxcoptool.enablefxcop
helpviewer_keywords:
- managed code analyis, warnings
- warnings, managed code analysis
- managed code analysis warnings
- code analysis,managed code
ms.assetid: 3c2741ff-0d3a-42e6-acd5-d42310bd03c4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 8fbc5bbb596cc7b790ea456b22a24b582e1b609a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72622455"
---
# <a name="code-analysis-for-managed-code-warnings"></a>Analisi del codice per gli avvisi del codice gestito
Lo strumento di analisi del codice gestito fornisce avvisi che indicano le violazioni delle regole nelle librerie del codice gestito. Gli avvisi sono organizzati in aree di regole, ad esempio progettazione, localizzazione, prestazioni e sicurezza. Ogni avviso indica una violazione di una regola di analisi del codice gestito. Questa sezione fornisce descrizioni dettagliate ed esempi per ogni avviso di analisi del codice gestito.

 La tabella seguente mostra il tipo di informazioni fornite per ogni avviso.

|Elemento|Descrizione|
|----------|-----------------|
|Digitare|TypeName per la regola.|
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

|||
|-|-|
|[Avvisi generati da CheckId](../code-quality/code-analysis-warnings-for-managed-code-by-checkid.md)|Elenchi di tutti gli avvisi generati da CheckId|
|[Avvisi di crittografia](../code-quality/cryptography-warnings.md)|Avvisi che supportano applicazioni e librerie più sicure attraverso l'uso corretto della crittografia.|
|[Avvisi di progettazione](../code-quality/design-warnings.md)|Avvisi che supportano la progettazione corretta della libreria come specificato dalle linee guida di progettazione .NET.|
|[Avvisi di documentazione](../code-quality/documentation-warnings.md)|Avvisi che supportano la progettazione di librerie ben documentate mediante l'utilizzo corretto di commenti di documentazione XML.|
|[Avvisi di globalizzazione](../code-quality/globalization-warnings.md)|Avvisi che supportano applicazioni e librerie internazionalizzate.|
|[Avvisi di interoperabilità](../code-quality/interoperability-warnings.md)|Avvisi che supportano l'interazione con i client COM.|
|[Avvisi di manutenibilità](../code-quality/maintainability-warnings.md)|Avvisi che supportano la manutenzione di applicazioni e librerie.|
|[Mobility Warnings](../code-quality/mobility-warnings.md)|Avvisi che supportano l'utilizzo efficiente dell'energia.|
|[Avvisi di denominazione](../code-quality/naming-warnings.md)|Avvisi che supportano la conformità alle convenzioni di denominazione delle linee guida di progettazione .NET.|
|[Avvisi di prestazioni](../code-quality/performance-warnings.md)|Avvisi che supportano applicazioni e librerie ad alte prestazioni.|
|[Avvisi di portabilità](../code-quality/portability-warnings.md)|Avvisi che supportano la portabilità tra piattaforme diverse.|
|[Avvisi di affidabilità](../code-quality/reliability-warnings.md)|Avvisi che supportano l'affidabilità di applicazioni e librerie, ad esempio il corretto utilizzo di memoria e thread.|
|[Avvisi di sicurezza](../code-quality/security-warnings.md)|Avvisi che supportano applicazioni e librerie più sicure.|
|[Avvisi di utilizzo](../code-quality/usage-warnings.md)|Avvisi che supportano l'utilizzo appropriato di .NET.|
|[Errori dei criteri per l'analisi del codice](../code-quality/code-analysis-policy-errors.md)|Errori che si verificano se i criteri di analisi del codice non sono soddisfatti al momento dell'archiviazione.|
