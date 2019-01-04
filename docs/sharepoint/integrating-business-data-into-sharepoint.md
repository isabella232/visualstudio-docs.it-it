---
title: Integrazione di dati aziendali in SharePoint | Microsoft Docs
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 194f2e0c88a0cbce9ef34f77246cf7969066833e
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53934440"
---
# <a name="integrate-business-data-into-sharepoint"></a>Integrare i dati aziendali in SharePoint
  È possibile integrare i dati aziendali in SharePoint. I dati aziendali possono provenire da applicazioni server back-end, ad esempio [!INCLUDE[TLA#tla_sqlsvr](../sharepoint/includes/tlasharptla-sqlsvr-md.md)], Siebel e SAP, o un servizio Web. Gli utenti possono visualizzare, aggiungere, aggiornare o eliminare i dati aziendali usando gli elenchi esterni o Web part dei dati aziendali in SharePoint.  Gli utenti possono accedere anche questi dati in un'applicazione Microsoft Office, ad esempio Microsoft Outlook. Per altre informazioni, vedere [dove possibile è visualizzazione dei dati esterni](http://go.microsoft.com/fwlink/?LinkId=169295).  
  
 Per integrare i dati in SharePoint, creare un modello per il servizio di integrazione applicativa dei dati (BDC). Il servizio di integrazione applicativa dei dati è un'applicazione in SharePoint che archivia le informazioni sui dati nelle applicazioni aziendali. Per altre informazioni, vedere [servizio di integrazione applicativa dei dati (BDC)](http://go.microsoft.com/fwlink/?LinkID=169276).  
  
## <a name="models-in-visual-studio"></a>Modelli in Visual Studio  
 I modelli in Visual Studio consentono di scrivere codice personalizzato per recuperare e aggiornare i dati da origini dati back-end. È anche possibile aggregare i dati da più origini dati. Ad esempio, è possibile visualizzare un elenco di clienti che contiene i dati da un [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)] database e un servizio Web.  
  
 È anche possibile importare i modelli che sono già stati distribuiti in SharePoint. Dopo aver importato un modello, è possibile aggiungere codice personalizzato o semplicemente usare Visual Studio per creare un pacchetto e distribuirlo in più server farm di SharePoint. Per altre informazioni, vedere [creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md).  
  
## <a name="design-a-model-in-visual-studio"></a>Progettare un modello in Visual Studio
 È possibile progettare un modello usando una finestra di progettazione e finestre degli strumenti diversi. Quando si progetta il modello, Visual Studio genera il codice XML del modello. Per altre informazioni, vedere [Cenni preliminari sugli strumenti di progettazione di modelli di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md).  
  
 Un modello contiene entità e i metodi.  
  
### <a name="entities"></a>Entità  
 Un'entità descrive una raccolta di campi. Ad esempio, un'entità può rappresentare una tabella in un database. Un'entità viene visualizzata come un tipo di contenuto esterno in SharePoint. Per altre informazioni sui tipi di contenuto esterni, vedere [quali sono i tipi di contenuto esterni?](http://go.microsoft.com/fwlink/?LinkId=169293)  
  
### <a name="methods"></a>Metodi  
 Un metodo consente ai consumer del tipo di contenuto esterno per eseguire un'azione sui campi di un'entità. Ad esempio, un metodo Updater potrà consentire agli utenti di modificare l'indirizzo e la data di un cliente di nascita in cui `Address` e `BirthDate` sono campi del `Customer` entità.  
  
 Visual Studio genera un file di codice del servizio per ogni entità nel modello. Quando si aggiunge un metodo per il modello, Visual Studio genera un metodo corrispondente nel file di codice del servizio. Aggiungere codice per ogni metodo per eseguire l'operazione appropriata. Ad esempio, se si aggiunge un metodo Creator al modello, Visual Studio genera un metodo Creator nel file di codice del servizio. Questo metodo viene chiamato dal servizio di integrazione applicativa dei dati quando un utente sceglie il **nuovo elemento** pulsante in un elenco che si basa sul modello. Pertanto, è possibile aggiungere codice al metodo Creator che aggiungono nuovi dati a un'origine dati. Per altre informazioni, vedere [progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
## <a name="related-topics"></a>Argomenti correlati
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Creare un modello di integrazione applicativa dei dati business](../sharepoint/creating-a-business-data-connectivity-model.md)|Mostra si come creare un nuovo modello o si importa un modello esportato da SharePoint.|  
|[Progettare un modello di integrazione applicativa dei dati business](../sharepoint/designing-a-business-data-connectivity-model.md)|Viene illustrato come progettare gli elementi di un modello usando gli strumenti di progettazione di Visual Studio.|  
|[Quando Visual Studio di utilizzare SharePoint Designer. Soluzioni di Visual Studio per la compilazione tramite BCS](http://go.microsoft.com/fwlink/?LinkID=183448)|Consente di decidere se usare Visual Studio o utilizzare SharePoint Designer per creare un modello per l'integrazione applicativa dei dati.|  
