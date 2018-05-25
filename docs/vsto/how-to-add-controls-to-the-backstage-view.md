---
title: 'Procedura: aggiungere controlli alla visualizzazione Backstage '
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- customizing the Ribbon, menus
- controls, Ribbon
- menus, customizing
- Microsoft Office Button
- custom Ribbon, menus
- Ribbon, customizing
- Office button
- Ribbon, menus
- Microsoft Office Menu
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 6b775c7613b8cc0953e419b2546ec017c96e8454
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procedura: aggiungere controlli alla visualizzazione Backstage
  È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic il **File** scheda. Quando si esegue l'applicazione, i controlli aggiunti per il **File** scheda visualizzata un gruppo denominato **Add-ins**.  
  
 È possibile posizionare i controlli prima o dopo i controlli incorporati utilizzando la finestra di progettazione della barra multifunzione in Visual Studio. Un controllo incorporato è un controllo che è già presente nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli incorporati, è necessario utilizzare un XML della barra multifunzione. Per ulteriori informazioni su **della barra multifunzione (XML)**, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md). Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere [Introduzione alla visualizzazione Backstage di Office 2010 per gli sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### <a name="to-add-controls-to-backstage-view"></a>Per aggiungere controlli alla visualizzazione Backstage  
  
1.  Aprire l'elemento barra multifunzione in visualizzazione progettazione.  
  
     Per informazioni su come aggiungere un **della barra multifunzione (finestra di progettazione visiva)** elemento al progetto, vedere [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).  
  
2.  Nella finestra di progettazione della barra multifunzione, fare clic su di **File** scheda.  
  
     Verrà visualizzata una finestra di progettazione di menu. Questa area di progettazione non contiene tutti i controlli.  
  
3.  Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare uno qualsiasi dei seguenti controlli nella finestra di progettazione dal menu:  
  
    -   Button  
  
    -   CheckBox  
  
    -   Raccolta  
  
    -   Menu  
  
    -   Separatore  
  
    -   SplitButton  
  
    -   ToggleButton  
  
4.  Trascinare i controlli per spostarli in una nuova posizione del menu.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Barra multifunzione XML](../vsto/ribbon-xml.md)   
 [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)   
 [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)  
  
  