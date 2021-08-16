---
title: Creazione di controlli riutilizzabili per Web part o pagine applicazione | Microsoft Docs
titleSuffix: ''
description: Creare controlli personalizzati e riutilizzabili (controlli utente) in Visual Studio che possono essere utilizzati dalle pagine dell'applicazione e dalle web part eseguite in SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 263396167ea99aab30c965ee5c5bee571ceccbd4dae09979e156374c3be554c0
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425557"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Creare controlli riutilizzabili per web part o pagine dell'applicazione
  In Visual Studio è possibile creare controlli riutilizzabili personalizzati che possono essere utilizzati dalle pagine applicazione e dalle Web part eseguite in SharePoint. Questi controlli sono detti controlli utente. Un controllo utente è un tipo di controllo composito che funziona in modo molto simile a una pagina Web ASP.NET. È possibile aggiungere controlli server Web e markup esistenti a un controllo utente e definire proprietà e metodi per il controllo. È quindi possibile incorporarli nelle ASP.NET Web, dove fungono da unità.

## <a name="create-a-user-control"></a>Creare un controllo utente
 Per creare un controllo utente, aggiungere un **controllo utente** a un controllo **SharePoint Project**. Per altre informazioni, vedere Procedura: Creare un controllo utente per una [SharePoint'applicazione o una web part.](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)

 Quando si aggiunge un **elemento Controllo** utente, Visual Studio crea una cartella nel progetto e quindi aggiunge diversi file alla cartella. Nella tabella seguente vengono descritti i singoli file.

|File|Descrizione|
|----------|-----------------|
|File di controllo utente|Definisce il controllo utente. Progettare il controllo utente aggiungendo controlli e markup a questo file.|
|File di codice|Contiene il codice dietro il controllo utente. Aggiungere codice per gestire gli eventi in questo file.|
|File di codice della finestra di progettazione|Contiene il codice generato dalla finestra di progettazione e non deve essere modificato direttamente.|

## <a name="design-the-user-control"></a>Progettare il controllo utente
 Progettare il controllo utente usando la finestra di progettazione di Visual Web Developer in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre il file del controllo utente nel progetto e si sceglie **la scheda** Progettazione.

## <a name="consume-the-user-control"></a>Utilizzare il controllo utente
 I controlli utente non vengono visualizzati in SharePoint fino a quando non vengono inclusi in una pagina dell'applicazione o in una web part.

 Per includere un controllo utente in una pagina dell'applicazione, aprire la pagina Web a cui si vuole aggiungere il controllo ASP.NET utente. Passare alla visualizzazione Progettazione, selezionare il file del controllo utente personalizzato in Esplora soluzioni e trascinarlo nella pagina. Il ASP.NET utente viene aggiunto alla pagina e la finestra di progettazione crea la direttiva @ Register, necessaria per il riconoscimento del controllo utente da parte della pagina. È ora possibile usare le proprietà e i metodi pubblici del controllo.

 Per includere un controllo utente in una web part, aggiungere il controllo utente alla raccolta web part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> nel file di codice della web part. Nell'esempio seguente viene aggiunto un controllo utente alla <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> raccolta di una web part.

 :::code language="vb" source="../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb" id="Snippet5":::
 :::code language="csharp" source="../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs" id="Snippet5":::

## <a name="debug-a-user-control"></a>Eseguire il debug di un controllo utente
 Per eseguire il debug di un controllo utente, assicurarsi che il controllo utente sia incluso in una pagina dell'applicazione o in una web part nel SharePoint progetto. È quindi possibile eseguire il debug del codice nel controllo utente esattamente come si esegue il debug del codice in qualsiasi Visual Studio Project.

 Quando si avvia il debugger Visual Studio, Visual Studio apre il SharePoint corrente.

 In SharePoint aprire la pagina dell'applicazione che include il controllo utente. Se il controllo utente è incluso in una web part, aggiungere la web part a una pagina web part in SharePoint.

 Per altre informazioni sul debug di SharePoint, vedere [Risolvere i problemi relativi SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: Creare un controllo utente per una pagina SharePoint o una web part dell'applicazione](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Illustra come creare controlli personalizzati e riutilizzabili che possono essere utilizzati dalle pagine dell'applicazione Web part che vengono eseguiti in SharePoint.|
