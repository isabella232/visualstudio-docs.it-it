---
title: Creazione di controlli utente riutilizzabili per Web part o pagine di applicazione | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- SharePoint development in Visual Studio, user controls
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 7d042c42bae59c6dbf92f0e381444cc011b40db0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842823"
---
# <a name="create-reusable-controls-for-web-parts-or-application-pages"></a>Creare controlli utente riutilizzabili per web part o pagine applicazione
  In Visual Studio è possibile creare controlli riutilizzabili personalizzati che possono essere utilizzati dalle pagine applicazione e dalle Web part eseguite in SharePoint. Questi controlli sono denominati controlli utente. Un controllo utente è un tipo di controllo composito che funziona in modo analogo a una pagina Web ASP.NET, è possibile aggiungere controlli server Web esistenti e il markup per un controllo utente e definire le proprietà e metodi per il controllo. È quindi possibile incorporarli nelle pagine Web ASP.NET, in cui vengono usate come un'unità.  
  
## <a name="create-a-user-control"></a>Creare un controllo utente
 Per creare un controllo utente, aggiungere un **UserControl** a un **progetto SharePoint vuoto**. Per altre informazioni, vedere [Procedura: Creare un controllo utente per una parte di pagina o web dell'applicazione SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md).  
  
 Quando si aggiunge un **controllo utente** item, Visual Studio crea una cartella nel progetto e quindi vengono aggiunti alcuni file nella cartella. La tabella seguente descrive ogni file.  
  
|File|Descrizione|  
|----------|-----------------|  
|File di controllo utente|Definisce il controllo utente. Progettare il controllo utente mediante l'aggiunta di controlli e codice per questo file.|  
|File di codice|Contiene il codice dietro il controllo utente. Aggiungere il codice per gestire gli eventi per questo file.|  
|File di codice della finestra di progettazione|Contiene il codice generato dalla finestra di progettazione e non deve essere modificato direttamente.|  
  
## <a name="design-the-user-control"></a>Progettare il controllo utente
 Progettare il controllo utente utilizzando la finestra di progettazione di Visual Web Developer in Visual Studio. Questa finestra di progettazione viene visualizzata quando si apre il file di controllo utente nel progetto e scegliere il **progettazione** scheda.  

## <a name="consume-the-user-control"></a>Usare il controllo utente
 Controlli utente non vengono visualizzati in SharePoint fino a quando non verranno inclusi in una pagina dell'applicazione o una Web Part.  
  
 Per includere un controllo utente in una pagina applicazione, aprire la pagina Web a cui si desidera aggiungere il controllo utente ASP.NET. Passare alla visualizzazione progettazione, quindi selezionare il file di controllo utente personalizzato in Esplora soluzioni e trascinarla nella pagina. Il controllo utente ASP.NET viene aggiunto alla pagina e la finestra di progettazione crea la direttiva @ Register, che è necessaria per la pagina riconoscere il controllo utente. È ora possibile utilizzare con le proprietà pubbliche e i metodi del controllo.  
  
 Per includere un controllo utente in una Web Part, aggiungere il controllo utente per la Web Part <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> raccolta nel file di codice di Web Part. L'esempio seguente aggiunge un controllo utente per il <xref:System.Web.UI.WebControls.WebParts.Part.Controls%2A> raccolta di una Web Part.  
  
 [!code-vb[SP_VisualWebPart#5](../sharepoint/codesnippet/VisualBasic/sp_visualwebpart.vb/visualwebpart1/visualwebpart1.vb#5)]
 [!code-csharp[SP_VisualWebPart#5](../sharepoint/codesnippet/CSharp/sp_visualwebpart.cs/visualwebpart1/visualwebpart1.cs#5)]  
  
## <a name="debug-a-user-control"></a>Eseguire il debug di un controllo utente
 Per eseguire il debug di un controllo utente, verificare che il controllo utente sia incluso in una pagina dell'applicazione o Web Part nel progetto di SharePoint. È quindi possibile eseguire il debug codice nel controllo utente esattamente come si potrebbe eseguire il debug di codice in qualsiasi progetto di Visual Studio.  
  
 Quando si avvia il debugger di Visual Studio, Visual Studio apre il sito di SharePoint.  
  
 In SharePoint, aprire la pagina dell'applicazione che include il controllo utente. Se il controllo utente è incluso in una Web Part, aggiungere la Web Part a una pagina Web Part in SharePoint.  
  
 Per altre informazioni sul debug di progetti SharePoint, vedere [risolvere i problemi di SharePoint soluzioni](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## <a name="related-topics"></a>Argomenti correlati
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Procedura: Creare un controllo utente per una parte di pagina o web dell'applicazione SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Illustra come creare controlli personalizzati riutilizzabili che possono essere utilizzati dalle pagine dell'applicazione e dalle Web part eseguite in SharePoint.|  
