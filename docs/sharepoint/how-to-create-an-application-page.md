---
title: "Procedura: creare una pagina dell'applicazione | Microsoft Docs"
description: Creare una pagina Web ASP.NET (nota anche come pagina dell'applicazione) in Visual Studio per uno o più siti di SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
ms.openlocfilehash: df52ca75ef99fe98158cb5f874e59fe4ee0c47b4
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/18/2020
ms.locfileid: "94849857"
---
# <a name="how-to-create-an-application-page"></a>Procedura: creare una pagina dell'applicazione
  È possibile creare una pagina Web ASP.NET per uno o più siti di SharePoint. In SharePoint queste pagine sono denominate pagine dell'applicazione. Diversamente da una pagina del sito, una pagina dell'applicazione contiene il codice che viene eseguito dietro la pagina. Per ulteriori informazioni, vedere [creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

### <a name="to-create-an-application-page"></a>Per creare una pagina dell'applicazione

1. In Visual Studio aprire o creare un progetto SharePoint.

     Per ulteriori informazioni, vedere [modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Scegliere il nodo di progetto in **Esplora soluzioni**.

3. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

4. Nella finestra di dialogo **Aggiungi nuovo elemento** espandere il nodo **SharePoint** , quindi scegliere l'elemento **2010** .

5. Nell'elenco dei modelli di SharePoint scegliere **pagina applicazione**.

6. Nella casella **nome** specificare un nome per la pagina applicazione, quindi scegliere il pulsante **Aggiungi** .

     Visual Studio aggiunge diversi file e cartelle al progetto. Per ulteriori informazioni su questi file, vedere [creare pagine dell'applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md).

     Nella visualizzazione **origine** di Visual Web Developer Designer viene visualizzato il file di paging ASP.NET. È possibile progettare la pagina aggiungendo i controlli dalla **casella degli strumenti** e inserendoli nei segnaposto di contenuto. Per ulteriori informazioni, vedere [visualizzazione origine, progettazione pagina Web](/previous-versions/aspnet/ms178154\(v\=vs.100\)).

7. Se si desidera gestire gli eventi di controllo, aggiungere il codice al file di codice per la pagina applicazione.

     Il file di codice viene visualizzato se si espande il nodo per il file di paging ASP.NET con estensione *CS* o *VB* , a seconda del linguaggio del progetto. Per un esempio end-to-end di come creare una pagina dell'applicazione, vedere [procedura dettagliata: creare un'applicazione di SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md).

## <a name="see-also"></a>Vedere anche
- [Creazione di pagine applicazione per SharePoint](../sharepoint/creating-application-pages-for-sharepoint.md)
- [Procedura dettagliata: creare una pagina dell'applicazione SharePoint](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
