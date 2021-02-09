---
title: Creare il controllo utente per la pagina o la Web part dell'app SharePoint
titleSuffix: ''
description: Creazione di controlli utente personalizzati che forniscono funzionalità personalizzate per la soluzione SharePoint e riutilizzo di tale funzionalità in una Web part o una pagina di applicazione.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- user controls [SharePoint development in Visual Studio], creating
- user controls [SharePoint development in Visual Studio], adding
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 43386f3ba450058d6aaf8ab180e331d2f303a235
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925584"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Procedura: creare un controllo utente per una Web part o una pagina dell'applicazione di SharePoint
  È possibile creare controlli utente personalizzati che forniscono funzionalità personalizzate per la soluzione SharePoint in uso, nonché riutilizzare le funzionalità in questione all'interno del progetto. È possibile includere i controlli utente in una web part o in una pagina applicazione, aggiungere altri controlli ASP.NET e di SharePoint e definire proprietà e metodi per il controllo. Per ulteriori informazioni sui controlli utente, vedere [creare controlli riutilizzabili per Web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) e [controlli utente e controlli server in SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Per creare un controllo utente per SharePoint

1. In Visual Studio aprire o creare un progetto SharePoint.

     Vedere [modelli di progetti e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Scegliere il nodo di progetto in **Esplora soluzioni**.

3. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

4. Nel riquadro **installato** scegliere il nodo **Office/SharePoint** .

5. Nell'elenco dei modelli di SharePoint scegliere **controllo utente (solo soluzione farm)**.

    > [!NOTE]
    > I controlli utente possono essere utilizzati solo nelle soluzioni farm.

6. Nella casella **nome** specificare un nome per il controllo utente, quindi scegliere il pulsante **Aggiungi** .

     Visual Studio aggiunge diversi file e cartelle al progetto. Per ulteriori informazioni su questi file, vedere [creare controlli riutilizzabili per Web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md).

     Per impostazione predefinita, il file di controllo utente viene visualizzato nella visualizzazione **origine** della finestra di progettazione di Visual Web Developer. In questa visualizzazione è possibile modificare il markup XML del controllo. È possibile passare alla visualizzazione **progettazione** se si desidera progettare visivamente il controllo trascinando i controlli dalla **casella degli strumenti**. Vedere [visualizzazione progettazione, progettazione pagina Web](/previous-versions/aspnet/ms178149\(v\=vs.100\)).

7. Se si desidera gestire eventi che si verificano nel controllo, aggiungere codice al file di codice del controllo utente.

     Questo file viene visualizzato in **Esplora soluzioni** nel file di controllo utente e ha un'estensione *CS* o *VB* , a seconda del linguaggio del progetto.

## <a name="see-also"></a>Vedi anche
- [Creazione di controlli riutilizzabili per Web part o pagine applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
