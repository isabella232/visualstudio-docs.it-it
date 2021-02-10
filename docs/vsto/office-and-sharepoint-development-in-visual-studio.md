---
title: Sviluppo di Office e SharePoint in Visual Studio
description: Informazioni su come estendere Microsoft Office e SharePoint creando un'app leggera o un componente aggiuntivo che gli utenti scaricano da Office Store.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], about developing applications
- Office development in Visual Studio
- Office projects
- Visual Studio Tools for Office, see Office development in Visual Studio
- Office applications [Office development in Visual Studio]
- Office Business Applications
- applications [Office development in Visual Studio]
- programming [Office development in Visual Studio]
- VSTO, see Office development in Visual Studio
- Office, development with Visual Studio
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cebcb16708e42f8102e2dc235b52a81e16c588c7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99940904"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Sviluppo di Office e SharePoint in Visual Studio
  È possibile estendere Microsoft Office e SharePoint creando un'app leggera o un componente aggiuntivo che gli utenti scaricano da [Office Store](https://store.office.com/) o da un catalogo dell'organizzazione oppure creando una soluzione basata su.NET Framework che gli utenti installano in un computer.

 In questo argomento

- [Creare componenti aggiuntivi per Office e SharePoint](#Apps)

- [Creare un componente aggiuntivo VSTO](#Add-ins)

- [Creare una soluzione SharePoint](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a> Creazione di componenti aggiuntivi per Office e SharePoint
 Office 2013 e SharePoint 2013 introducono un nuovo modello di componente aggiuntivo che consente di creare, distribuire e monetizzare i componenti aggiuntivi che estendono Office e SharePoint.  Questi componenti aggiuntivi possono essere eseguiti in Office o SharePoint Online e gli utenti possono interagire con i componenti aggiuntivi da molti dispositivi.

 Informazioni su come usare il nuovo [modello di componente aggiuntivo di Office](/office/dev/add-ins/overview/office-add-ins) per estendere l'esperienza di Office per gli utenti.

 Questi componenti aggiuntivi hanno footprint di piccole dimensioni rispetto a soluzioni e componenti aggiuntivi VSTO e possono essere compilati con quasi tutte le tecnologie di programmazione Web, ad esempio HTML5, JavaScript, CSS3 e XML.  Per iniziare, usare il Office Developer Tools in Visual Studio, che consente di creare progetti, scrivere codice ed eseguire i componenti aggiuntivi in un browser.

 ![Applicazioni per un modello concettuale di Office e SharePoint](../vsto/media/officeandsharepointapps2015.png "Applicazioni per un modello concettuale di Office e SharePoint")

### <a name="build-an-office-add-in"></a>Compilare un componente aggiuntivo di Office
 Per estendere la funzionalità di Office, creare un componente aggiuntivo per Office. Si tratta fondamentalmente di una pagina Web ospitata in un'applicazione di Office, ad esempio Excel, Word, Outlook e PowerPoint. L'app può aggiungere funzionalità a documenti, fogli di lavoro, messaggi di posta elettronica, appuntamenti, presentazioni e progetti.

 È possibile vendere l'app in Office Store.  [Office Store](https://store.office.com/) consente facilmente di monetizzare i componenti aggiuntivi, gestire gli aggiornamenti e controllare la telemetria. È anche possibile pubblicare l'app per gli utenti tramite un catalogo di app in SharePoint o in Exchange Server.

 L'app seguente per Office mostra i dati del foglio di lavoro in una mappa di Bing.

 ![App contenuto per Office](../vsto/media/appforoffice.png "App contenuto per Office")

 **Scopri di più**

|A|Vedere|
|--------|---------|
|Altre informazioni sui componenti aggiuntivi per Office e sulla relativa creazione.|[Componenti aggiuntivi di Office](/office/dev/add-ins/publish/publish)|
|Confrontare i diversi modi in cui è possibile estendere Office e decidere se usare un'app o un componente aggiuntivo di Office.|[Roadmap per i componenti aggiuntivi di Office, VSTO e VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>Creazione di un componente aggiuntivo per SharePoint
 Per estendere SharePoint per gli utenti, creare un componente aggiuntivo per SharePoint. Si tratta fondamentalmente di un'applicazione autonoma di piccole dimensioni, facile da usare che risolve la necessità di utenti o aziende.

 È possibile vendere l'app per SharePoint in [Office Store](https://store.office.com/). È anche possibile pubblicare il componente aggiuntivo per gli utenti tramite un catalogo di componenti aggiuntivi in SharePoint.  I proprietari del sito possono installare, aggiornare e disinstallare il componente aggiuntivo nei siti di SharePoint senza l'aiuto di un server della farm o di un amministratore della raccolta di siti.

 Di seguito è riportato un esempio di un'app per SharePoint che consente agli utenti di gestire i contatti aziendali.

 ![Applicazione gestione contatti business per SharePoint](../vsto/media/appforsharepoint.png "Applicazione gestione contatti business per SharePoint")

 **Scopri di più**

|A|Vedere|
|--------|---------|
|Altre informazioni sui componenti aggiuntivi per SharePoint e sulla relativa creazione.|[Componenti aggiuntivi di SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Confrontare i componenti aggiuntivi per SharePoint con le soluzioni tradizionali di SharePoint.|[Confronto tra componenti aggiuntivi di SharePoint e soluzioni di SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Scegliere se creare un componente aggiuntivo di SharePoint o una soluzione di SharePoint.|[Decidere tra i componenti aggiuntivi di SharePoint e le soluzioni SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a> Creare un componente aggiuntivo VSTO
 Creare un componente aggiuntivo VSTO per Office 2007 o Office 2010 oppure per estendere Office 2013 e Office 2016 oltre le possibilità offerte dai componenti aggiuntivi per Office. I componenti aggiuntivi VSTO vengono eseguiti solo sul desktop. Gli utenti devono installare i componenti aggiuntivi VSTO, quindi sono in genere più difficili da distribuire e supportare.  Tuttavia, un componente aggiuntivo VSTO può essere maggiormente integrato con Office. Ad esempio, può aggiungere schede e controlli alla barra multifunzione di Office ed eseguire attività di automazione avanzate come l'unione di documenti o la modifica di grafici. È possibile sfruttare .NET Framework e usare C# e Visual Basic per interagire con gli oggetti di Office.

 Ecco un esempio di ciò che può fare un componente aggiuntivo VSTO. Questo componente aggiuntivo VSTO aggiunge alcuni controlli della barra multifunzione, un riquadro attività personalizzato e una finestra di dialogo a PowerPoint.

 ![Soluzione per i componenti aggiuntivi di PowerPoint](../vsto/media/powerpointaddin.png "Soluzione del componente aggiuntivo PowerPoint")

 **Scopri di più**

|A|Lettura|
|--------|----------|
|Confrontare i diversi modi in cui è possibile estendere Office e decidere se usare un componente aggiuntivo VSTO o un componente aggiuntivo di Office.|[Roadmap per i componenti aggiuntivi di Office, VSTO e VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|Creare un componente aggiuntivo VSTO.|[Componenti aggiuntivi VSTO creati con Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> Creare una soluzione di SharePoint
 Creare una soluzione di SharePoint per SharePoint Foundation 2010 e SharePoint Server 2010 o per estendere SharePoint 2013 e SharePoint 2016 in modi diversi rispetto a quanto possibile con un componente aggiuntivo per SharePoint.

 Le soluzioni di SharePoint richiedono server della farm di SharePoint locali che devono essere installati dagli amministratori e poiché le soluzioni vengono eseguite in SharePoint, possono influenzare le prestazioni del server. Tuttavia, le soluzioni offrono un accesso più diretto agli oggetti di SharePoint. Inoltre, quando si crea una soluzione di SharePoint, è possibile sfruttare .NET Framework e usare C# e Visual Basic per interagire con gli oggetti di SharePoint.

 **Scopri di più**

|A|Vedere|
|--------|---------|
|Confrontare le soluzioni di SharePoint con i componenti aggiuntivi di SharePoint.|[Confronto tra componenti aggiuntivi di SharePoint e soluzioni di SharePoint](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Creare una soluzione di SharePoint.|[Creazione di soluzioni SharePoint](../sharepoint/create-sharepoint-solutions.md)|