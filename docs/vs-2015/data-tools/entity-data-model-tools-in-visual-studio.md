---
title: Strumenti di Entity Data Model
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5f44b44cb0aa2d574d81fd63ef8541c25a4c2453
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "59001638"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Strumenti di Entity Data Model in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]


Entity Framework è una tecnologia di mapping relazionale a oggetti che consente agli sviluppatori .NET di utilizzare dati relazionali mediante oggetti specifici di dominio. In questo modo la maggior parte del codice di accesso ai dati che in genere gli sviluppatori devono scrivere non è più necessaria. Entity Framework è il consigliato object relational mapping (ORM) modellazione tecnologia per le nuove applicazioni .NET.

 A partire da marzo 2016, è la versione rilasciata più recente [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) è disponibile in versione non definitiva.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Gli strumenti sono progettati per facilitare la compilazione [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] applicazioni. La documentazione completa per [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Tools è qui: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Con [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] degli strumenti, è possibile creare un *del modello concettuale* da un oggetto esistente del database e quindi graficamente visualizzare e modificare il modello concettuale. È inoltre possibile creare prima graficamente un modello concettuale e successivamente generare un database di supporto al modello. In entrambi i casi, è possibile aggiornare automaticamente il modello quando viene modificato il database sottostante e generare automaticamente codice del livello oggetti per l'applicazione. La generazione del database e del codice del livello oggetti è personalizzabile.

 Questi sono gli strumenti specifici che costituiscono Entity Data Model Tools in Visual Studio 2015:

- È possibile usare la [!INCLUDE[vstecado](../includes/vstecado-md.md)]  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] progettazione** (**Entity Designer**) per creare visivamente e modificare le entità, associazioni, mapping e relazioni di ereditarietà. Il **Entity Designer** genera inoltre [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] o [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] codice del livello oggetti.

- È possibile usare la  **[!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] guidata** per generare un modello concettuale da un database esistente e aggiungere le informazioni di connessione di database all'applicazione.

- È possibile usare la **procedura guidata Crea Database** creare prima un modello concettuale e quindi creare un database che supporta il modello.

- È possibile usare la **procedura guidata Aggiorna modello** per aggiornare il modello concettuale, un modello di archiviazione e un mapping quando sono state apportate modifiche al database sottostante.

  > [!NOTE]
  >  A partire da Visual Studio 2010 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] strumenti potrebbero non supportare [!INCLUDE[ss2k](../includes/ss2k-md.md)].

  Gli strumenti generano o modificare un file con estensione edmx. Questo file contiene informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra di essi. Per altre informazioni, vedere [EDMX](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools consentono di compilare applicazioni che usano Entity Data Model. Gli strumenti possono generare un modello concettuale, convalidare un modello esistente, produrre file del codice sorgente contenenti classi di oggetti basate sul modello concettuale e produrre file del codice sorgente contenenti visualizzazioni generate dal modello. Per informazioni dettagliate, vedere [Pre-Generated Mapping viste](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[ADO.NET Entity Framework](http://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Viene descritto come utilizzare [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] strumenti di cui [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] fornisce, per creare applicazioni.|
|[Entity Data Model](http://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Fornisce collegamenti e informazioni per l'utilizzo di dati utilizzati dalle applicazioni compilate in [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)].|
|[Introduzione a .NET completo (Console, WinForms, WPF e così via)](/ef/ef6/get-started)|Fornisce esercitazioni su come creare applicazioni desktop .NET che usano Entity Framework 7.|
|[ASP.NET 5 dell'applicazione al nuovo Database](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Viene descritto come creare una nuova applicazione ASP.NET 5 usando Entity Framework 7.|

## <a name="see-also"></a>Vedere anche
 [Visual Studio Data Tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
