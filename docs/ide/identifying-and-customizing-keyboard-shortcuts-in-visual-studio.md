---
description: È possibile identificare i tasti di scelta rapida per i comandi di Visual Studio, personalizzarli ed esportarli per consentirne l'utilizzo ad altri utenti.
title: Identificare e personalizzare i tasti di scelta rapida
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VS.ToolsOptionsPages.Environment.Keyboard
helpviewer_keywords:
- keyboard shortcuts [Visual Studio], customizing
- importing shortcut keys [Visual Studio]
- shortcut key combinations [Visual Studio]
- commands [Visual Studio], shortcut keys
- custom shortcut keys [Visual Studio]
- customizing keyboard shortcuts [Visual Studio]
- exporting shortcut keys [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: a1a3aa2ace6279211c27847b8b9cc46d71b0d9ad
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038603"
---
# <a name="identify-and-customize-keyboard-shortcuts-in-visual-studio"></a>Identificare e personalizzare i tasti di scelta rapida in Visual Studio

È possibile identificare i tasti di scelta rapida per i comandi di Visual Studio, personalizzarli ed esportarli per consentirne l'utilizzo ad altri utenti. Molti tasti di scelta rapida richiamano sempre gli stessi comandi, ma il comportamento di un tasto può variare in base alle condizioni indicate di seguito.

- Impostazioni di ambiente predefinite scelte la prima volta che è stato aperto Visual Studio, ad esempio Impostazioni generali per lo sviluppo o Visual C#. Per informazioni sulla modifica o la reimpostazione delle impostazioni, vedere [Impostazioni dell'ambiente](environment-settings.md).

- Se è stato personalizzato il comportamento del tasto di scelta rapida.

- Contesto attivo quando si seleziona il tasto di scelta rapida. Ad esempio, il tasto di scelta rapida **F2** richiama il comando `Edit.EditCell` se si usa **Progettazione impostazioni**, mentre richiama il comando `File.Rename` se si usa **Team Explorer**.

Indipendentemente dalle impostazioni, dalla personalizzazione e dal contesto, è possibile trovare e modificare un tasto di scelta rapida nella finestra di dialogo **Opzioni**. È anche possibile cercare i tasti di scelta rapida predefiniti per diverse decine di comandi in [Tasti di scelta rapida più comuni](../ide/default-keyboard-shortcuts-in-visual-studio.md#most-popular-keyboard-shortcuts). Per un elenco completo di tutti i tasti di scelta rapida predefiniti (in base alle **Impostazioni generali per lo sviluppo**), vedere [Tutti i tasti di scelta rapida](../ide/default-keyboard-shortcuts-in-visual-studio.md).

Se un tasto di scelta rapida viene assegnato a un comando nel contesto *Globale* e in nessun altro contesto, richiamerà sempre il comando in questione. Un tasto di scelta rapida può tuttavia essere assegnato a un comando nel contesto globale e a un altro in un contesto specifico. Se si utilizza tale tasto di scelta rapida nel contesto specifico, richiama il comando per il contesto specifico, non il contesto globale.

> [!NOTE]
> In base alle impostazioni e all'edizione di Visual Studio, i nomi e le pozioni dei comandi dei menu e le opzioni visualizzate nelle finestre di dialogo possono variare. Questa pagina è basata sul profilo **Impostazioni generali per lo sviluppo**.

## <a name="identify-a-keyboard-shortcut"></a>Identificare un tasto di scelta rapida

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

2. Espandere **Ambiente**, quindi scegliere **Tastiera**.

   ![Visualizzare i tasti di scelta rapida nella finestra di dialogo Opzioni](../ide/media/optionskeyboard.png)

3. Nella casella **Mostra comandi contenenti** immettere il nome del comando intero o parziale, senza spazi.

   Sono ad esempio disponibili comandi per `solutionexplorer`.

4. Scegliere il comando corretto nell'elenco.

    Ad esempio, è possibile scegliere `View.SolutionExplorer`.

5. Se al comando è associato un tasto di scelta rapida, verrà visualizzato nell'elenco **Tasti di scelta rapida per comando selezionato**.

   ![Visualizzare un collegamento per un comando specifico](../ide/media/viewshortcut.png)

## <a name="customize-a-keyboard-shortcut"></a>Personalizzare un tasto di scelta rapida

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

2. Espandere **Ambiente**, quindi scegliere **Tastiera**.

3. Facoltativo: filtrare l'elenco di comandi immettendo il nome del comando in tutto o in parte, senza spazi, nella casella **Mostra comandi contenenti**.

4. Nell'elenco scegliere il comando a cui si desidera assegnare un tasto di scelta rapida.

   Nell'elenco **Usa nuova combinazione in** scegliere l'area di funzionalità in cui verrà usato il tasto di scelta rapida.

   Ad esempio, scegliere **Globale** se il tasto di scelta rapida deve funzionare in tutti i contesti. È possibile utilizzare qualsiasi tasto di scelta rapida non mappato come globale in un altro editor. In caso contrario, la specifica dell'editor avrà la precedenza.

   > [!NOTE]
   > Non è possibile assegnare i tasti seguenti nei tasti di scelta rapida in **Globale**:
   >
   > - INVIO, TAB, BLOC MAIUSC
   > - STAMP/R SIST, BLOC SCORR, PAUSA/INTERR
   > - INS, HOME, FINE, PGSU, PGGIÙ
   > - tasto WINDOWS, tasto MENU SCELTA RAPIDA, tasti di direzione
   > - BLOC NUM, CANC o CANC sul tastierino numerico
   > - combinazione di tasti CTRL+ALT+CANC

6. Nella casella **Premi tasti di scelta rapida** immettere il tasto di scelta rapida che si vuole usare.

    > [!NOTE]
    > È possibile creare un collegamento che combina una lettera con **alt,** **CTRL** o entrambi. È anche possibile creare un collegamento che combina il **tasto** MAIUSC e una lettera con **alt,** **CTRL** o entrambi.

     Se un tasto di scelta rapida è già assegnato a un altro comando, verrà visualizzato nella casella **Combinazione già utilizzata da**. In tal caso, scegliere **il tasto Backspace** per eliminare il collegamento prima di provarne uno diverso.

    ![Specificare un collegamento diverso per un comando](../ide/media/reassignshortcut.png)

7. Scegliere il pulsante **Assegna**.

    > [!NOTE]
    > Se si specifica un tasto di scelta rapido differente per un comando, fare clic su **Assegna** e quindi su **Annulla** per chiudere la finestra di dialogo. Il tasto di scelta rapida assegnato non viene ripristinato.

## <a name="share-custom-keyboard-shortcuts"></a>Condividere i tasti di scelta rapida personalizzati

È possibile condividere i tasti di scelta rapida personalizzati esportandoli in un file e quindi fornendo il file ad altri utenti in modo che possano importare i dati.

### <a name="to-export-only-keyboard-shortcuts"></a>Per esportare solo i tasti di scelta rapida

1. Sulla barra dei menu scegliere **Strumenti**  >  **Importa ed esporta impostazioni**.

2. Scegliere **Esporta le impostazioni di ambiente selezionate** e quindi scegliere **Avanti**.

3. In **Quali impostazioni si desidera esportare?** deselezionare la casella di controllo **Tutte le impostazioni**, espandere **Opzioni** e quindi **Ambiente**.

4. Selezionare la casella di controllo **Tastiera** e quindi scegliere **Avanti**.

   ![Esportare solo i tasti di scelta rapida personalizzati](../ide/media/exportshortcuts.png)

5. Nelle caselle **Assegnare un nome al file di impostazioni** e **Archivia il file di impostazioni in questa directory** lasciare i valori predefiniti o specificare valori diversi e quindi scegliere **Fine**.

::: moniker range="vs-2017"

Per impostazione predefinita, i tasti di scelta rapida vengono salvati in un file nella cartella *%USERPROFILE%\Documents\Visual Studio 2017\Settings*. Il nome del file riflette la data di esportazione delle impostazioni e l'estensione *è vssettings*.

::: moniker-end

::: moniker range=">=vs-2019"

Per impostazione predefinita, i tasti di scelta rapida vengono salvati in un file nella cartella *%USERPROFILE%\Documenti\Visual Studio 2019\Settings*. Il nome del file riflette la data di esportazione delle impostazioni e l'estensione *è vssettings*.

::: moniker-end

### <a name="to-import-only-keyboard-shortcuts"></a>Per importare solo i tasti di scelta rapida

1. Sulla barra dei menu scegliere **Strumenti**  >  **Importa ed esporta impostazioni**.

2. Selezionare il pulsante di opzione **Importa le impostazioni di ambiente selezionate** e quindi fare clic su **Avanti**.

3. Selezionare il pulsante di opzione **No, importa soltanto le nuove impostazioni, sovrascrivendo le impostazioni correnti** e quindi scegliere **Avanti**.

4. In **Impostazioni personali** scegliere il file contenente i tasti di scelta rapida da importare o scegliere il pulsante **Sfoglia** per individuare il file corretto.

5. Scegliere **Avanti**.

6. In **Quali impostazioni si desidera importare?** deselezionare la casella di controllo **Tutte le impostazioni**, espandere **Opzioni**, quindi **Ambiente**.

7. Selezionare la casella di controllo **Tastiera** e quindi scegliere **Fine**.

   ![Importare solo i tasti di scelta rapida personalizzati](../ide/media/importshortcuts.png)

## <a name="see-also"></a>Vedere anche

- [Funzionalità di accessibilità di Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)
