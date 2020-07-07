---
title: 'Procedura: creare una Web part di SharePoint tramite una finestra di progettazione | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], designer
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 0830cec748d68f010397c42334a5ed83365ee6b7
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016475"
---
# <a name="how-to-create-a-sharepoint-web-part-by-using-a-designer"></a>Procedura: creare una Web part di SharePoint tramite una finestra di progettazione
  È possibile creare una Web part aggiungendo un elemento **Web part visiva** a qualsiasi progetto SharePoint. Verrà visualizzata la finestra di progettazione di Visual Web Developer in Visual Studio, in cui è possibile aggiungere controlli e codice alla web part. Le web part visive funzionano in modo analogo alle web part. L'unica differenza è rappresentata dal fatto che si progettano Web part visive in Visual Web Developer Designer.

### <a name="to-create-a-project-for-visual-web-parts"></a>Per creare un progetto per Web part visive

1. Sulla barra dei menu scegliere **file**  > **nuovo**  >  **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. Nella finestra di dialogo **nuovo progetto** , in **Visual C#** o **Visual Basic**, espandere il nodo **Office/SharePoint** , quindi scegliere la categoria **soluzioni SharePoint** .

3. Nell'elenco dei modelli di progetto scegliere **SharePoint 2013-Web part visiva**, quindi scegliere il pulsante **OK** .

     Viene visualizzata la **personalizzazione guidata SharePoint** .

4. Nella pagina **specificare il sito e il livello di sicurezza per il debug** specificare l'URL di un sito di SharePoint che si trova nel computer locale, quindi scegliere il pulsante **fine** .

     In **Esplora soluzioni**, viene visualizzata una Web part. Dopo aver progettato la Web part in Visual Web Developer Designer, è possibile eseguirne il test nel sito specificato.

### <a name="to-add-a-visual-web-part-to-an-existing-sharepoint-project"></a>Per aggiungere una Web part visiva a un progetto SharePoint esistente

1. Sulla barra dei menu scegliere **progetto**  >  **Aggiungi nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** scegliere il nodo **Office/SharePoint** .

3. Nell'elenco dei modelli di progetto scegliere **Web part visiva**, denominarlo, quindi scegliere il pulsante **Aggiungi** .

     In **Esplora soluzioni**viene visualizzata la Web part. Dopo aver progettato la Web part in Visual Web Developer Designer, è possibile eseguirne il test nel sito specificato.

## <a name="see-also"></a>Vedere anche
- [Creazione di Web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)
- [Procedura: creare una Web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)
- [Procedura dettagliata: creare una Web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [Procedura dettagliata: creare una Web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
