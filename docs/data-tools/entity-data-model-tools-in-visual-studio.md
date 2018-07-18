---
title: Strumenti di Entity Framework in Visual Studio
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3209a79b0358471977a0e58e8ab5d8d7e5c08e07
ms.sourcegitcommit: 30f653d9625ba763f6b58f02fb74a24204d064ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2018
ms.locfileid: "36755368"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Strumenti di Entity Framework in Visual Studio
Entity Framework è una tecnologia di mapping relazionale a oggetti che consente agli sviluppatori .NET di utilizzare dati relazionali mediante oggetti specifici di dominio. In questo modo la maggior parte del codice di accesso ai dati che in genere gli sviluppatori devono scrivere non è più necessaria. Entity Framework è il consigliato object relational mapping (ORM) modellazione tecnologia per le nuove applicazioni .NET.

Strumenti di Entity Framework sono progettati per la compilazione di applicazioni Entity Framework (EF). La documentazione completa per Entity Framework è qui: [EF Core ed Entity Framework 6](/ef/).

Con strumenti di Entity Framework, è possibile creare un *del modello concettuale* da un oggetto esistente del database e quindi graficamente visualizzare e modificare il modello concettuale. È inoltre possibile creare prima graficamente un modello concettuale e successivamente generare un database di supporto al modello. In entrambi i casi, è possibile aggiornare automaticamente il modello quando viene modificato il database sottostante e generare automaticamente codice del livello oggetti per l'applicazione. La generazione del database e del codice del livello oggetti è personalizzabile.

Strumenti di Entity Framework vengono installati come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer. È inoltre possibile installarli come componente singoli con il **SDK, librerie e Framework** categoria.

Questi sono gli strumenti specifici che costituiscono gli strumenti di Entity Framework in Visual Studio:

-   È possibile usare la [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)]  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] progettazione** (**Entity Designer**) per creare visivamente e modificare le entità, associazioni, mapping e relazioni di ereditarietà. Il **Entity Designer** genera inoltre [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] codice del livello oggetti.

-   È possibile usare la  **[!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] guidata** per generare un modello concettuale da un database esistente e aggiungere le informazioni di connessione di database all'applicazione.

-   È possibile usare la **procedura guidata Crea Database** creare prima un modello concettuale e quindi creare un database che supporta il modello.

-   È possibile usare la **procedura guidata Aggiorna modello** per aggiornare il modello concettuale, un modello di archiviazione e un mapping quando sono state apportate modifiche al database sottostante.

    > [!NOTE]
    >  A partire da Visual Studio 2010, strumenti di Entity Framework non supportano [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)].

Gli strumenti generano o modificano un' *edmx* file. Ciò *edmx* file contiene informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra di essi. Per altre informazioni, vedere [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) consentono di compilare applicazioni che usano Entity Data Model. I power tools può generare un modello concettuale, convalidare un modello esistente, produrre file del codice sorgente contenenti classi di oggetti basate sul modello concettuale e produrre file del codice sorgente contenenti visualizzazioni generate dal modello. Per informazioni dettagliate, vedere [Pre-Generated Mapping viste](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index)|Viene descritto come utilizzare [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] strumenti di cui [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] fornisce, per creare applicazioni.|
|[Entity Data Model](/dotnet/framework/data/adonet/entity-data-model)|Fornisce collegamenti e informazioni per l'utilizzo di dati utilizzati dalle applicazioni compilate in [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)].|
|[Documentazione di Entity Framework (EF))](https://msdn.microsoft.com/library/ee712907(v=vs.113).aspx)|Fornisce un indice dei video, esercitazioni e documentazione avanzata che consentono di sfruttare al meglio di Entity Framework.|
|[ASP.NET 5 dell'applicazione al nuovo Database](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Viene descritto come creare una nuova applicazione ASP.NET 5 usando Entity Framework 7.|

## <a name="see-also"></a>Vedere anche

- [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)