---
title: Modificare temi, tipi di carattere, testo e contrasto per l'accessibilità
description: Informazioni su come modificare i Visual Studio colori, i colori dei caratteri, le dimensioni del testo e i colori a contrasto aggiuntivo per problemi di accessibilità e facilità d'uso.
ms.date: 08/20/2020
ms.topic: how-to
ms.custom: contperf-fy21q1
helpviewer_keywords:
- Visual Studio, color themes
- color themes, Visual Studio
ms.assetid: 60d91ba1-244b-4c43-847f-60b744f1352a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 63edc199e5c6386adc9c11dc3e893c4b093f994033b2f2b4c06043b92f38c011
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121272421"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Procedura: Modificare tipi di carattere, colori e temi in Visual Studio

È possibile modificare i tipi di carattere e i colori in Visual Studio in molti modi. Ad esempio, è possibile modificare il tema colori blu predefinito con il tema scuro (noto anche come "modalità scura"). È anche possibile selezionare un tema a contrasto aggiuntivo se più adatto alle proprie esigenze. È anche possibile modificare il tipo di carattere e le dimensioni del testo predefiniti sia nell'IDE che nell'editor di codice.

## <a name="change-the-color-theme"></a>Modificare il tema colori

Ecco come modificare il tema colori della cornice dell'IDE e delle finestre degli strumenti in Visual Studio.

1. Sulla barra dei menu scegliere **Strumenti**  >  **Opzioni**.

1. Nell'elenco di opzioni scegliere **Ambiente**  >  **Generale.**

1. Nell'elenco **Tema** colori scegliere il tema  blu predefinito,  il tema Chiaro, il tema Scuro o il tema Blu **(contrasto** aggiuntivo). 

   ![Screenshot della finestra di dialogo Opzioni per modificare il tema colori](media/fonts-colors-theme.png "Screenshot della finestra di dialogo Opzioni che è possibile usare per modificare il tema colori")

    > [!NOTE]
    > Quando si modifica un tema colori, il testo nell'IDE ripristina i tipi di carattere e le dimensioni predefiniti o personalizzati in precedenza per tale tema.

    :::moniker range="vs-2017"

    > [!TIP]
    > È possibile creare e modificare temi Visual Studio personalizzati installando l'Editor tema colori [per Visual Studio 2017.](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > È possibile creare e modificare temi di Visual Studio personalizzati installando la finestra Visual Studio [Color Theme Designer](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner).

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Modificare i tipi di carattere e le dimensioni del testo

È possibile modificare il tipo di carattere e le dimensioni del testo per tutte le finestre degli strumenti e le finestre degli strumenti dell'IDE o solo per determinate finestre o elementi di testo. È anche possibile modificare il tipo di carattere e le dimensioni del testo nell'editor.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>Per modificare il tipo di carattere e le dimensioni del testo nell'IDE

1. Sulla barra dei menu scegliere **Strumenti**  >  **Opzioni**.

1. Nell'elenco di opzioni scegliere **Tipi di** carattere e  >  **colori dell'ambiente.**

1. **Nell'elenco Mostra impostazioni per** scegliere **Ambiente**.

   ![Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'IDE](media/fonts-colors-environment.png "Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'IDE")

    > [!NOTE]
    > Se si intende modificare il tipo di carattere solo per le finestre degli strumenti, nell'elenco **Mostra impostazioni per** scegliere **Tutte le finestre degli strumenti di testo**.

1. Modificare le **opzioni Carattere** **e Dimensioni** per modificare il tipo di carattere e le dimensioni del testo per l'IDE.

1. Selezionare l'elemento appropriato in **Elementi di visualizzazione**, quindi modificare le opzioni **Primo piano elemento** e **Sfondo elemento**.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Per modificare il tipo di carattere e le dimensioni del testo nell'editor

1. Sulla barra dei menu scegliere **Strumenti**  >  **Opzioni**.

1. Nell'elenco di opzioni scegliere **Tipi di** carattere e  >  **colori dell'ambiente.**

1. **Nell'elenco Mostra impostazioni per** selezionare Editor di **testo.**

   ![Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'editor](media/fonts-colors-text-editor.png "Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'editor")

1. Modificare le **opzioni Carattere** **e Dimensioni** per modificare il tipo di carattere e le dimensioni del testo per l'editor.

1. Selezionare l'elemento appropriato in **Elementi di visualizzazione**, quindi modificare le opzioni **Primo piano elemento** e **Sfondo elemento**.

Per altre informazioni, vedere la pagina [Modificare i tipi di carattere e i colori per l'editor.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="accessibility-options"></a>Opzioni di accessibilità

Se si ha problemi di vista, sono disponibili opzioni per il tema colori. È possibile usare un'opzione a contrasto elevato per *tutte* le app e l'interfaccia utente in un computer o un'opzione di contrasto aggiuntivo solo per Visual Studio app.

### <a name="use-windows-high-contrast"></a>Usare Windows contrasto elevato

Utilizzare una delle procedure seguenti per attivare o disattivare l Windows a contrasto elevato:

- In Windows o in qualsiasi applicazione Microsoft, premere ALT di sinistra MAIUSC di sinistra +  + **PrtScn.**

- In Windows scegliere **Start Impostazioni**  >    >  **Accessibilità**  >  **Contrasto elevato.**

    > [!WARNING]
    > L Windows di contrasto elevato influisce su tutte le applicazioni e l'interfaccia utente nel computer.

### <a name="use-visual-studio-extra-contrast"></a>Usare Visual Studio contrasto aggiuntivo

Usare le procedure seguenti per attivare o disattivare l Visual Studio di contrasto aggiuntivo:

1. Nella barra dei menu in Visual Studio strumenti Opzioni , quindi nell'elenco delle opzioni  >  scegliere **Generale**  >  **ambiente**.

1. **Nell'elenco a** discesa Tema colori scegliere il **tema Blu (contrasto aggiuntivo)** e quindi scegliere **OK.**

Per altre informazioni su altre opzioni Visual Studio accessibilità disponibili, vedere la pagina Funzionalità [di accessibilità Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md) accessibilità.

> [!TIP]
> Se è disponibile un'opzione di accessibilità per i colori o i tipi di carattere che si  pensa potrebbero essere utili, ma che non sono attualmente disponibili in Visual Studio, è possibile contattarci selezionando Suggerisci una funzionalità in Visual Studio [Developer Community](https://aka.ms/feedback/suggest?space=8). Per altre informazioni su questo forum e sul suo funzionamento, vedere la pagina [Suggerisci una](../ide/suggest-a-feature.md) funzionalità.

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su tutti gli elementi dell'interfaccia utente per cui è possibile modificare combinazioni di tipi di carattere e colori, vedere la pagina Tipi di carattere e [colori, Ambiente,](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) finestra di dialogo Opzioni.

## <a name="see-also"></a>Vedi anche

- [Procedura: Modificare i tipi di carattere e i colori per l'editor in Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Funzionalità dell'editor Visual Studio codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Personalizzare l'IDE Visual Studio e l'editor](../ide/quickstart-personalize-the-ide.md)
