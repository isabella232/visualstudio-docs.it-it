---
title: Office e SharePoint sviluppo in Visual Studio
description: Informazioni su come estendere Microsoft Office e SharePoint creando un'app leggera o un componente aggiuntivo scaricato dagli utenti da Office Store.
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: b22d2975404b335583acf5fa74eb261901c31bc23ced58bd349ef96058ac35f3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121331065"
---
# <a name="office-and-sharepoint-development-in-visual-studio"></a>Office e SharePoint sviluppo in Visual Studio
  È possibile estendere Microsoft Office e SharePoint creando un'app leggera o un componente aggiuntivo che gli utenti scaricano da [Office Store](https://store.office.com/) o da un catalogo dell'organizzazione oppure creando una soluzione basata su.NET Framework che gli utenti installano in un computer.

 In questo argomento

- [Creare componenti aggiuntivi per Office e SharePoint](#Apps)

- [Creare un VSTO componente aggiuntivo](#Add-ins)

- [Creare una SharePoint personalizzata](#Solutions)

## <a name="create-add-ins-for-office-and-sharepoint"></a><a name="Apps"></a>Creare componenti aggiuntivi per Office e SharePoint
 Office 2013 e SharePoint 2013 introducono un nuovo modello di componente aggiuntivo che consente di creare, distribuire e monetizzare i componenti aggiuntivi che estendono Office e SharePoint.  Questi componenti aggiuntivi possono essere eseguiti in Office o SharePoint Online e gli utenti possono interagire con i componenti aggiuntivi da molti dispositivi.

 Informazioni su come usare il nuovo modello Office componente aggiuntivo [per](/office/dev/add-ins/overview/office-add-ins) estendere l'esperienza Office per gli utenti.

 Questi componenti aggiuntivi hanno footprint ridotti rispetto VSTO componenti aggiuntivi e soluzioni ed è possibile compilarli usando quasi tutte le tecnologie di programmazione Web, ad esempio HTML5, JavaScript, CSS3 e XML.  Per iniziare, usare il Office Strumenti di sviluppo in Visual Studio, che consente di creare progetti, scrivere codice ed eseguire i componenti aggiuntivi in un browser.

 ![Applicazioni per un modello concettuale di Office e SharePoint](../vsto/media/officeandsharepointapps2015.png "Applicazioni per un modello concettuale di Office e SharePoint")

### <a name="build-an-office-add-in"></a>Compilare Office componente aggiuntivo
 Per estendere la funzionalità di Office, creare un componente aggiuntivo per Office. Si tratta fondamentalmente di una pagina Web ospitata in un'applicazione Office, ad esempio Excel, Word, Outlook e PowerPoint. L'app può aggiungere funzionalità a documenti, fogli di lavoro, messaggi di posta elettronica, appuntamenti, presentazioni e progetti.

 È possibile vendere l'app in Office Store.  [Office Store](https://store.office.com/) consente facilmente di monetizzare i componenti aggiuntivi, gestire gli aggiornamenti e controllare la telemetria. È anche possibile pubblicare l'app per gli utenti tramite un catalogo di app in SharePoint o in Exchange Server.

 L'app seguente per Office mostra i dati del foglio di lavoro in una mappa di Bing.

 ![App contenuto per Office](../vsto/media/appforoffice.png "App contenuto per Office")

 **Scopri di più**

|A|Vedere|
|--------|---------|
|Altre informazioni sui componenti aggiuntivi per Office e sulla relativa creazione.|[Office componenti aggiuntivi](/office/dev/add-ins/publish/publish)|
|Confrontare i diversi modi in cui è possibile estendere Office e decidere se usare un'app o un componente aggiuntivo di Office.|[Roadmap per Office componenti aggiuntivi, VSTO e VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|

### <a name="build-a-sharepoint-add-in"></a>Compilare SharePoint componente aggiuntivo
 Per estendere SharePoint per gli utenti, creare un componente aggiuntivo per SharePoint. Si tratta fondamentalmente di un'applicazione piccola, semplice da usare e autonoma che risolve la necessità di utenti o aziende.

 È possibile vendere l'app per SharePoint in [Office Store](https://store.office.com/). È anche possibile pubblicare il componente aggiuntivo per gli utenti tramite un catalogo di componenti aggiuntivi in SharePoint.  I proprietari del sito possono installare, aggiornare e disinstallare il componente aggiuntivo nei siti di SharePoint senza l'aiuto di un server della farm o di un amministratore della raccolta di siti.

 Di seguito è riportato un esempio di app per SharePoint che consente agli utenti di gestire i contatti commerciali.

 ![Applicazione gestione contatti business per SharePoint](../vsto/media/appforsharepoint.png "Applicazione gestione contatti business per SharePoint")

 **Scopri di più**

|A|Vedere|
|--------|---------|
|Altre informazioni sui componenti aggiuntivi per SharePoint e sulla relativa creazione.|[Componenti aggiuntivi di SharePoint](/sharepoint/dev/sp-add-ins/sharepoint-add-ins)|
|Confrontare i componenti aggiuntivi per SharePoint con le soluzioni tradizionali di SharePoint.|[SharePoint Componenti aggiuntivi rispetto alle soluzioni SharePoint personalizzate](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Scegliere se creare un componente aggiuntivo di SharePoint o una soluzione di SharePoint.|[Decidere tra SharePoint componenti aggiuntivi e SharePoint soluzioni](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|

## <a name="create-a-vsto-add-in"></a><a name="Add-ins"></a>Creare un VSTO componente aggiuntivo
 Creare un componente aggiuntivo VSTO per la destinazione Office 2007 o Office 2010 o per estendere Office 2013 e Office 2016 oltre ciò che è possibile con i componenti aggiuntivi Office. VSTO componenti aggiuntivi vengono eseguiti solo sul desktop. Gli utenti devono installare VSTO componenti aggiuntivi, quindi sono in genere più difficili da distribuire e supportare.  Tuttavia, un componente aggiuntivo VSTO può essere maggiormente integrato con Office. Ad esempio, può aggiungere schede e controlli alla barra multifunzione di Office ed eseguire attività di automazione avanzate come l'unione di documenti o la modifica di grafici. È possibile sfruttare .NET Framework e usare C# e Visual Basic per interagire con gli oggetti di Office.

 Ecco un esempio delle VSTO componente aggiuntivo. Questo componente aggiuntivo VSTO aggiunge alcuni controlli della barra multifunzione, un riquadro attività personalizzato e una finestra di dialogo a PowerPoint.

 ![PowerPoint Soluzione del componente aggiuntivo](../vsto/media/powerpointaddin.png "Soluzione del componente aggiuntivo PowerPoint")

 **Scopri di più**

|Per|Read|
|--------|----------|
|Confrontare i diversi modi in cui è possibile estendere Office e decidere se usare un componente aggiuntivo VSTO o un componente aggiuntivo di Office.|[Roadmap per Office componenti aggiuntivi, VSTO e VBA](/archive/blogs/officeapps/roadmap-for-apps-for-office-vsto-and-vba)|
|Creare un componente aggiuntivo VSTO.|[Componenti aggiuntivi VSTO creati con Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)|

## <a name="create-a-sharepoint-solution"></a><a name="Solutions"></a> Creare una soluzione di SharePoint
 Creare una soluzione SharePoint per SharePoint Foundation 2010 e SharePoint Server 2010 o per estendere SharePoint 2013 e SharePoint 2016 in modi diversi da quanto possibile con un componente aggiuntivo SharePoint.

 Le soluzioni di SharePoint richiedono server della farm di SharePoint locali che devono essere installati dagli amministratori e poiché le soluzioni vengono eseguite in SharePoint, possono influenzare le prestazioni del server. Tuttavia, le soluzioni offrono un accesso più diretto agli oggetti di SharePoint. Inoltre, quando si crea una soluzione di SharePoint, è possibile sfruttare .NET Framework e usare C# e Visual Basic per interagire con gli oggetti di SharePoint.

 **Scopri di più**

|A|Vedere|
|--------|---------|
|Confrontare le soluzioni di SharePoint con i componenti aggiuntivi di SharePoint.|[SharePoint Componenti aggiuntivi rispetto alle soluzioni SharePoint personalizzate](/sharepoint/dev/general-development/sharepoint-server-application-lifecycle-management)|
|Creare una soluzione di SharePoint.|[Creare SharePoint soluzioni](../sharepoint/create-sharepoint-solutions.md)|