---
title: Accessibilità nei progetti di Office
ms.date: 02/02/2017
ms.prod: visual-studio-dev15
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
ms.openlocfilehash: 99deac9a1a6587d345d288123029a5e3dde4308b
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54865853"
---
# <a name="accessibility-in-office-projects"></a>Accessibilità nei progetti di Office

Microsoft Visual Studio e Microsoft Office include molte funzionalità di accessibilità che consentono di creare soluzioni personalizzate che soddisfano i requisiti di accessibilità standard. Microsoft pubblica le linee guida per l'accesso facilitato sul Web. Per informazioni dettagliate, vedere la [sito Web di accessibilità](http://go.microsoft.com/fwlink/?LinkID=37113).

Nella maggior parte dei casi, i progetti di Office in Visual Studio riunisce accessibilità standard o espone proprietà che è possibile impostare per rendere accessibili le soluzioni. Esistono tuttavia alcune funzionalità che non dispongono di accessibilità.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Accessibilità in fase di progettazione

### <a name="use-shortcut-keys-in-document-level-projects"></a>Usare i tasti di scelta rapida in progetti a livello di documento
 Quando un documento di Microsoft Office Word o una cartella di lavoro di Microsoft Office Excel è aperto in Visual Studio, solo un'applicazione in un momento riceve i comandi dei tasti di scelta rapida. Per impostazione predefinita, Visual Studio riceve tutti i comandi dei tasti di scelta rapida, ma è possibile apportare Word o Excel riceverli quando il documento dispone dello stato attivo selezionando **schema della tastiera dinamico** nel **le impostazioni della tastiera** pagina del **opzioni** nella finestra di dialogo. Per altre informazioni, vedere [tastiera di Microsoft Office Word, impostazioni tastiera Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) e [tastiera di Microsoft Office Excel, impostazioni tastiera Microsoft Office, finestra di dialogo Opzioni](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Visualizzare i tasti di scelta rapida per la barra multifunzione nei progetti a livello di documento
 Quando un documento di Word o una cartella di lavoro di Excel è aperto in Visual Studio, non è possibile premere il **Alt** tasto per visualizzare i tasti di scelta rapida per le schede e controlli della barra multifunzione. Per visualizzare i tasti di scelta rapida quando il documento o la cartella di lavoro è aperto nella finestra di progettazione, eseguire la procedura seguente.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Per visualizzare i tasti di scelta rapida per le schede della barra multifunzione e i controlli nella finestra di progettazione

1.  In Visual Studio, nel **Tools** menu, fare clic su **opzioni**.

2.  Espandere la **gli strumenti di Office** nodo e selezionare **tastiera di Microsoft Office Excel** oppure **tastiera di Microsoft Office Word**, nel modo appropriato.

3.  Selezionare **schema della tastiera dinamico**.

     Viene visualizzato un messaggio che informa che è necessario riavviare Visual Studio per la modifica diventi effettiva.

4.  Fare clic su **OK**.

5.  Riavviare Visual Studio e riaprire il progetto.

6.  Aprire la finestra di documento o cartella di lavoro di progettazione per il progetto.

7.  Premere **F6** per visualizzare i tasti di scelta rapida per la barra multifunzione.

## <a name="accessibility-at-runtime"></a>Accessibilità in fase di esecuzione

### <a name="windows-forms-controls-on-office-documents"></a>Controlli Windows Form nei documenti di Office
 Controlli Windows Form espongono proprietà di accessibilità per fornire informazioni sul controllo per gli strumenti di accessibilità, quali gli screen reader. È possibile sfruttare i vantaggi di queste proprietà di accessibilità quando i controlli si trovano in un documento di Office in una personalizzazione a livello di documento. Per altre informazioni, vedere [forniscono informazioni sull'accessibilità per i controlli in un Form Windows](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Tuttavia, esistono alcune limitazioni di accessibilità in fase di esecuzione quando i controlli Windows Form sono ospitati in una cartella di lavoro di Excel o un documento di Word:

- È possibile scheda da un controllo a un'altra.

- Controlli in un documento sono disabilitati quando si modifica l'impostazione dello zoom del documento su un valore qualsiasi diverso da 100%.

  Per informazioni sulle limitazioni dei controlli Windows Form nei documenti, vedere [consente di controllare le limitazioni di Windows Form nei documenti di Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Riquadri azioni e riquadri attività personalizzati
 Quando un riquadro attività personalizzato o un riquadro azioni ha lo stato attivo, si controlli di accesso allo stesso modo è possibile accedere a controlli in un'applicazione Windows Form. Per spostare il cursore tra il riquadro azioni e il documento, è possibile premere **F6**.

 Per altre informazioni sui riquadri azioni e riquadri attività personalizzati, vedere [Cenni preliminari sul riquadro azioni](../vsto/actions-pane-overview.md) e [riquadri attività personalizzati](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modalità di visualizzazione

Visual Studio presenta le limitazioni seguenti relative alle modalità di visualizzazione:

- I controlli in un documento di Word o un foglio di lavoro di Excel sono disabilitati quando si modifica l'impostazione dello zoom del documento su un valore qualsiasi diverso da 100%.

- Il **nuovo progetto** finestra di dialogo controlli vengono visualizzati correttamente se un utente modifica le opzioni di accessibilità del computer per **Usa Contrasto elevato**.

È possibile utilizzare la lente di ingrandimento per superare queste limitazioni. Lente di ingrandimento è un'utilità di Windows che consente di creare una finestra separata che consente di visualizzare un'area ingrandita della schermata.

## <a name="see-also"></a>Vedere anche

- [Sviluppare soluzioni Office](../vsto/developing-office-solutions.md)
- [Controlli nei documenti di Office](../vsto/controls-on-office-documents.md)
- [Accessibilità per persone affette da disabilità](../ide/reference/accessibility-for-people-with-disabilities.md)
- [Funzionalità di accessibilità di Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)