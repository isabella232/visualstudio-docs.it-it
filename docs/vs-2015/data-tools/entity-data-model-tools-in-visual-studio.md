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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672389"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Strumenti di Entity Data Model in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework è una tecnologia di mapping relazionale a oggetti che consente agli sviluppatori .NET di utilizzare i dati relazionali utilizzando oggetti specifici del dominio. Elimina la necessità di gran parte del codice di accesso ai dati che in genere gli sviluppatori devono scrivere. Entity Framework è la tecnologia di modellazione ORM (Object-Relational Mapping) consigliata per le nuove applicazioni .NET.

 A partire dal 2016 marzo, la versione rilasciata più recente è [Entity Framework 6](https://msdn.microsoft.com/data/ef) . [Entity Framework 7](https://docs.efproject.net/en/latest/) è in versione non definitiva.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] Gli strumenti sono progettati per facilitare la compilazione di [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] applicazioni. La documentazione completa per [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] gli strumenti è disponibile qui: [Entity Framework](https://msdn.microsoft.com/data/jj590134).

 Con [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] gli strumenti, è possibile creare un *modello concettuale* da un database esistente e quindi visualizzare graficamente e modificare il modello concettuale. È inoltre possibile creare prima graficamente un modello concettuale e successivamente generare un database di supporto al modello. In entrambi i casi, è possibile aggiornare automaticamente il modello quando viene modificato il database sottostante e generare automaticamente codice del livello oggetti per l'applicazione. La generazione del database e del codice del livello oggetti è personalizzabile.

 Questi sono gli strumenti specifici che compongono Entity Data Model strumenti in Visual Studio 2015:

- È possibile utilizzare la [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] finestra di progettazione** (**Entity Designer**) per creare e modificare visivamente entità, associazioni, mapping e relazioni di ereditarietà. Il **Entity Designer** genera anche [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] codice del livello oggetti o.

- È possibile utilizzare la ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] procedura guidata** per generare un modello concettuale da un database esistente e aggiungere le informazioni di connessione al database all'applicazione.

- È possibile utilizzare la **procedura guidata Crea database** per creare prima un modello concettuale, quindi creare un database che supporti il modello.

- È possibile utilizzare la **procedura guidata Aggiorna modello** per aggiornare il modello concettuale, il modello di archiviazione e i mapping quando sono state apportate modifiche al database sottostante.

  > [!NOTE]
  > A partire da Visual Studio 2010, [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] gli strumenti non supportano [!INCLUDE[ss2k](../includes/ss2k-md.md)] .

  Gli strumenti generano o modificano un file con estensione edmx. Questo file contiene informazioni che descrivono il modello concettuale, il modello di archiviazione e i mapping tra di essi. Per ulteriori informazioni, vedere  [edmx](https://msdn.microsoft.com/data/jj650889.aspx).

  Entity Framework Power Tools consentono di creare applicazioni che usano l'Entity Data Model. Gli strumenti possono generare un modello concettuale, convalidare un modello esistente, produrre file del codice sorgente contenenti classi di oggetti basate sul modello concettuale e produrre file del codice sorgente contenenti visualizzazioni generate dal modello. Per informazioni dettagliate, vedere [viste di mapping pre-generate](https://msdn.microsoft.com/data/dn469601.aspx).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|Viene descritto come utilizzare [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] gli strumenti [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] disponibili in per creare applicazioni.|
|[Entity Data Model](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|Vengono forniti collegamenti e informazioni per l'utilizzo dei dati utilizzati dalle applicazioni basate su [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] .|
|[Introduzione su .NET completo (console, WinForms, WPF e così via)](/ef/ef6/get-started)|Vengono fornite esercitazioni sulla creazione di applicazioni desktop .NET che utilizzano Entity Framework 7.|
|[ASP.NET 5-applicazione al nuovo database](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Viene descritto come creare una nuova applicazione ASP.NET 5 utilizzando Entity Framework 7.|

## <a name="see-also"></a>Vedere anche
 [Visual Studio data tools per .NET](../data-tools/visual-studio-data-tools-for-dotnet.md)
