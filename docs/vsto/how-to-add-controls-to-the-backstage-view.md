---
title: 'Procedura: Aggiungere controlli alla visualizzazione Backstage '
description: Informazioni su come usare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu che si apre quando si fa clic sulla scheda File.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: f667011410938af59bf0f50f3ac5ece833157557
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710088"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procedura: Aggiungere controlli alla visualizzazione Backstage
  È possibile usare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si fa clic sulla **scheda File** . Quando si esegue l'applicazione, i controlli aggiunti alla scheda **File** vengono visualizzati in un gruppo denominato **Componenti aggiuntivi.**

 Non è possibile posizionare i controlli prima o dopo i controlli predefiniti usando la finestra di progettazione della barra multifunzione in Visual Studio. Un controllo incorporato è un controllo già visualizzato nella visualizzazione Backstage. Se si desidera posizionare i controlli prima o dopo i controlli predefiniti, è necessario usare un xml della barra multifunzione. Per altre informazioni sulla barra **multifunzione (XML),** vedere [XML della barra multifunzione.](../vsto/ribbon-xml.md) Per altre informazioni sulla personalizzazione della visualizzazione Backstage, vedere Introduction [to the Office 2010 Backstage view for developers](/previous-versions/office/developer/office-2010/ee691833(v=office.14)) (Introduzione alla visualizzazione Backstage di Office 2010 per gli sviluppatori) e Customize the Office [2010 Backstage view for developers](/previous-versions/office/developer/office-2010/ee815851(v=office.14))(Personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Per aggiungere controlli alla visualizzazione Backstage

1. Aprire l'elemento Barra multifunzione nella visualizzazione Progettazione.

     Per informazioni su come aggiungere un elemento della barra **multifunzione (finestra** di progettazione visiva) al progetto, vedere Procedura: Iniziare a personalizzare [la barra multifunzione.](../vsto/how-to-get-started-customizing-the-ribbon.md)

2. Nella finestra di progettazione della barra multifunzione fare clic **sulla scheda File** .

     Verrà visualizzata una finestra di progettazione menu. Questa area di progettazione non contiene controlli.

3. Dalla scheda **Office della casella** degli strumenti trascinare uno dei controlli seguenti nella finestra di progettazione menu:

    - Button

    - CheckBox

    - Raccolta

    - Menu

    - Separatore

    - SplitButton

    - ToggleButton

4. Trascinare i controlli per spostarli in nuove posizioni nel menu.

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
