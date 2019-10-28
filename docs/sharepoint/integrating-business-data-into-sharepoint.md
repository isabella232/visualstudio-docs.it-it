---
title: Integrazione di dati business in SharePoint | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 06d9e8059db8daa1c27b8c1d5fecc50940b7facb
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986396"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrare i dati aziendali in SharePoint
  È possibile integrare i dati aziendali in SharePoint. I dati aziendali possono provenire dalle applicazioni server back-end, ad esempio [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel e SAP o un servizio Web. Gli utenti possono visualizzare, aggiungere, aggiornare o eliminare i dati aziendali utilizzando elenchi esterni o dati aziendali Web part in SharePoint.  Gli utenti possono anche accedere ai dati offline in un'applicazione Microsoft Office, ad esempio Microsoft Outlook. Per ulteriori informazioni, vedere [dove è possibile visualizzare i dati esterni](/previous-versions/office/developer/sharepoint-2010/ee558737(v=office.14)).

 Per integrare i dati in SharePoint, creare un modello per il servizio di integrazione applicativa dei dati. Il servizio BDC è un'applicazione di SharePoint che archivia le informazioni sui dati nelle applicazioni aziendali. Per ulteriori informazioni, vedere servizio di integrazione applicativa [dei dati](/previous-versions/office/developer/sharepoint-2010/ee556407(v=office.14)).

## <a name="models-in-visual-studio"></a>Modelli in Visual Studio
 I modelli in Visual Studio consentono di scrivere codice personalizzato per recuperare e aggiornare i dati dalle origini dati back-end. È anche possibile aggregare dati da più origini dati. Ad esempio, è possibile visualizzare un elenco di clienti che contengono dati da un database di [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] e un servizio Web.

 È inoltre possibile importare modelli già distribuiti in SharePoint. Dopo aver importato un modello, è possibile aggiungere codice personalizzato oppure utilizzare semplicemente Visual Studio per creare il pacchetto e distribuire il modello in più server farm di SharePoint. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md).

## <a name="design-a-model-in-visual-studio"></a>Progettare un modello in Visual Studio
 È possibile progettare un modello utilizzando una finestra di progettazione e diverse finestre degli strumenti. Quando si progetta il modello, Visual Studio genera il codice XML del modello. Per altre informazioni, vedere [Panoramica degli strumenti di progettazione dei modelli BDC](../sharepoint/bdc-model-design-tools-overview.md).

 Un modello contiene entità e metodi.

### <a name="entities"></a>Entità
 Un'entità descrive una raccolta di campi. Un'entità, ad esempio, può rappresentare una tabella in un database. Un'entità viene visualizzata come tipo di contenuto esterno in SharePoint. Per ulteriori informazioni sui tipi di contenuto esterno, vedere [che cosa sono i tipi di contenuto esterno?](/previous-versions/office/developer/sharepoint-2010/ee556391(v=office.14))

### <a name="methods"></a>Metodi
 Un metodo consente ai consumer di un tipo di contenuto esterno di eseguire un'azione sui campi di un'entità. Un metodo di aggiornamento, ad esempio, può consentire agli utenti di modificare l'indirizzo e la data di nascita di un cliente in cui `Address` e `BirthDate` sono campi dell'entità `Customer`.

 Visual Studio genera un file di codice del servizio per ogni entità nel modello. Quando si aggiunge un metodo al modello, Visual Studio genera un metodo corrispondente nel file di codice del servizio. Aggiungere codice a ogni metodo per eseguire l'attività appropriata. Se ad esempio si aggiunge un metodo Creator al modello, Visual Studio genera un metodo Creator nel file di codice del servizio. Questo metodo viene chiamato dal servizio di integrazione applicativa dei dati quando un utente fa clic sul pulsante **nuovo elemento** in un elenco basato sul modello. Quindi, aggiungere il codice al metodo Creator che aggiunge nuovi dati a un'origine dati. Per ulteriori informazioni, vedere [progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Creare un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)|Viene illustrato come creare un nuovo modello o importare un modello esportato da SharePoint.|
|[Progettare un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)|Viene illustrato come progettare gli elementi di un modello utilizzando gli strumenti di progettazione di Visual Studio.|
|[Quando utilizzare SharePoint Designer e Visual Studio quando si compilano soluzioni con BCS](/previous-versions/office/developer/sharepoint-2010/ee558875(v=office.14))|Consente di decidere se utilizzare Visual Studio o utilizzare SharePoint Designer per creare un modello per l'integrazione applicativa dei dati.|
