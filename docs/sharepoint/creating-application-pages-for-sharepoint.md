---
title: Creazione di pagine applicazione per SharePoint | Microsoft Docs
description: Creazione di pagine applicazione per SharePoint. Una pagina dell'applicazione è una pagina Web ASP.NET progettata per l'uso in un sito Web di SharePoint.
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1228ef551235fd616803d6e05057ee50f0ea7ec4
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850442"
---
# <a name="create-application-pages-for-sharepoint"></a>Creazione di pagine applicazione per SharePoint
  Una *pagina dell'applicazione* è una pagina Web ASP.NET progettata per l'utilizzo in un sito Web di SharePoint. Le pagine dell'applicazione sono un tipo specializzato di pagina ASP.NET. La differenza principale tra una pagina dell'applicazione e una pagina ASP.NET standard consiste nel fatto che una pagina dell'applicazione contiene contenuto unito a una pagina master di SharePoint. Una pagina master consente alle pagine dell'applicazione di condividere lo stesso aspetto e lo stesso comportamento delle altre pagine di un sito.

 Visual Studio consente di progettare pagine dell'applicazione usando una finestra di progettazione. Nella finestra di progettazione viene visualizzata un'area di contenuto per ogni segnaposto di contenuto definito in una pagina master. È possibile progettare la pagina dell'applicazione trascinando i controlli in queste aree di contenuto.

## <a name="application-pages"></a>Pagine applicazione
 Le pagine dell'applicazione vengono condivise in tutti i siti del server, mentre una pagina del sito è specifica di un sito. Per ulteriori informazioni, i [tipi di pagina di SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

 Per impostazione predefinita, la maggior parte delle pagine visualizzate quando si crea un sito di SharePoint sono pagine del sito. Una pagina del sito può essere aggiunta a una raccolta di pagine di SharePoint. Gli utenti possono personalizzare una pagina del sito utilizzando strumenti come SharePoint Designer. Una pagina del sito può inoltre ospitare caratteristiche quali Dynamic Web part e zone Web part.

 Le pagine dell'applicazione non possono eseguire queste operazioni. Tuttavia, una pagina dell'applicazione è il tipo di pagina migliore da creare se si desidera che la pagina contenga codice personalizzato. Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, l'esecuzione del codice viene arrestata quando l'utente personalizza la pagina utilizzando strumenti come SharePoint Designer.

> [!NOTE]
> Visual Studio non fornisce modelli che consentono di creare pagine del sito per un sito di SharePoint. Per ulteriori informazioni, vedere [tipi di pagine di SharePoint](/previous-versions/office/developer/sharepoint-2010/aa979592(v=office.14)).

## <a name="create-an-application-page"></a>Creare una pagina dell'applicazione
 Per creare una pagina dell'applicazione, aggiungere un elemento della **pagina dell'applicazione** a un progetto SharePoint. Quando si crea una pagina dell'applicazione, Visual Studio aggiunge le cartelle seguenti al progetto:

|Cartella|Descrizione|
|------------|-----------------|
|Layout|Esegue il mapping alla directory virtuale _layouts della file system di SharePoint.|
|Sottocartella layout|Contiene i file che costituiscono la pagina dell'applicazione. Per impostazione predefinita, questa cartella ha lo stesso nome del progetto. È possibile rinominare questa cartella in qualsiasi momento. Quando si esegue il progetto, Visual Studio distribuisce questa cartella nella directory virtuale _layouts della file system di SharePoint.|

 Visual Studio aggiunge i file seguenti al progetto:

|File|Descrizione|
|----------|-----------------|
|File di paging ASP.NET (*aspx*)|Contiene il markup XML che definisce la pagina.|
|File di codice della pagina dell'applicazione|Contiene il codice dietro la pagina dell'applicazione. Aggiungere il codice che gestisce gli eventi in questo file.|
|File di codice della finestra di progettazione della pagina dell'applicazione|Contiene il codice generato dalla finestra di progettazione. Non modificare direttamente questo file.|

## <a name="design-and-debug-an-application-page"></a>Progettare ed eseguire il debug di una pagina dell'applicazione
 Progettare il contenuto di una pagina dell'applicazione usando la visualizzazione di progettazione in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre la pagina dell'applicazione nel progetto (facendo doppio clic su di essa o aprendo il menu di scelta rapida e scegliendo **Apri**), quindi scegliere il pulsante **progettazione** nella parte inferiore dell'editor.

> [!NOTE]
> È possibile progettare la pagina solo nella visualizzazione **origine** della finestra di progettazione. La visualizzazione **progettazione** della finestra di progettazione è disabilitata per le pagine dell'applicazione.

 È possibile eseguire il debug di una pagina dell'applicazione come se si eseguisse il debug di altri elementi di progetto SharePoint in Visual Studio. Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.

 Per visualizzare la pagina dell'applicazione, è necessario passare manualmente al percorso della pagina dell'applicazione, ad esempio: http://<em>server_name</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 Per ulteriori informazioni su come eseguire il debug di progetti SharePoint, vedere [risolvere i problemi di soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Scegliere una pagina master
 Per impostazione predefinita, un elemento della **pagina dell'applicazione** fa riferimento alla pagina master del sito che si sta usando per eseguire il debug del progetto. Questa pagina è denominata v4. master ed è disponibile nella **raccolta di pagine master** del sito di SharePoint.

 È possibile modificare in modo esplicito la pagina master utilizzata dalla pagina dell'applicazione impostando l' `MasterPageFile` attributo dell' `Page` elemento Application. (Ad esempio: `MasterPageFile="~/_layouts/applicationv4.master"` ). In realtà, è necessario impostare questo attributo se le pagine master dinamiche non sono abilitate nel server SharePoint. Per ulteriori informazioni sulle pagine master in SharePoint, vedere la pagina relativa alle [pagine master](/previous-versions/office/developer/sharepoint-2010/ms443795(v=office.14)).

## <a name="see-also"></a>Vedere anche
- [Sviluppo di SharePoint Foundation in dettaglio](/previous-versions/office/developer/sharepoint-2010/ee539092(v=office.14))
- [Panoramica di ASP.NET](/aspnet/overview)
- [Pagine Web ASP.NET](/aspnet/web-pages/index)
