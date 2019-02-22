---
title: Creazione di pagine dell'applicazione per SharePoint | Microsoft Docs
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
ms.openlocfilehash: d8f02fbff9ed727359adbc5db1b25ee14dbccb3a
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56644445"
---
# <a name="create-application-pages-for-sharepoint"></a>Creare le pagine dell'applicazione per SharePoint
  Un' *pagina dell'applicazione* è una pagina Web ASP.NET è progettata per l'uso in un sito Web di SharePoint. Le pagine dell'applicazione sono un tipo specializzato di pagina ASP.NET. La differenza principale tra una pagina dell'applicazione e una pagina ASP.NET standard è che una pagina dell'applicazione contiene il contenuto che viene unito a una pagina master di SharePoint. Una pagina master consente alle pagine di applicazione condividere lo stesso aspetto e comportamento delle altre pagine in un sito.

 Visual Studio consente di progettare pagine applicazione usando una finestra di progettazione. La finestra di progettazione consente di visualizzare un'area di contenuto per ogni segnaposto di contenuto definito in una pagina master. È possibile progettare la pagina dell'applicazione trascinando i controlli in queste aree di contenuto.

## <a name="application-pages"></a>Pagine dell'applicazione
 Le pagine dell'applicazione sono condivise tra tutti i siti sul server, mentre una pagina del sito si trova a un sito specifico. Per altre informazioni, [tipi di pagine di SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).

 Per impostazione predefinita, la maggior parte delle pagine visualizzate quando si crea un sito di SharePoint sono le pagine del sito. Una pagina del sito può essere aggiunti a una raccolta di pagine di SharePoint. Gli utenti possono personalizzare una pagina del sito usando gli strumenti, ad esempio SharePoint Designer. Una pagina del sito può ospitare anche le funzionalità, ad esempio dynamic Web part e le aree Web Part.

 Le pagine dell'applicazione non è possibile eseguire queste operazioni. Tuttavia, una pagina dell'applicazione è il tipo migliore della pagina per creare, se si desidera che la pagina contiene codice personalizzato. Sebbene sia possibile aggiungere codice personalizzato a una pagina del sito, il codice si interrompe quando l'utente Personalizza la pagina usando gli strumenti, ad esempio SharePoint Designer.

> [!NOTE]
>  Visual Studio fornisce modelli che consentono di creano pagine del sito per un sito di SharePoint. Per altre informazioni, vedere [tipi di pagine di SharePoint](http://go.microsoft.com/fwlink/?LinkID=211584).

## <a name="create-an-application-page"></a>Creare una pagina applicazione
 Per creare una pagina applicazione, aggiungere un' **pagina dell'applicazione** elemento a un progetto SharePoint. Quando si crea una pagina applicazione, Visual Studio aggiunge le cartelle seguenti al progetto:

|Cartella|Descrizione|
|------------|-----------------|
|Layout|Esegue il mapping alla directory LAYOUTS virtuale del file system di SharePoint.|
|Sottocartella di layout|Contiene i file che costituiscono la pagina dell'applicazione. Per impostazione predefinita, questa cartella ha lo stesso nome del progetto. È possibile rinominare la cartella in qualsiasi momento. Quando si esegue il progetto, Visual Studio distribuisce questa cartella alla directory LAYOUTS virtuale del file system di SharePoint.|

 Visual Studio aggiunge i file seguenti al progetto:

|File|Descrizione|
|----------|-----------------|
|File della pagina ASP.NET (*aspx*)|Contiene il markup XML che definisce la pagina.|
|File di codice pagina applicazione|Contiene il codice dietro la pagina dell'applicazione. Aggiungere il codice che gestisce gli eventi per questo file.|
|File di codice della finestra di progettazione pagina applicazione|Contiene il codice generato dalla finestra di progettazione. Non modificare direttamente il file.|

## <a name="design-and-debug-an-application-page"></a>Progettare ed eseguire il debug di una pagina dell'applicazione
 Progettare il contenuto di una pagina dell'applicazione utilizzando la visualizzazione di progettazione in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre la pagina dell'applicazione nel progetto (facendovi doppio clic o aprendo il relativo menu di scelta rapida e scegliendo **apre**) e quindi scegliere il **progettazione** pulsante nella parte inferiore della l'editor.

> [!NOTE]
>  È possibile progettare la pagina solo nella **origine** visualizzazione della finestra di progettazione. Il **progettazione** visualizzazione della finestra di progettazione è disabilitata per le pagine dell'applicazione.

 È possibile eseguire il debug di una pagina dell'applicazione esattamente come si potrebbero eseguire il debug di altri elementi del progetto SharePoint in Visual Studio. Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.

 Per visualizzare la pagina dell'applicazione, è necessario passare manualmente al percorso della pagina applicazione (ad esempio: http://<em>nome_server</em>/_layouts/*Project_Name*/ApplicationPage1.aspx).

 Per altre informazioni su come eseguire il debug di progetti SharePoint, vedere [risolvere i problemi di SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="choose-a-master-page"></a>Scegliere una pagina master
 Per impostazione predefinita, un' **pagina dell'applicazione** elemento fa riferimento alla pagina master del sito che si usa per il debug del progetto. Che pagina denominata v4. master ed è possibile trovare è inclusa nell'elenco il **raccolta pagine Master** del sito di SharePoint.

 È possibile modificare in modo esplicito la pagina master viene utilizzata dalla pagina dell'applicazione impostando il `MasterPageFile` attributo dell'applicazione `Page` elemento. (Ad esempio: `MasterPageFile="~/_layouts/applicationv4.master"`). In effetti, è necessario impostare questo attributo se le pagine master dinamiche non sono abilitate nel server SharePoint. Per altre informazioni sulle pagine master in SharePoint, vedere [pagine Master](http://go.microsoft.com/fwlink/?LinkID=169281).

## <a name="see-also"></a>Vedere anche
- [Sviluppo per SharePoint Foundation in profondità](http://go.microsoft.com/fwlink/?LinkID=182103)
- [Panoramica di ASP.NET](/aspnet/overview)
- [ASP.NET Web Pages](/aspnet/web-pages/index)
