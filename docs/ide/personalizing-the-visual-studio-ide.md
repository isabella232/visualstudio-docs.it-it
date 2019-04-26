---
title: Personalizzare l'IDE
ms.date: 11/20/2017
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 62f2d98777f1fe87b67bdb28e6302f29f752f27f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62953296"
---
# <a name="personalize-the-visual-studio-ide"></a>Personalizzare l'IDE di Visual Studio

È possibile personalizzare Visual Studio in vari modi per supportare in modo ottimale stili e requisiti specifici per lo sviluppo. Molte impostazioni consentono di effettuare il roaming tra più istanze di Visual Studio&mdash;vedere [Impostazioni sincronizzate](../ide/synchronized-settings-in-visual-studio.md). Questo articolo descrive brevemente alcune personalizzazioni e indica dove è possibile trovare altre informazioni.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Personalizzare l'IDE di Visual Studio per Mac](/visualstudio/mac/customizing-the-ide).

## <a name="default-settings"></a>Impostazioni predefinite

È possibile scegliere una raccolta predefinita di impostazioni che consenta di ottimizzare Visual Studio per il tipo di sviluppo che si svolge abitualmente. Per altre informazioni, vedere [Impostazioni dell'ambiente](environment-settings.md).

## <a name="general-environment-options"></a>Opzioni generali dell'ambiente

Molte opzioni di personalizzazione sono esposte tramite la finestra di dialogo [Opzioni ambiente](../ide/reference/environment-options-dialog-box.md). È possibile accedere a questa finestra di dialogo in due modi:

- Sulla barra dei menu scegliere **Strumenti** > **Opzioni**e, se non è già stato fatto, espandere il nodo **Ambiente**.

- Premere **CTRL**+**Q**, digitare **ambiente** nella casella di ricerca e quindi scegliere **Ambiente--> Generale** nei risultati.

> [!TIP]
> Quando viene visualizzata la finestra di dialogo Opzioni, è possibile premere **F1** per le informazioni della Guida sulle diverse impostazioni nella pagina.

## <a name="environment-color-themes"></a>Temi colore dell'ambiente

Per modificare il tema colori tra chiaro, scuro e blu, digitare **ambiente** nella casella di ricerca e quindi scegliere **Ambiente--> Generale**. Nella finestra di dialogo **Opzioni** modificare l'opzione **Tema colori**.

Per modificare le opzioni di colorazione nell'editor, digitare **ambiente** nella casella di ricerca e quindi scegliere **Ambiente --> Tipi di carattere e colori**. Vedere [How to: Modificare tipi di carattere e colori](../ide/how-to-change-fonts-and-colors-in-visual-studio.md).

### <a name="main-menu-casing"></a>Utilizzo di maiuscole e minuscole nel menu principale

È possibile modificare la combinazione di maiuscole e minuscole per il menu principale scegliendo tra le opzioni **Tutte Iniziali Maiuscole** ("File") e **Tutto maiuscole** ("FILE"). Digitare **ambiente** nella casella di ricerca, selezionare **Ambiente > Generale** e quindi modificare l'opzione **Applica lo stile Tutte Iniziali Maiuscole alla barra dei menu**.

### <a name="customize-menus-and-toolbars"></a>Personalizzare menu e barre degli strumenti

Per aggiungere o rimuovere voci di menu o elementi della barra degli strumenti, vedere [Procedura: Personalizzare menu e barre degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

::: moniker range="vs-2017"

## <a name="start-page"></a>Pagina iniziale

Per creare una pagina iniziale personalizzata per l'utente e il team, vedere [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).

::: moniker-end

## <a name="window-layouts"></a>Layout delle finestre

È possibile definire e salvare più layout di finestra e passare da un layout all'altro. Ad esempio, è possibile definire un layout per la scrittura del codice e uno per il debug. Per definire le posizioni e il comportamento delle finestre e salvare i layout personalizzati, vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="external-tools"></a>Strumenti esterni

È possibile personalizzare il menu **Strumenti** per avviare gli strumenti esterni. Per altre informazioni, vedere [Gestire gli strumenti esterni](../ide/managing-external-tools.md).

## <a name="see-also"></a>Vedere anche

- [Impostazioni dell'ambiente](environment-settings.md)
- [Panoramica dell'IDE di Visual Studio](../get-started/visual-studio-ide.md)
- [Avvio rapido: Presentazione dell'IDE di Visual Studio](../ide/quickstart-ide-orientation.md)
- [Personalizzare l'IDE di Visual Studio per Mac](/visualstudio/mac/customizing-the-ide)