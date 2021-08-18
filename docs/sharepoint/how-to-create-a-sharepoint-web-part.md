---
title: 'Procedura: Creare una SharePoint web part | Microsoft Docs'
description: Creare e personalizzare una web part usando una finestra di progettazione oppure aggiungendo un elemento web part a qualsiasi progetto SharePoint e quindi modificando il file di codice per la web part.
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
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: ad3761012732f6191d40bfdf47da84221b78209e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130988"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>Procedura: Creare una SharePoint web part
  È possibile creare e personalizzare una web part aggiungendo un elemento web **part** SharePoint qualsiasi progetto e quindi modificando il file di codice per la web part o usando una finestra di progettazione. Per altre informazioni, vedere Procedura: Creare una SharePoint [web part usando una finestra di progettazione.](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)

### <a name="to-create-a-sharepoint-web-part"></a>Per creare una SharePoint web part

1. Creare o aprire un progetto SharePoint.

     Per altre informazioni, vedere Modelli [SharePoint progetto e elemento di progetto](../sharepoint/sharepoint-project-and-project-item-templates.md).

2. Scegliere il SharePoint progetto **in** Esplora soluzioni e quindi **scegliere** Project Aggiungi nuovo  >  **elemento**.

3. Nella finestra **di dialogo Aggiungi nuovo** elemento espandere il **nodo** SharePoint e quindi scegliere il **nodo 2010.**

4. Nell'elenco dei SharePoint modelli scegliere **Web part**.

5. Nella casella **Nome** specificare un nome per la web part e quindi scegliere il **pulsante** Aggiungi.

     La web part viene visualizzata in **Esplora soluzioni**. Per altre informazioni sui file inclusi in una web part, vedere [Creare web part per](../sharepoint/creating-web-parts-for-sharepoint.md)SharePoint .

6. In **Esplora soluzioni** aprire il file di codice per la web part appena creata.

     Ad esempio, se il nome della web part è *WebPart1,* aprire *WebPart1.vb* (in Visual Basic) o *WebPart1.cs* (in C#).

7. Nel file di codice aggiungere controlli al metodo <xref:System.Web.UI.Control.CreateChildControls%2A>.

     Per un esempio, vedere [Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md).

## <a name="see-also"></a>Vedi anche
- [Creare web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Procedura: Creare una SharePoint web part usando una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [Procedura dettagliata: Creare una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procedura dettagliata: Creare una web part per SharePoint usando una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
