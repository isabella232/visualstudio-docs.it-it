---
title: Creare un controllo utente per SharePoint o web part dell'app
titleSuffix: ''
description: Creare controlli utente personalizzati che forniscono funzionalità personalizzate per la soluzione SharePoint e riutilizzare tale funzionalità all'interno di una web part o di una pagina dell'applicazione.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 9a622fa1d85ed916a393d7ea4cac56a335d550f3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711443"
---
# <a name="how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part"></a>Procedura: Creare un controllo utente per una SharePoint o una web part dell'applicazione
  È possibile creare controlli utente personalizzati che forniscono funzionalità personalizzate per la soluzione SharePoint in uso, nonché riutilizzare le funzionalità in questione all'interno del progetto. È possibile includere i controlli utente in una web part o in una pagina applicazione, aggiungere altri controlli ASP.NET e di SharePoint e definire proprietà e metodi per il controllo. Per altre informazioni sui controlli utente, vedere Creare controlli riutilizzabili per [web](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md) part o pagine dell'applicazione e Controlli utente e controlli [server in SharePoint](https://blogs.msdn.microsoft.com/kaevans/2011/04/28/user-controls-and-server-controls-in-sharepoint/).

### <a name="to-create-a-user-control-for-sharepoint"></a>Per creare un controllo utente per SharePoint

1. In Visual Studio aprire o creare un progetto SharePoint.

     Vedere [SharePoint di progetto e di elemento di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Scegliere il nodo di progetto in **Esplora soluzioni**.

3. Nella barra dei menu **scegliere** Project Aggiungi nuovo  >  **elemento**.

     Verrà **visualizzata la finestra di dialogo** Aggiungi nuovo elemento .

4. Nel riquadro **Installato** scegliere il nodo **Office/SharePoint.**

5. Nell'elenco dei modelli SharePoint scegliere **Controllo utente (solo soluzione farm)**.

    > [!NOTE]
    > I controlli utente possono essere utilizzati solo nelle soluzioni farm.

6. Nella casella **Nome** specificare un nome per il controllo utente e quindi scegliere il **pulsante** Aggiungi.

     Visual Studio aggiunge diverse cartelle e file al progetto. Per altre informazioni su questi file, vedere [Creare controlli riutilizzabili per web part o pagine dell'applicazione.](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)

     Per impostazione predefinita, il file del controllo utente viene visualizzato nella **visualizzazione Origine** della finestra di progettazione di Visual Web Developer. In questa visualizzazione è possibile modificare il markup XML del controllo. È possibile passare alla **visualizzazione Progettazione** se si vuole progettare il controllo visivamente trascinando i controlli dalla Casella **degli strumenti**. Vedere [Visualizzazione Progettazione, Progettazione pagine Web.](/previous-versions/aspnet/ms178149\(v\=vs.100\))

7. Se si desidera gestire eventi che si verificano nel controllo, aggiungere codice al file di codice del controllo utente.

     Questo file viene visualizzato **Esplora soluzioni** nel file di controllo utente e ha estensione *cs* o *vb,* a seconda del linguaggio del progetto.

## <a name="see-also"></a>Vedi anche
- [Creare controlli riutilizzabili per web part o pagine dell'applicazione](../sharepoint/creating-reusable-controls-for-web-parts-or-application-pages.md)
- [Creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
