---
title: 'Procedura: Aggiungere un pulsante di avvio della finestra di dialogo a un gruppo della barra multifunzione'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b930348845e04dca089cf153a11cc2a9fd29c880
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255898"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Procedura: Aggiungere un pulsante di avvio della finestra di dialogo a un gruppo della barra multifunzione
  È possibile aggiungere un pulsante di avvio della finestra di dialogo a qualsiasi gruppo su una barra multifunzione. Un pulsante di avvio della finestra di dialogo è una piccola icona visualizzata in un gruppo. Gli utenti fanno clic su questa icona per aprire finestre di dialogo correlate o riquadri attività che forniscono più opzioni correlate al gruppo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Per aggiungere un pulsante di avvio della finestra di dialogo a un gruppo della barra multifunzione

1. Selezionare il file di codice della barra multifunzione (file con*estensione VB* o *cs* ) in **Esplora soluzioni**.

2. Scegliere **finestra di progettazione**dal menu **Visualizza** .

3. Nella finestra di progettazione della barra multifunzione fare clic con il pulsante destro del mouse su un gruppo, quindi scegliere **Aggiungi DialogBoxLauncher**.

     Aggiungere codice all' <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> evento del gruppo per aprire una finestra di dialogo personalizzata o incorporata.

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Procedure dettagliate e esempi di sviluppo per Office](../vsto/office-development-samples-and-walkthroughs.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione Ribbon alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Modificare la posizione di una scheda sulla barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: Mostra errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
