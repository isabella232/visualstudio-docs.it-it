---
title: 'Procedura: Aggiungere controlli alla visualizzazione Backstage '
ms.date: 02/02/2017
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
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: c4241464fe8a43af882fbdbad0f898838e8fd897
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60068366"
---
# <a name="how-to-add-controls-to-the-backstage-view"></a>Procedura: Aggiungere controlli alla visualizzazione Backstage
  È possibile usare la finestra di progettazione della barra multifunzione per aggiungere controlli al menu visualizzato quando si sceglie la **File** scheda. Quando si esegue l'applicazione, i controlli aggiunti per il **File** scheda visualizzata un gruppo denominato **Add-ins**.

 È possibile posizionare i controlli prima o dopo i controlli incorporati tramite la finestra di progettazione della barra multifunzione in Visual Studio. Un controllo incorporato è un controllo già disponibile nella visualizzazione Backstage. Se si desidera posizionare controlli prima o dopo i controlli incorporati, è necessario utilizzare un formato XML della barra multifunzione. Per altre informazioni sulle **sulla barra multifunzione (XML)**, vedere [XML della barra multifunzione](../vsto/ribbon-xml.md). Per altre informazioni sulla personalizzazione della visualizzazione Backstage, vedere [Introduzione alla visualizzazione Backstage di Office 2010 per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182189) e [personalizzare la visualizzazione Backstage di Office 2010 per gli sviluppatori](http://go.microsoft.com/fwlink/?LinkId=182188).

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-controls-to-backstage-view"></a>Per aggiungere controlli alla visualizzazione Backstage

1. Aprire l'elemento della barra multifunzione in visualizzazione progettazione.

     Per informazioni su come aggiungere un **sulla barra multifunzione (finestra di progettazione visiva)** elemento al progetto, vedere [come: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md).

2. Nella finestra di progettazione della barra multifunzione, scegliere il **File** scheda.

     Verrà visualizzata una finestra di progettazione menu. Questa area di progettazione non contiene tutti i controlli.

3. Dal **controlli della barra multifunzione di Office** scheda della finestra di **della casella degli strumenti**, trascinare uno dei seguenti controlli nella finestra di progettazione menu:

    - Button

    - CheckBox

    - Raccolta

    - Menu

    - Separatore

    - SplitButton

    - ToggleButton

4. Trascinare i controlli per spostarle in una nuova posizione del menu.

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
