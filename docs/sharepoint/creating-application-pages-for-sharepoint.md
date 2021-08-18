---
title: Creazione di pagine applicazione per SharePoint | Microsoft Docs
description: Creare pagine dell'applicazione SharePoint. Una pagina applicazione è una ASP.NET Web progettata per l'uso in un SharePoint web.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, Web pages
- SharePoint development in Visual Studio, content pages
- SharePoint development in Visual Studio, application pages
- application pages [SharePoint development in Visual Studio], developing
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 035c3b952fd16dd8aa4adf3ffb95542fe39464ff
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122149520"
---
# <a name="create-application-pages-for-sharepoint"></a>Creare pagine dell'applicazione per SharePoint
  Una *pagina dell'applicazione* è una ASP.NET Web che è progettata per l'uso in un SharePoint Web. Le pagine dell'applicazione sono un tipo specializzato di ASP.NET pagina. La differenza principale tra una pagina dell'applicazione e una pagina ASP.NET standard è che una pagina dell'applicazione contiene contenuto unito a una SharePoint master. Una pagina master consente alle pagine dell'applicazione di condividere lo stesso aspetto e lo stesso comportamento delle altre pagine di un sito.

 Visual Studio consente di progettare pagine dell'applicazione usando una finestra di progettazione. La finestra di progettazione visualizza un'area di contenuto per ogni segnaposto di contenuto definito in una pagina master. È possibile progettare la pagina dell'applicazione trascinando i controlli in queste aree di contenuto.

## <a name="application-pages"></a>Pagine dell'applicazione
 Le pagine dell'applicazione vengono condivise tra tutti i siti del server, mentre una pagina del sito è specifica di un sito. Per altre informazioni, vedere [SharePoint Page Types](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Per impostazione predefinita, la maggior parte delle pagine visualizzate quando si crea un SharePoint sito sono pagine del sito. È possibile aggiungere una pagina del sito a una SharePoint raccolta pagine. Gli utenti possono personalizzare una pagina del sito usando strumenti come SharePoint Designer. Una pagina del sito può ospitare anche funzionalità quali la Web part dinamica e le zone web part.

 Le pagine dell'applicazione non possono eseguire queste operazioni. Tuttavia, una pagina dell'applicazione è il tipo di pagina migliore da creare se si vuole che la pagina contenga codice personalizzato. Anche se è possibile aggiungere codice personalizzato a una pagina del sito, l'esecuzione del codice viene interrotta quando l'utente personalizza la pagina usando strumenti come SharePoint Designer.

> [!NOTE]
> Visual Studio non fornisce modelli che consentono di creare pagine del sito per un SharePoint sito. Per altre informazioni, vedere Tipi [SharePoint pagina](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Creare una pagina dell'applicazione
 Per creare una pagina dell'applicazione, aggiungere un **elemento Pagina applicazione** a un SharePoint progetto. Quando si crea una pagina dell'applicazione, Visual Studio le cartelle seguenti al progetto:

|Cartella|Descrizione|
|------------|-----------------|
|Layout|Mappe alla directory _layouts virtuale del SharePoint file system.|
|Sottocartella Layout|Contiene i file che costituiscono la pagina dell'applicazione. Per impostazione predefinita, questa cartella ha lo stesso nome del progetto. È possibile rinominare questa cartella in qualsiasi momento. Quando si esegue il progetto, Visual Studio questa cartella viene distribuita nella directory _layouts virtuale del SharePoint file system.|

 Visual Studio aggiunge i file seguenti al progetto:

|File|Descrizione|
|----------|-----------------|
|ASP.NET file di pagina (*aspx*)|Contiene il markup XML che definisce la pagina.|
|File di codice della pagina dell'applicazione|Contiene il codice dietro la pagina dell'applicazione. Aggiungere il codice che gestisce gli eventi a questo file.|
|File di codice della finestra di progettazione della pagina dell'applicazione|Contiene il codice generato dalla finestra di progettazione. Non modificare direttamente questo file.|

## <a name="design-and-debug-an-application-page"></a>Progettare ed eseguire il debug di una pagina dell'applicazione
 Progettare il contenuto di una pagina dell'applicazione usando la visualizzazione progettazione in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre la pagina dell'applicazione nel progetto (facendo doppio clic su di essa o aprendo il relativo menu di scelta rapida e scegliendo Apri **)** e quindi scegliendo il **pulsante** Progettazione nella parte inferiore dell'editor.

> [!NOTE]
> È possibile progettare la pagina solo nella **visualizzazione Origine** della finestra di progettazione. La **visualizzazione Progettazione** della finestra di progettazione è disabilitata per le pagine dell'applicazione.

 È possibile eseguire il debug di una pagina dell'applicazione esattamente come si farebbe per altri SharePoint di progetto in Visual Studio. Quando si avvia il debugger Visual Studio, Visual Studio apre il SharePoint sito.

 Per visualizzare la pagina dell'applicazione, è necessario passare manualmente al percorso della pagina dell'applicazione, ad esempio http://<em>Server_Name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx.

 Per altre informazioni su come eseguire il debug di SharePoint progetti, vedere [Risolvere i SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Scegliere una pagina master
 Per impostazione predefinita, un **elemento Pagina applicazione** fa riferimento alla pagina master del sito in uso per eseguire il debug del progetto. Tale pagina è denominata v4.master ed è disponibile nella raccolta pagine **master** del SharePoint sito.

 È possibile modificare in modo esplicito la pagina master usata dalla pagina dell'applicazione impostando `MasterPageFile` l'attributo dell'elemento `Page` dell'applicazione. (Ad esempio: `MasterPageFile="~/_layouts/applicationv4.master"` ). È infatti necessario impostare questo attributo se le pagine master dinamiche non sono abilitate SharePoint server. Per altre informazioni sulle pagine master in SharePoint, vedere [Pagine master](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Vedi anche
- [SharePoint Sviluppo di base in profondità](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Panoramica di ASP.NET](/aspnet/overview)
- [Pagine Web ASP.NET](/aspnet/web-pages/index)
