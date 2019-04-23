---
title: 'Procedura: Aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione'
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
ms.openlocfilehash: 9d831cb629665e641394d011bd11eb74481c4f94
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60087183"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Procedura: Aggiungere un pulsante di visualizzazione della finestra di dialogo a un gruppo della barra multifunzione
  È possibile aggiungere una visualizzazione finestra di dialogo a un gruppo in una barra multifunzione. Visualizzazione di una finestra di dialogo è una piccola icona visualizzata in un gruppo. Gli utenti fanno clic sull'icona per aprire finestre di dialogo correlate o riquadri attività che forniscono ulteriori opzioni correlate al gruppo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Per aggiungere una visualizzazione finestra di dialogo a un gruppo della barra multifunzione

1. Selezionare il file di codice della barra multifunzione (*vb* oppure *cs* file) in **Esplora**.

2. Nel **View** menu, fare clic su **progettazione**.

3. Nella finestra di progettazione della barra multifunzione, fare doppio clic su qualsiasi gruppo e quindi fare clic su **Aggiungi DialogBoxLauncher**.

     Aggiungere il codice per il <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> eventi del gruppo per aprire una finestra di dialogo personalizzata o incorporata.

## <a name="see-also"></a>Vedere anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Procedure dettagliate ed esempi di sviluppo office](../vsto/office-development-samples-and-walkthroughs.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione alla barra multifunzione XML](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Modificare la posizione di una scheda della barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Introduzione alla personalizzazione della barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: Mostra errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Procedura dettagliata: Creare una scheda personalizzata utilizzando XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
