---
title: 'Procedura: aggiungere controlli alla visualizzazione Backstage '
ms.date: 02/02/2017
ms.topic: how-to
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5b4ea5cdcd869f16f987e9431359511831af9573
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85538346"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procedura: aggiungere controlli alla visualizzazione Backstage
  È possibile utilizzare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic sulla scheda **file** . Quando si esegue l'applicazione, i controlli aggiunti alla scheda **file** vengono visualizzati in un gruppo denominato **componenti**aggiuntivi.

 Non è possibile posizionare i controlli prima o dopo i controlli incorporati tramite la finestra di progettazione della barra multifunzione in Visual Studio. Un controllo incorporato è un controllo già visualizzato nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli incorporati, è necessario utilizzare un XML della barra multifunzione. Per ulteriori informazioni sulla **barra multifunzione (XML)**, vedere [Ribbon XML](../vsto/ribbon-xml.md). Per ulteriori informazioni sulla personalizzazione della visualizzazione Backstage, vedere [Introduzione alla visualizzazione Backstage di office 2010 per gli sviluppatori](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) e [personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori](/previous-versions/office/developer/office-2010/ee815851(v=office.14)).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Per aggiungere controlli alla visualizzazione Backstage

1. Aprire l'elemento della barra multifunzione in visualizzazione progettazione.

     Per informazioni su come aggiungere un elemento **barra multifunzione (finestra di progettazione visiva)** al progetto, vedere [procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Nella finestra di progettazione della barra multifunzione fare clic sulla scheda **file** .

     Viene visualizzata una finestra di progettazione dei menu. Questa area di progettazione non contiene controlli.

3. Dalla scheda **controlli barra multifunzione di Office** della **casella degli strumenti**trascinare uno dei seguenti controlli nella finestra di progettazione menu:

    - Button

    - CheckBox

    - Raccolta

    - Menu

    - Separatore

    - SplitButton

    - ToggleButton

4. Trascinare i controlli per spostarli in nuove posizioni nel menu.

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura: iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura dettagliata: creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
