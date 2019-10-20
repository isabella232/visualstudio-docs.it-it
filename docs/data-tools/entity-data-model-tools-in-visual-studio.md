---
title: Strumenti di Entity Framework
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 53b87ce39f0eb5b1455f0a38b2aea7cc6b604342
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648522"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Entity Framework Tools in Visual Studio

Entity Framework è una tecnologia di mapping relazionale a oggetti che consente agli sviluppatori .NET di utilizzare i dati relazionali utilizzando oggetti specifici del dominio. In questo modo la maggior parte del codice di accesso ai dati che in genere gli sviluppatori devono scrivere non è più necessaria. Entity Framework è la tecnologia di modellazione ORM (Object-Relational Mapping) consigliata per le nuove applicazioni .NET.

Entity Framework Tools sono progettate per semplificare la compilazione di applicazioni Entity Framework (EF). La documentazione completa per Entity Framework è disponibile qui: [Panoramica-EF 6](/ef/ef6/).

  > [!NOTE]
  > I Entity Framework Tools descritti in questa pagina vengono usati per generare file con *estensione edmx* , che non sono supportati nella EF core. Per generare un modello di EF Core da un database esistente, vedere [Reverse Engineering-EF Core](/ef/core/managing-schemas/scaffolding). Per ulteriori informazioni sulle differenze tra EF 6 e EF Core, vedere [confrontare EF 6 e EF Core](/ef/efcore-and-ef6/).

Con Entity Framework Tools, è possibile creare un *modello concettuale* da un database esistente e quindi visualizzare graficamente e modificare il modello concettuale. È inoltre possibile creare prima graficamente un modello concettuale e successivamente generare un database di supporto al modello. In entrambi i casi, è possibile aggiornare automaticamente il modello quando viene modificato il database sottostante e generare automaticamente codice del livello oggetti per l'applicazione. La generazione del database e del codice del livello oggetti è personalizzabile.

Gli strumenti di Entity Framework vengono installati come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel programma di installazione di Visual Studio. È anche possibile installarli come singolo componente nella categoria **SDK, librerie e Framework** .

Questi sono gli strumenti specifici che compongono Entity Framework strumenti in Visual Studio:

- È possibile utilizzare la **finestra di progettazione [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** (**Entity Designer**) per creare e modificare visivamente entità, associazioni, mapping e relazioni di ereditarietà. Il **Entity Designer** genera anche [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] codice del livello oggetti.

- È possibile utilizzare la **procedura guidata [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)]** per generare un modello concettuale da un database esistente e aggiungere le informazioni di connessione al database all'applicazione.

- È possibile utilizzare la **procedura guidata Crea database** per creare prima un modello concettuale, quindi creare un database che supporti il modello.

- È possibile utilizzare la **procedura guidata Aggiorna modello** per aggiornare il modello concettuale, il modello di archiviazione e i mapping quando sono state apportate modifiche al database sottostante.

  > [!NOTE]
  > A partire da Visual Studio 2010, gli strumenti di Entity Framework non supportano [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Gli strumenti generano o modificano un file con estensione *edmx* . Questo file con *estensione edmx* contiene informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra di essi. Per ulteriori informazioni, vedere [edmx](https://docs.microsoft.com/ef/ef6/).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) consentono di creare applicazioni che usano l'Entity Data Model. Power Tools consente di generare un modello concettuale, convalidare un modello esistente, produrre file del codice sorgente contenenti classi di oggetti basate sul modello concettuale e produrre file del codice sorgente contenenti visualizzazioni generate dal modello. Per informazioni dettagliate, vedere [viste di mapping pre-generate](https://docs.microsoft.com/ef/ef6/fundamentals/performance/pre-generated-views).

## <a name="related-topics"></a>Argomenti correlati

| Titolo | Descrizione |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | Viene descritto come utilizzare gli strumenti di [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)], che [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fornisce, per creare applicazioni. |
| [Entity Data Model](/dotnet/framework/data/adonet/entity-data-model) | Vengono forniti collegamenti e informazioni per l'utilizzo dei dati utilizzati dalle applicazioni basate su [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)]. |
| [Documentazione di Entity Framework (EF))](https://docs.microsoft.com/ef/ef6/get-started) | Fornisce un indice di video, esercitazioni e documentazione avanzata che consentono di sfruttare al meglio le Entity Framework. |
| [ASP.NET 5-applicazione al nuovo database](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Viene descritto come creare una nuova applicazione ASP.NET 5 utilizzando Entity Framework 7. |

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)