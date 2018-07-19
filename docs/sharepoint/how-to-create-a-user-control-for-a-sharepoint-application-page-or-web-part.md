---
title: 'Procedura: creare un controllo utente per una pagina di applicazione di SharePoint Web Part o | Microsoft Docs'
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 98333049f711e9d28d7adb1ad0c17cfc8514e4ad
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2018
ms.locfileid: "37118868"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Procedura: creare un controllo utente per una parte di pagina o web dell'applicazione SharePoint
  È possibile creare controlli utente personalizzati che forniscono funzionalità personalizzate per la soluzione SharePoint in uso, nonché riutilizzare le funzionalità in questione all'interno del progetto. È possibile includere i controlli utente in una web part o in una pagina applicazione, aggiungere altri controlli ASP.NET e di SharePoint e definire proprietà e metodi per il controllo. Per altre informazioni sui controlli utente, vedere [creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) e [controlli utente e controlli Server in SharePoint](http://blogs.msdn.com/b/kaevans/archive/2011/04/28/user-controls-and-server-controls-in-sharepoint.aspx).  
  
### <a name="to-create-a-user-control-for-sharepoint"></a>Per creare un controllo utente per SharePoint  
  
1.  In Visual Studio aprire o creare un progetto SharePoint.  
  
     Visualizzare [SharePoint modelli di elemento di progetto e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).  
  
2.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
3.  Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
4.  Nel **Installed** riquadro, scegliere il **Office/SharePoint** nodo.  
  
5.  Nell'elenco dei modelli di SharePoint, scegliere **controllo utente (solo soluzione Farm)**.  
  
    > [!NOTE]  
    >  I controlli utente possono essere utilizzati solo nelle soluzioni farm.  
  
6.  Nel **Name** casella, specificare un nome per il controllo utente e quindi scegliere il **Add** pulsante.  
  
     Visual Studio aggiunge diversi file e cartelle nel progetto. Per altre informazioni su questi file, vedere [creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).  
  
     Per impostazione predefinita, il file di controllo utente viene visualizzato nei **origine** visualizzazione della finestra di progettazione di Visual Web Developer. In questa visualizzazione è possibile modificare il markup XML del controllo. È possibile passare a **Design** visualizzare se si desidera progettare visivamente il controllo trascinando i controlli dalle **della casella degli strumenti**. Visualizzare [visualizzazione progettazione, progettazione pagina Web](http://msdn.microsoft.com/en-us/d8f2270a-357d-40a4-9b39-1a3f2366216d).  
  
7.  Se si desidera gestire eventi che si verificano nel controllo, aggiungere codice al file di codice del controllo utente.  
  
     Questo file viene visualizzato nella **Esplora soluzioni** sotto il file di controllo utente e ha una *cs* o *vb* estensione, a seconda del linguaggio del progetto.  
  
## <a name="see-also"></a>Vedere anche
 [Creare controlli utente riutilizzabili per web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)   
 [Creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)   
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)  
  
