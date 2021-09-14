---
title: Strumenti di Entity Framework
description: Informazioni Entity Framework Tools in Visual Studio. Entity Framework Tools sono progettati per facilitare la compilazione di Entity Framework (EF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 28a703518405bfedd4a786a583e8688dcb7db134
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631403"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools in Visual Studio

Entity Framework è una tecnologia di mapping relazionale a oggetti che consente agli sviluppatori .NET di usare dati relazionali usando oggetti specifici di dominio. Elimina la necessità di gran parte del codice di accesso ai dati che in genere gli sviluppatori devono scrivere. Entity Framework è la tecnologia di modellazione ORM (Object-Relational Mapping) consigliata per le nuove applicazioni .NET.

Entity Framework Tools sono progettati per facilitare la compilazione di Entity Framework (EF). La documentazione completa per Entity Framework è disponibile qui: [Panoramica - EF 6.](/ef/ef6/)

  > [!NOTE]
  > Le Entity Framework Tools descritte in questa pagina vengono usate per generare file con estensione *edmx,* che non sono supportati in EF Core. Per generare un modello EF Core da un database esistente, vedere [Reverse Engineering - EF Core](/ef/core/managing-schemas/scaffolding). Per altre informazioni sulle differenze tra EF 6 e EF Core, vedere [Confrontare EF 6 e EF Core](/ef/efcore-and-ef6/).

Con Entity Framework Tools, è possibile creare *un* modello concettuale da un database esistente e quindi visualizzare e modificare graficamente il modello concettuale. È inoltre possibile creare prima graficamente un modello concettuale e successivamente generare un database di supporto al modello. In entrambi i casi, è possibile aggiornare automaticamente il modello quando viene modificato il database sottostante e generare automaticamente codice del livello oggetti per l'applicazione. La generazione del database e del codice del livello oggetti è personalizzabile.

Gli Entity Framework vengono installati come parte  del carico di lavoro Elaborazione ed archiviazione dati nel Programma di installazione di Visual Studio. È anche possibile installarli come singoli componenti nella categoria **SDK, librerie e framework.**

Questi sono gli strumenti specifici che costituiscono Entity Framework strumenti in Visual Studio:

- È possibile usare Progettazione ( Entity Designer ) per creare e modificare visivamente [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** entità, associazioni, mapping e relazioni diereditarietà. Il **Entity Designer** genera anche [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] il codice a livello di oggetto o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] .

- È possibile usare la procedura **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] guidata per** generare un modello concettuale da un database esistente e aggiungere le informazioni di connessione del database all'applicazione.

- È possibile utilizzare la **Creazione guidata database** per creare prima un modello concettuale e quindi creare un database che supporta il modello.

- È possibile usare **l'Aggiornamento guidato modelli** per aggiornare il modello concettuale, il modello di archiviazione e i mapping quando sono state apportate modifiche al database sottostante.

  > [!NOTE]
  > A partire Visual Studio 2010, Entity Framework non supportano [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] .

Gli strumenti generano o modificano un file *con estensione edmx.* Questo file *con estensione edmx* contiene informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra di essi. Per altre informazioni, vedere [EDMX.](/ef/ef6/)

[Entity Framework Power Tools consente](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) di creare applicazioni che usano il Entity Data Model. Gli strumenti avanzati possono generare un modello concettuale, convalidare un modello esistente, produrre file di codice sorgente contenenti classi di oggetti basate sul modello concettuale e generare file di codice sorgente contenenti visualizzazioni generate dal modello. Per informazioni dettagliate, vedere [Visualizzazioni di mapping pre-generate.](/ef/ef6/fundamentals/performance/pre-generated-views)

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Viene descritto come utilizzare [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] gli strumenti forniti da per creare [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] applicazioni. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Fornisce collegamenti e informazioni per l'utilizzo dei dati utilizzati dalle applicazioni compilate in [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] . |
| [Entity Framework (EF) Documentation)](/ef/ef6/get-started) | Fornisce un indice di video, esercitazioni e documentazione avanzata che consentono di ottenere il massimo Entity Framework. |
| [ASP.NET 5 da applicazione a nuovo database](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Viene descritto come creare una nuova ASP.NET 5 usando Entity Framework 7. |

## <a name="see-also"></a>Vedi anche

- [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
