---
title: Accessibilità nei Office di lavoro
description: Informazioni su Microsoft Office includono molte funzionalità di accessibilità che consentono di creare soluzioni personalizzate che soddisfano i requisiti di accessibilità standard.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 440eb9ee0e5d228280cc8a8052abc3e7267e681e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059894"
---
# <a name="accessibility-in-office-projects"></a>Accessibilità nei Office di lavoro

Microsoft Visual Studio e Microsoft Office includono molte funzionalità di accessibilità che consentono di creare soluzioni personalizzate che soddisfano i requisiti di accessibilità standard. Microsoft pubblica linee guida per l'accessibilità sul Web. Per informazioni dettagliate, vedere il sito [Web accessibilità](https://www.microsoft.com/accessibility/).

Nella maggior parte dei Office in Visual Studio standard di accessibilità o espone proprietà che è possibile impostare per rendere accessibili le soluzioni. Esistono tuttavia alcune funzionalità con accessibilità limitata.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Accessibilità in fase di progettazione

### <a name="use-shortcut-keys-in-document-level-projects"></a>Usare i tasti di scelta rapida nei progetti a livello di documento
 Quando una Microsoft Office documento di Word o una Microsoft Office Excel cartella di lavoro è aperta in Visual Studio, solo un'applicazione alla volta riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è  possibile fare in modo che Word o  Excel li riceva quando il documento ha lo stato attivo selezionando Combinazione di tasti dinamica nella pagina Tastiera **Impostazioni** della finestra di dialogo Opzioni. Per altre informazioni, vedere Microsoft Office tastiera di Word, Microsoft Office [tastiera Impostazioni,](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) finestra di dialogo Opzioni e tastiera Microsoft Office Excel, Microsoft Office [tastiera Impostazioni, finestra](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)di dialogo Opzioni .

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Visualizzare i tasti di scelta rapida per la barra multifunzione nei progetti a livello di documento
 Quando un documento di Word o una cartella di lavoro Excel è aperta in Visual Studio, non è possibile premere **ALT** per visualizzare i tasti di scelta rapida per le schede e i controlli sulla barra multifunzione. Per visualizzare i tasti di scelta rapida mentre il documento o la cartella di lavoro è aperta nella finestra di progettazione, seguire questa procedura.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Per visualizzare i tasti di scelta rapida per le schede e i controlli della barra multifunzione nella finestra di progettazione

1. In Visual Studio scegliere Opzioni **dal** menu **Strumenti**.

2. Espandere il **nodo Office Strumenti** e selezionare Microsoft Office Excel **tastiera** o Microsoft Office tastiera **di Word,** in base alle esigenze.

3. Selezionare **Schema di tastiera dinamico**.

     Viene visualizzato un messaggio che indica che è necessario riavviare Visual Studio per l'applicazione della modifica.

4. Fare clic su **OK**.

5. Riavviare Visual Studio e riaprire il progetto.

6. Aprire la finestra di progettazione del documento o della cartella di lavoro per il progetto.

7. Premere **F6** per visualizzare i tasti di scelta rapida per la barra multifunzione.

## <a name="accessibility-at-run-time"></a>Accessibilità in fase di esecuzione

### <a name="windows-forms-controls-on-office-documents"></a>Windows Controlli dei moduli Office documenti
 Windows I controlli Form espongono proprietà di accessibilità per fornire informazioni sul controllo agli strumenti di accessibilità, ad esempio le utilità per la lettura dello schermo. È possibile sfruttare queste proprietà di accessibilità quando i controlli si Office documento in una personalizzazione a livello di documento. Per altre informazioni, vedere [Fornire informazioni sull'accessibilità per i controlli in un Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Esistono tuttavia alcune limitazioni di accessibilità in fase di esecuzione quando Windows form sono ospitati in una cartella Excel o in un documento di Word:

- Non è possibile premere TAB da un controllo a un altro.

- I controlli di un documento vengono disabilitati quando si modifica l'impostazione dello zoom del documento su un valore diverso dal 100%.

  Per informazioni sulle limitazioni dei controlli Windows Form nei documenti, vedere Limitazioni dei controlli Windows Form Office [documenti](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Riquadri azioni e riquadri attività personalizzati
 Quando un riquadro azioni o un riquadro attività personalizzato ha lo stato attivo, si accede ai controlli nello stesso modo in cui si accede ai controlli in un'Windows Forms. Per spostare il cursore tra il riquadro azioni e il documento, è possibile premere **F6.**

 Per altre informazioni sui riquadri azioni e i riquadri attività personalizzati, vedere [Panoramica del](../vsto/actions-pane-overview.md) riquadro Azioni e [Riquadri attività personalizzati](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modalità di visualizzazione

Visual Studio presenta le limitazioni seguenti correlate alle modalità di visualizzazione:

- I controlli in un documento di Word o Excel foglio di lavoro sono disabilitati quando si modifica l'impostazione dello zoom del documento su un valore diverso dal 100%.

- La **finestra di dialogo** Project non visualizza correttamente i controlli se un utente modifica le opzioni di accessibilità del computer in **Usa** Contrasto elevato .

È possibile usare Lente di ingrandimento per superare queste limitazioni. Lente di ingrandimento è un'utilità Windows che crea una finestra separata che visualizza una parte ingrandita dello schermo.

## <a name="see-also"></a>Vedi anche

- [Sviluppare Office soluzioni](../vsto/developing-office-solutions.md)
- [Controlli sui Office di lavoro](../vsto/controls-on-office-documents.md)
- [Accessibilità per le persone con disabilità](../ide/reference/accessibility-features-of-visual-studio.md)
- [Funzionalità di accessibilità di Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)