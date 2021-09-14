---
title: "Procedura: Aggiungere un'icona di avvio di una finestra di dialogo a un gruppo della barra multifunzione"
description: È possibile aggiungere un'icona di avvio della finestra di dialogo a qualsiasi gruppo di una barra multifunzione in grado di aprire finestre di dialogo o riquadri attività correlati che forniscono altre opzioni correlate al gruppo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- dialog box launcher [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], dialog box launcher
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 43ff3dec0245759c35dd8fc4165dc7b279835cde
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710099"
---
# <a name="how-to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Procedura: Aggiungere un'icona di avvio di una finestra di dialogo a un gruppo della barra multifunzione
  È possibile aggiungere un'icona di avvio della finestra di dialogo a qualsiasi gruppo di una barra multifunzione. Un'icona di avvio della finestra di dialogo è una piccola icona visualizzata in un gruppo. Gli utenti fanno clic su questa icona per aprire finestre di dialogo o riquadri attività correlati che forniscono altre opzioni correlate al gruppo.

 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]

### <a name="to-add-a-dialog-box-launcher-to-a-ribbon-group"></a>Per aggiungere un'icona di avvio della finestra di dialogo a un gruppo della barra multifunzione

1. Selezionare il file di codice della barra multifunzione (file *con estensione vb* o *cs)* in **Esplora soluzioni**.

2. Scegliere **Progettazione** dal menu **Visualizza**.

3. Nella finestra di progettazione della barra multifunzione fare clic con il pulsante destro del mouse su qualsiasi gruppo e quindi scegliere **Aggiungi DialogBoxLauncher**.

     Aggiungere codice all'evento del gruppo per aprire una finestra di dialogo <xref:Microsoft.Office.Tools.Ribbon.RibbonGroup.DialogLauncherClick> personalizzata o incorporata.

## <a name="see-also"></a>Vedi anche
- [Panoramica della barra multifunzione](../vsto/ribbon-overview.md)
- [Accedere alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)
- [Office esempi di sviluppo e procedure dettagliate](../vsto/office-development-samples-and-walkthroughs.md)
- [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)
- [Panoramica del modello a oggetti della barra multifunzione](../vsto/ribbon-object-model-overview.md)
- [Ribbon XML](../vsto/ribbon-xml.md)
- [Procedura: Esportare una barra multifunzione dalla finestra di progettazione della barra multifunzione al codice XML della barra multifunzione](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md)
- [Procedura: Modificare la posizione di una scheda sulla barra multifunzione](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md)
- [Procedura: Personalizzare una scheda incorporata](../vsto/how-to-customize-a-built-in-tab.md)
- [Procedura: Aggiungere controlli alla visualizzazione backstage](../vsto/how-to-add-controls-to-the-backstage-view.md)
- [Personalizzare una barra multifunzione per Outlook](../vsto/customizing-a-ribbon-for-outlook.md)
- [Procedura: Iniziare a personalizzare la barra multifunzione](../vsto/how-to-get-started-customizing-the-ribbon.md)
- [Procedura: Visualizzare gli errori dell'interfaccia utente del componente aggiuntivo](../vsto/how-to-show-add-in-user-interface-errors.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)
- [Procedura dettagliata: Aggiornare i controlli in una barra multifunzione in fase di esecuzione](../vsto/walkthrough-updating-the-controls-on-a-ribbon-at-run-time.md)
- [Procedura dettagliata: Creare una scheda personalizzata usando il codice XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)
