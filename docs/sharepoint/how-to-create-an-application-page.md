---
title: "Procedura: Creare una pagina dell'applicazione | Microsoft Docs"
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb5c4d7497525706384ced52caae1ba8e02f3e23
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60063023"
---
# <a name="how-to-create-an-application-page"></a>Procedura: Creare una pagina applicazione
  È possibile creare una pagina Web ASP.NET per uno o più siti di SharePoint. In SharePoint, queste pagine sono dette pagine dell'applicazione. A differenza di una pagina del sito, una pagina dell'applicazione contiene codice che viene eseguito dietro la pagina. Per altre informazioni, vedere [creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Per creare una pagina dell'applicazione

1. In Visual Studio aprire o creare un progetto SharePoint.

     Per altre informazioni, vedere [SharePoint modelli di elemento di progetto e progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Scegliere il nodo di progetto in **Esplora soluzioni**.

3. Nella barra dei menu scegliere **Progetto** > **Aggiungi nuovo elemento**.

4. Nel **Aggiungi nuovo elemento** finestra di dialogo espandere il **SharePoint** nodo e quindi scegliere il **2010** elemento.

5. Nell'elenco dei modelli di SharePoint, scegliere **pagina dell'applicazione**.

6. Nel **Name** casella, specificare un nome per la pagina dell'applicazione e quindi scegliere il **Add** pulsante.

     Visual Studio aggiunge diversi file e cartelle nel progetto. Per altre informazioni su questi file, vedere [creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     Nel **origine** visualizzazione della finestra di progettazione in Visual Web Developer, il file della pagina ASP.NET è disponibile. È possibile progettare la pagina aggiungendo i controlli dal **casella degli strumenti** e inserendoli nei segnaposti del contenuto. Per altre informazioni, vedere [visualizzazione origine, progettazione pagina Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Se si desidera gestire gli eventi di controllo, aggiungere il codice al file di codice per la pagina applicazione.

     Il file di codice viene visualizzato se si espande il nodo per il file della pagina ASP.NET e ha un *cs* oppure *vb* estensione, a seconda del linguaggio del progetto. Per un esempio end-to-end di come creare una pagina applicazione, vedere [procedura dettagliata: Creare una pagina dell'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Vedere anche
- [Creare le pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Procedura dettagliata: Creare una pagina dell'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
