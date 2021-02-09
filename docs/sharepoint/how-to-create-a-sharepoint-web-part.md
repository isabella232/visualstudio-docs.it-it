---
title: 'Procedura: creare una Web part di SharePoint | Microsoft Docs'
description: Creare e personalizzare una Web part utilizzando una finestra di progettazione oppure aggiungendo un elemento Web part a qualsiasi progetto SharePoint e modificando quindi il file di codice per la Web part.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: f15cd788d19540bdea416b36ab0f8e8d8aa95e3a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925596"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Procedura: creare una Web part di SharePoint
  È possibile creare e personalizzare una Web part aggiungendo un elemento **Web part** a qualsiasi progetto SharePoint, quindi modificando il file di codice per la Web part o utilizzando una finestra di progettazione. Per ulteriori informazioni, vedere [procedura: creare una Web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).

### <a name="to-create-a-sharepoint-web-part"></a>Per creare una Web part di SharePoint

1. Creare o aprire un progetto SharePoint.

     Per ulteriori informazioni, vedere [modelli di progetto e di elementi di progetto SharePoint](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Scegliere il nodo del progetto SharePoint in **Esplora soluzioni** , quindi scegliere **progetto**  >  **Aggiungi nuovo elemento**.

3. Nella finestra di dialogo **Aggiungi nuovo elemento** espandere il nodo **SharePoint** , quindi scegliere il nodo **2010** .

4. Nell'elenco dei modelli di SharePoint scegliere **Web part**.

5. Nella casella **nome** specificare un nome per la Web part, quindi scegliere il pulsante **Aggiungi** .

     La Web part viene visualizzata in **Esplora soluzioni**. Per ulteriori informazioni sui file inclusi in una Web part, vedere [creare Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md).

6. In **Esplora soluzioni** aprire il file di codice per la Web part appena creata.

     Ad esempio, se il nome della web part è *WebPart1*, aprire *WebPart1. vb* (in Visual Basic) o *WebPart1.cs* (in C#).

7. Nel file di codice aggiungere controlli al metodo <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Per un esempio, vedere [procedura dettagliata: creare una Web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Vedi anche
- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Procedura: creare una Web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Procedura dettagliata: creare una Web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procedura dettagliata: creare una Web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
