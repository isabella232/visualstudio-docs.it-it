---
title: Creazione di definizioni di sito per SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, site definitions
- site definitions [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0f1a512218c3c1b7af179cfaba3e231a90941fe0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "86015066"
---
# <a name="create-site-definitions-for-sharepoint"></a>Creare definizioni di sito per SharePoint
  Il progetto di definizione del sito di SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consente di creare una *definizione di sito*, che funge da base per un nuovo sito di SharePoint. Queste definizioni non solo determinano l'aspetto e il comportamento del sito di SharePoint, ma anche il contenuto e le funzionalità predefinite. Nella definizione è possibile inserire elenchi preconfigurati, tipi di contenuto, ricevitori di eventi, immagini e altri elementi. In SharePoint sono incluse alcune definizioni di sito come BLOG, ad esempio. Quando si crea un sito basato sulla definizione del sito del BLOG, il sito contiene gli elenchi, le web part e altri elementi richiesti da un sito di Blog.

 Per ulteriori informazioni sulle definizioni del sito, vedere [modelli e definizioni di sito](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Progetti di definizione del sito
 I progetti di definizione del sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] forniscono solo i file di base necessari a un sito di SharePoint, ma non forniscono funzionalità predefinite. Per fornire la funzionalità desiderata, è necessario aggiungere i file e il contenuto. È possibile compilare il sito manualmente, creando e aggiungendo i file necessari.

## <a name="feature-stapling"></a>Graffatura delle funzionalità
 Un vantaggio della creazione di definizioni di sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] consiste nel fatto che usano automaticamente la *graffettatura delle funzionalità*. La graffatura delle funzionalità associa una funzionalità a una definizione del sito anziché incorporarne la funzionalità nella definizione del sito. In questo modo è possibile aggiungere la funzionalità a qualsiasi sito creato utilizzando la definizione del sito senza modificare la definizione del sito originale. Per altre informazioni, vedere [graffatura delle funzionalità](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Componenti del progetto di definizione del sito
 Quando si crea una soluzione di definizione del sito, vengono aggiunti i file predefiniti seguenti al nodo **SiteDefinition** .

|File Name|Descrizione|
|---------------|-----------------|
|*default. aspx*|Home page ASPX predefinito per il nuovo sito di SharePoint.|
|*onet.xml*|Specifica la configurazione del nuovo sito, i componenti del modello di definizione del sito e il comportamento predefinito. Queste impostazioni possono includere attributi quali i tipi di contenuto abilitati, le visualizzazioni elenco predefinite, i file modello di documento e le web part incluse nel sito. Per impostazione predefinita, la `Modules` sezione elenca i file da aggiungere al sito di SharePoint e il modo in cui vengono configurati.|
|*webtemp_ \<SiteDefinitionName> . XML*|Specifica le configurazioni di definizione del sito visualizzate nella sezione **Selezione modello** della pagina **nuovo sito di SharePoint** .|

 Per impostazione predefinita, tutte le definizioni del sito sono archiviate nella cartella \Programmi\File * \<drive:> Comuni\microsoft Shared\Web server extensions\14\TEMPLATE\SiteTemplates* Ogni definizione di sito ha una propria sottocartella.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: creare un progetto di definizione di sito di base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Guida dettagliata alla creazione di un progetto di definizione di sito di base in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Procedura: creare una definizione di sito e una configurazione personalizzati](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Viene descritto come creare una definizione di sito personalizzata in SharePoint copiando una definizione di sito esistente e quindi modificando la copia.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Descrive il file originale che specifica le definizioni dei siti disponibili nella sezione **Selezione modello** della pagina **nuovo sito di SharePoint** .|
|[Localizzare le soluzioni SharePoint](../sharepoint/localizing-sharepoint-solutions.md)|Viene descritto come preparare le soluzioni SharePoint per l'utilizzo globale.|
|[Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Viene descritto come creare parti di una pagina di SharePoint che gli utenti possono modificare.|
|[Creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Viene descritto come creare controlli riutilizzabili che vengono eseguiti nelle pagine dell'applicazione e Web part.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Viene descritto come utilizzare la finestra di progettazione visualizzata quando si apre una pagina Web nel progetto.|
|[Panoramica di Pagine Web ASP.NET](/previous-versions/aspnet/428509ah(v=vs.100))|Vengono fornite informazioni generali sulla struttura delle [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine Web, sulle modalità di elaborazione delle pagine [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] e sul modo in cui le [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine visualizzano il markup conforme agli standard XHTML.|
|[Sintassi della pagina Web ASP.NET](/previous-versions/aspnet/k33801s3(v=vs.100))|Vengono descritti gli elementi di markup che costituiscono una pagina ASP.NET.|
|[Programmazione Pagine Web ASP.NET](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Vengono fornite informazioni su come creare i gestori eventi nelle [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine e come utilizzare lo script client.|
|[Programmazione in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Viene descritto come utilizzare il modello a oggetti gestito fornito in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>Vedere anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
