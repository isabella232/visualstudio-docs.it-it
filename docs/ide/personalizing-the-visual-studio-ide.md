---
title: Personalizzazione di IDE di Visual Studio
ms.date: 11/20/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8d2e42c31d7cbdb52e602eee4e424eb78ee89d77
ms.sourcegitcommit: bc43970c000f07c9cc2051f1264a9742943a9755
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2018
ms.locfileid: "51348696"
---
# <a name="personalize-the-visual-studio-ide"></a>Personalizzare l'IDE di Visual Studio

È possibile personalizzare Visual Studio in vari modi per supportare in modo ottimale stili e requisiti specifici per lo sviluppo. Molte impostazioni consentono di effettuare il roaming tra più istanze di Visual Studio&mdash;vedere [Impostazioni sincronizzate](../ide/synchronized-settings-in-visual-studio.md). Questo argomento descrive brevemente alcune personalizzazioni diverse e indica dove è possibile trovare altre informazioni.

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Personalizzare l'IDE di Visual Studio per Mac](/visualstudio/mac/customizing-the-ide).

## <a name="general-environment-options"></a>Opzioni generali dell'ambiente

Molte opzioni di personalizzazione sono esposte tramite la finestra di dialogo [Opzioni ambiente](../ide/reference/environment-options-dialog-box.md). È possibile accedere a questa finestra di dialogo in due modi:

- Sulla barra dei menu scegliere **Strumenti** > **Opzioni**e, se non è già stato fatto, espandere il nodo **Ambiente**.

- Digitare `environment` nella casella **Avvio veloce** e scegliere **Ambiente--> Generale** dall'elenco risultati.

   > [!TIP]
   > Quando viene visualizzata la finestra di dialogo, è possibile premere **F1** per le informazioni della Guida sulle diverse impostazioni nella pagina.

## <a name="environment-color-themes"></a>Temi colore dell'ambiente

Per modificare il tema colori tra chiaro, scuro e azzurro, digitare `environment` nella casella **Avvio veloce** e quindi scegliere **Ambiente--> Generale**. Nella finestra di dialogo **Opzioni** modificare l'opzione **Tema colori**.

Per modificare le opzioni di colorazione nell'editor, digitare `environment` nella casella **Avvio veloce** e quindi scegliere **Ambiente --> Tipi di carattere e colori**. Vedere [Procedura: Modificare i tipi di carattere e i colori](../ide/how-to-change-fonts-and-colors-in-visual-studio.md).

### <a name="main-menu-casing"></a>Utilizzo di maiuscole e minuscole nel menu principale

È possibile modificare la combinazione di maiuscole e minuscole per il menu principale scegliendo tra le opzioni **Tutte Iniziali Maiuscole** ("File") e **Tutto maiuscole** ("FILE"). Digitare `environment` nella casella **Avvio veloce** selezionare **Ambiente --> Generale** e quindi modificare l'opzione **Applica lo stile Tutte Iniziali Maiuscole alla barra dei menu**.

### <a name="customize-menus-and-toolbars"></a>Personalizzare menu e barre degli strumenti

Per aggiungere o rimuovere voci di menu o elementi della barra degli strumenti, vedere [Procedura: personalizzare menu e barre degli strumenti](../ide/how-to-customize-menus-and-toolbars-in-visual-studio.md).

## <a name="start-page"></a>Pagina iniziale

Per creare una pagina iniziale personalizzata per l'utente e il team, vedere [Personalizzare la pagina iniziale](../ide/customizing-the-start-page-for-visual-studio.md).

## <a name="window-layouts"></a>Layout delle finestre

È possibile definire e salvare più layout di finestra e passare da un layout all'altro. Ad esempio, è possibile definire un layout per la scrittura del codice e uno per il debug. Per definire le posizioni e il comportamento delle finestre e salvare i layout personalizzati, vedere [Personalizzare il layout delle finestre in Visual Studio](../ide/customizing-window-layouts-in-visual-studio.md).

## <a name="external-tools"></a>Strumenti esterni

È possibile personalizzare il menu **Strumenti** per avviare gli strumenti esterni. Per altre informazioni, vedere [Gestire gli strumenti esterni](../ide/managing-external-tools.md).

## <a name="see-also"></a>Vedere anche

- [Panoramica dell'IDE di Visual Studio](../ide/visual-studio-ide.md)
- [Guida introduttiva: Presentazione dell'IDE di Visual Studio](../ide/quickstart-ide-orientation.md)
- [Personalizzare l'IDE di Visual Studio per Mac](/visualstudio/mac/customizing-the-ide)