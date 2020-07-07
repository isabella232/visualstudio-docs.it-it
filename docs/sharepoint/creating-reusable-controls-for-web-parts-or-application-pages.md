---
title: Creazione di controlli riutilizzabili per Web part o pagine dell'applicazione | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b174e1e16802838f19cec6dce727ea3199df730f
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86015139"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Creazione di controlli riutilizzabili per Web part o pagine applicazione
  In Visual Studio è possibile creare controlli riutilizzabili personalizzati che possono essere utilizzati dalle pagine applicazione e dalle Web part eseguite in SharePoint. Questi controlli sono denominati controlli utente. Un controllo utente è un tipo di controllo composito che funziona in modo molto simile a una pagina Web di ASP.NET: è possibile aggiungere controlli server Web e markup esistenti a un controllo utente e definire proprietà e metodi per il controllo. È quindi possibile incorporarli nelle pagine Web di ASP.NET, in cui agiscono come unità.

## <a name="create-a-user-control"></a>Creare un controllo utente
 Per creare un controllo utente, aggiungere un **controllo utente** a un **progetto SharePoint vuoto**. Per altre informazioni, vedere [procedura: creare un controllo utente per una pagina dell'applicazione di SharePoint o una Web part](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).

 Quando si aggiunge un elemento di **controllo utente** , Visual Studio crea una cartella nel progetto e quindi aggiunge diversi file alla cartella. Nella tabella seguente vengono descritti i singoli file.

|File|Descrizione|
|----------|-----------------|
|File di controllo utente|Definisce il controllo utente. Progettare il controllo utente aggiungendo controlli e markup a questo file.|
|File di codice|Contiene il codice dietro il controllo utente. Aggiungere il codice per gestire gli eventi in questo file.|
|File di codice della finestra di progettazione|Contiene il codice generato dalla finestra di progettazione e non deve essere modificato direttamente.|

## <a name="design-the-user-control"></a>Progettare il controllo utente
 Progettare il controllo utente usando la finestra di progettazione di Visual Web Developer in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre il file di controllo utente nel progetto e si sceglie la scheda **progettazione** .

## <a name="consume-the-user-control"></a>Utilizzare il controllo utente
 I controlli utente non vengono visualizzati in SharePoint finché non vengono inclusi in una pagina dell'applicazione o in una Web part.

 Per includere un controllo utente in una pagina dell'applicazione, aprire la pagina Web a cui si desidera aggiungere il controllo utente ASP.NET. Passare alla visualizzazione progettazione, quindi selezionare il file di controllo utente personalizzato in Esplora soluzioni e trascinarlo nella pagina. Il controllo utente ASP.NET viene aggiunto alla pagina e la finestra di progettazione crea la direttiva @ Register, necessaria affinché la pagina riconosca il controllo utente. È ora possibile usare i metodi e le proprietà pubbliche del controllo.

 Per includere un controllo utente in una Web part, aggiungere il controllo utente alla raccolta web part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> nel file di codice della web part. Nell'esempio seguente viene aggiunto un controllo utente alla <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> raccolta di una Web part.

 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]

## <a name="debug-a-user-control"></a>Eseguire il debug di un controllo utente
 Per eseguire il debug di un controllo utente, assicurarsi che il controllo utente sia incluso in una pagina dell'applicazione o in una Web part nel progetto SharePoint. È quindi possibile eseguire il debug del codice nel controllo utente nello stesso modo in cui si esegue il debug del codice in qualsiasi progetto di Visual Studio.

 Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.

 In SharePoint aprire la pagina applicazione che include il controllo utente. Se il controllo utente è incluso in una Web part, aggiungere la Web part a una pagina Web part in SharePoint.

 Per ulteriori informazioni sul debug di progetti SharePoint, vedere [risolvere i problemi relativi alle soluzioni di SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).

## <a name="related-topics"></a>Argomenti correlati

|Titolo|Descrizione|
|-----------|-----------------|
|[Procedura: creare un controllo utente per una Web part o una pagina dell'applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Viene illustrato come creare controlli personalizzati riutilizzabili che possono essere utilizzati dalle pagine dell'applicazione e Web part eseguiti in SharePoint.|
