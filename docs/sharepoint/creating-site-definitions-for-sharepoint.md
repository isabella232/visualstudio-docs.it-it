---
title: Creazione di definizioni di sito per SharePoint | Microsoft Docs
description: Creare definizioni del sito per SharePoint. Le definizioni del sito determinano l'aspetto e il comportamento SharePoint sito e il relativo contenuto e funzionalità predefiniti.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2d0d97586b1f3f9f62e992aea3c5a480f538e018
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149364"
---
# <a name="create-site-definitions-for-sharepoint"></a>Creare definizioni di sito per SharePoint
  Il SharePoint di definizione del sito in consente di creare una definizione di sito che funge da base per un nuovo [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] SharePoint sito.  Queste definizioni non solo determinano l'aspetto e il comportamento del SharePoint, ma anche il contenuto e la funzionalità predefiniti. Nella definizione è possibile inserire elenchi preconfigurati, tipi di contenuto, ricevitori di eventi, immagini e altri elementi. In SharePoint sono incluse alcune definizioni di sito come BLOG, ad esempio. Quando si crea un sito basato sulla definizione del sito BLOG, il sito contiene gli elenchi, le web part e altri elementi necessari per un sito di blog.

 Per altre informazioni sulle definizioni di sito, vedere [Modelli di sito e definizioni](/previous-versions/office/developer/sharepoint-2010/ms434313(v=office.14)).

## <a name="site-definition-projects"></a>Progetti di definizione del sito
 I progetti di definizione del sito in forniscono solo i file di base necessari a un SharePoint sito e non [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] forniscono alcuna funzionalità predefinita. È necessario aggiungere file e contenuto per fornire le funzionalità desiderate. È possibile compilare il sito manualmente, creando e aggiungendo i file necessari.

## <a name="feature-stapling"></a>Graffatura delle funzionalità
 Uno dei vantaggi della creazione di definizioni di sito in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] è che usano automaticamente feature *stapling*. Feature Stapling collega una funzionalità a una definizione del sito invece di incorporarne le funzionalità nella definizione stessa. In questo modo è possibile aggiungere la funzionalità a qualsiasi sito creato usando la definizione del sito senza modificare la definizione del sito originale. Per altre informazioni, vedere [Feature Stapling](/previous-versions/office/developer/sharepoint-2007/bb861862(v=office.12)).

## <a name="site-definition-project-components"></a>Componenti del progetto di definizione del sito
 Quando si crea una soluzione di definizione del sito, i file predefiniti seguenti vengono aggiunti al relativo **nodo SiteDefinition.**

|File Name|Descrizione|
|---------------|-----------------|
|*Aspx*|L'home page ASPX predefinito per il nuovo SharePoint sito.|
|*onet.xml*|Specifica la configurazione del nuovo sito, i componenti del modello di definizione del sito e il comportamento predefinito. Queste impostazioni possono includere attributi quali i tipi di contenuto abilitati, le visualizzazioni elenco predefinite, i file modello di documento e le web part incluse nel sito. Per impostazione predefinita, la sezione elenca i file da aggiungere al sito SharePoint e come `Modules` vengono configurati.|
|*webtemp_ \<SiteDefinitionName>.xml*|Specifica le configurazioni della definizione del sito visualizzate nella sezione **Selezione** modello della pagina **SharePoint Sito.**|

 Per impostazione predefinita, tutte le definizioni di sito vengono archiviate nella cartella *\<drive:> \Programmi\File comuni\Microsoft Shared\Web Server Extensions\14\TEMPLATE\SiteTemplates.* Ogni definizione del sito ha una sottocartella specifica.

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura dettagliata: creare un progetto di definizione di sito di base](../sharepoint/walkthrough-create-a-basic-site-definition-project.md)|Guida dettagliatamente alla creazione di un progetto di definizione del sito di base in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .|
|[Procedura: Creare una definizione e una configurazione del sito personalizzate](/previous-versions/office/developer/sharepoint-2010/ms454677(v=office.14))|Viene descritto come creare una definizione di sito personalizzata in SharePoint copiando una definizione di sito esistente e quindi modificando la copia.|
|[*WebTemp.xml*](/previous-versions/office/developer/sharepoint-2010/ms447717(v=office.14))|Descrive il file originale che specifica le definizioni del sito disponibili nella sezione **Selezione** modello della **pagina Nuovo SharePoint sito.**|
|[Localizzare SharePoint soluzioni](../sharepoint/localizing-sharepoint-solutions.md)|Descrive come preparare le soluzioni SharePoint per l'uso globale.|
|[Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)|Viene descritto come creare parti di una pagina SharePoint che gli utenti possono modificare.|
|[Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)|Viene descritto come creare controlli riutilizzabili che vengono eseguiti nelle pagine dell'applicazione e Web part.|
|[Visual Web Developer](/previous-versions/visualstudio/visual-studio-2010/ms178093(v=vs.100))|Viene descritto come usare la finestra di progettazione visualizzata quando si apre una pagina Web nel progetto.|
|[Pagine Web ASP.NET Panoramica](/previous-versions/aspnet/428509ah(v=vs.100))|Fornisce informazioni generali sulla struttura delle pagine Web, sul modo in cui le pagine vengono elaborate da e sul modo in cui le pagine visualizzano markup conforme [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] agli standard [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] XHTML.|
|[ASP.NET Sintassi delle pagine Web](/previous-versions/aspnet/k33801s3(v=vs.100))|Descrive gli elementi di markup che costituiscono una ASP.NET pagina.|
|[Programmazione Pagine Web ASP.NET](/previous-versions/aspnet/0yt4zca8(v=vs.100))|Vengono fornite informazioni su come creare gestori eventi nelle [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] pagine e su come usare lo script client.|
|[Programmazione in Windows SharePoint Services](/previous-versions/office/developer/sharepoint-services/ms430674(v=office.12))|Viene descritto come usare il modello a oggetti gestito fornito in [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] .|

## <a name="see-also"></a>Vedi anche
- [Sviluppare soluzioni SharePoint](../sharepoint/developing-sharepoint-solutions.md)
