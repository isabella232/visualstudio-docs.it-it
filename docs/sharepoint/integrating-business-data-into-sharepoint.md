---
title: Integrazione dei dati aziendali in SharePoint | Microsoft Docs
description: Leggere un riepilogo di alto livello su come integrare i dati aziendali in SharePoint creando un modello per il servizio di connettività dei dati business (BDC).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Business Data Connectivity service [SharePoint development in Visual Studio], business data
- BDC [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], business data
- Business Data Connectivity service [SharePoint development in Visual Studio], aggregating data
- BDC [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], creating a model
- Business Data Connectivity service [SharePoint development in Visual Studio], data
- BDC [SharePoint development in Visual Studio], data
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: a68921a43a889b8a36204e3703c2e0003618b8139639d1cfab6ae8018ddb4eca
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121352855"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrare i dati aziendali in SharePoint
  È possibile integrare i dati aziendali in SharePoint. I dati aziendali possono derivare da applicazioni server back-end, ad esempio [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)] , Siebel e SAP o da un servizio Web. Gli utenti possono visualizzare, aggiungere, aggiornare o eliminare dati aziendali usando elenchi esterni o Web part dati aziendali in SharePoint.  Gli utenti possono anche accedere a questi dati offline in un'applicazione Microsoft Office, ad esempio Microsoft Outlook. Per altre informazioni, vedere [Dove è possibile visualizzare dati esterni.](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14))

 Per integrare i dati SharePoint, creare un modello per il servizio di integrazione applicativa dei dati (BDC). Il servizio BDC è un'applicazione in SharePoint che archivia le informazioni sui dati nelle applicazioni aziendali. Per altre informazioni, vedere Servizio di connettività dei dati [business (BDC).](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14))

## <a name="models-in-visual-studio"></a>Modelli in Visual Studio
 I modelli Visual Studio consentono di scrivere codice personalizzato per recuperare e aggiornare i dati dalle origini dati back-end. È anche possibile aggregare dati da più origini dati. Ad esempio, è possibile visualizzare un elenco di clienti che contiene i dati di un [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] database e di un servizio Web.

 È anche possibile importare modelli già distribuiti in SharePoint. Dopo aver importato un modello, è possibile aggiungere codice personalizzato o semplicemente usare Visual Studio per creare un pacchetto e distribuire il modello in SharePoint server farm. Per altre informazioni, vedere [Creare un modello di connettività dei dati business.](../sharepoint/creating-a-business-data-connectivity-model.md)

## <a name="design-a-model-in-visual-studio"></a>Progettare un modello in Visual Studio
 È possibile progettare un modello usando una finestra di progettazione e diverse finestre degli strumenti. Durante la progettazione del modello, Visual Studio genera il codice XML del modello. Per altre informazioni, vedere Panoramica degli strumenti di progettazione del modello [BDC.](../sharepoint/bdc-model-design-tools-overview.md)

 Un modello contiene entità e metodi.

### <a name="entities"></a>Entità
 Un'entità descrive una raccolta di campi. Ad esempio, un'entità può rappresentare una tabella in un database. Un'entità viene visualizzata come tipo di contenuto esterno in SharePoint. Per altre informazioni sui tipi di contenuto esterni, vedere [Che cosa sono i tipi di contenuto esterni?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Metodi
 Un metodo consente ai consumer di un tipo di contenuto esterno di eseguire un'azione sui campi di un'entità. Ad esempio, un metodo Updater potrebbe consentire agli utenti di modificare l'indirizzo e la data di nascita di un cliente in cui e `Address` `BirthDate` sono campi `Customer` dell'entità.

 Visual Studio genera un file di codice del servizio per ogni entità nel modello. Quando si aggiunge un metodo al modello, Visual Studio genera un metodo corrispondente nel file di codice del servizio. Aggiungere codice a ogni metodo per eseguire l'attività appropriata. Ad esempio, se si aggiunge un metodo Creator al modello, Visual Studio genera un metodo Creator nel file di codice del servizio. Questo metodo viene chiamato dal servizio BDC quando un utente fa clic sul pulsante Nuovo **elemento** in un elenco basato sul modello. Aggiungere quindi il codice al metodo Creator che aggiunge nuovi dati a un'origine dati. Per altre informazioni, vedere [Progettare un modello di connettività dei dati aziendali.](../sharepoint/designing-a-business-data-connectivity-model.md)

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare un modello di connettività dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)|Illustra come creare un nuovo modello o importare un modello esportato da SharePoint.|
|[Progettare un modello di connettività dei dati aziendali](../sharepoint/designing-a-business-data-connectivity-model.md)|Viene illustrato come progettare gli elementi di un modello usando Visual Studio di progettazione.|
|[Quando usare SharePoint Designer e Visual Studio quando si compilano soluzioni con BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Consente di decidere se usare Visual Studio o SharePoint Designer per creare un modello per il data center BDC.|
