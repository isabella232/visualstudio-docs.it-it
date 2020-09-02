---
title: Accessibilità nei progetti di Office
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8bd74f4d61c74a4dc348f7a615e103b283a15fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189629"
---
# <a name="accessibility-in-office-projects"></a>Accessibilità nei progetti di Office

Microsoft Visual Studio e Microsoft Office includono molte funzionalità di accessibilità che consentono di compilare soluzioni personalizzate che soddisfano i requisiti di accessibilità standard. Microsoft pubblica le linee guida per l'accessibilità sul Web. Per informazioni dettagliate, vedere il [sito Web di accessibilità](https://www.microsoft.com/accessibility/).

Nella maggior parte dei casi, i progetti di Office in Visual Studio soddisfano gli standard di accessibilità o espongono proprietà che è possibile impostare per rendere accessibili le soluzioni. Tuttavia, esistono alcune funzionalità con accessibilità limitata.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Accessibilità in fase di progettazione

### <a name="use-shortcut-keys-in-document-level-projects"></a>Usare i tasti di scelta rapida nei progetti a livello di documento
 Quando un documento di Word Microsoft Office o una cartella di lavoro di Excel Microsoft Office è aperto in Visual Studio, solo un'applicazione alla volta riceve i comandi del tasto di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile visualizzarli in Word o Excel quando lo stato attivo del documento è selezionando lo **schema della tastiera dinamico** nella pagina **Impostazioni tastiera** della finestra di dialogo **Opzioni** . Per ulteriori informazioni, vedere [Microsoft Office tastiera Word, Microsoft Office impostazioni della tastiera, finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) e [Microsoft Office tastiera di Excel, Microsoft Office impostazioni della tastiera, finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Visualizzare i tasti di scelta rapida per la barra multifunzione nei progetti a livello di documento
 Quando un documento di Word o una cartella di lavoro di Excel è aperta in Visual Studio, non è possibile premere il tasto **ALT** per visualizzare i tasti di scelta rapida per le schede e i controlli sulla barra multifunzione. Per visualizzare i tasti di scelta rapida mentre il documento o la cartella di lavoro è aperta nella finestra di progettazione, seguire questa procedura.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Per visualizzare i tasti di scelta rapida per schede e controlli della barra multifunzione nella finestra di progettazione

1. In Visual Studio scegliere **Opzioni**dal menu **strumenti** .

2. Espandere il nodo **strumenti di Office** e selezionare **Microsoft Office tastiera di Excel** o la **tastiera Microsoft Office Word**, a seconda dei casi.

3. Selezionare lo **schema della tastiera dinamica**.

     Viene visualizzato un messaggio che indica che è necessario riavviare Visual Studio per rendere effettive le modifiche.

4. Fare clic su **OK**.

5. Riavviare Visual Studio e riaprire il progetto.

6. Aprire la finestra di progettazione del documento o della cartella di lavoro per il progetto.

7. Premere **F6** per visualizzare i tasti di scelta rapida per la barra multifunzione.

## <a name="accessibility-at-run-time"></a>Accessibilità in fase di esecuzione

### <a name="windows-forms-controls-on-office-documents"></a>Windows Forms controlli nei documenti di Office
 I controlli Windows Forms espongono le proprietà di accessibilità per fornire informazioni sul controllo agli strumenti di accessibilità, ad esempio utilità per la lettura dello schermo. È possibile sfruttare queste proprietà di accessibilità quando i controlli si trovano in un documento di Office in una personalizzazione a livello di documento. Per ulteriori informazioni, vedere [fornire informazioni sull'accessibilità per i controlli in un Windows Form](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Tuttavia, in fase di esecuzione sono presenti alcune limitazioni di accessibilità quando Windows Forms controlli sono ospitati in una cartella di lavoro di Excel o in un documento di Word:

- Non è possibile tabulare da un controllo a un altro.

- I controlli di un documento sono disabilitati quando si modifica l'impostazione di zoom del documento su un valore diverso da 100%.

  Per informazioni sulle limitazioni dei controlli Windows Forms sui documenti, vedere [limitazioni dei controlli Windows Forms nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Riquadri azioni e riquadri attività personalizzati
 Quando un riquadro azioni o un riquadro attività personalizzato dispone dello stato attivo, è possibile accedere ai controlli nello stesso modo in cui si accede ai controlli in una Windows Forms Application. Per spostare il cursore tra il riquadro azioni e il documento, è possibile premere **F6**.

 Per ulteriori informazioni sui riquadri azioni e sui riquadri attività personalizzati, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md) e [riquadri attività personalizzati](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modalità di visualizzazione

Visual Studio presenta le limitazioni seguenti relative alle modalità di visualizzazione:

- I controlli in un documento di Word o in un foglio di lavoro di Excel vengono disabilitati quando si modifica l'impostazione di zoom del documento su un valore diverso dal 100%.

- La finestra di dialogo **nuovo progetto** non visualizza correttamente i controlli se un utente modifica le opzioni di accessibilità del computer per **utilizzare contrasto elevato**.

È possibile utilizzare la lente di ingrandimento per superare queste limitazioni. Magnifier è un'utilità di visualizzazione in Windows che consente di creare una finestra separata in cui viene visualizzata una parte ingrandita dello schermo.

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Accessibilità per utenti con particolari esigenze](../ide/reference/accessibility-features-of-visual-studio.md)
- [Funzionalità di accessibilità di Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)