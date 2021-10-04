---
title: Modificare temi, tipi di carattere, testo e contrasto per l'accessibilità
description: Informazioni su come modificare i Visual Studio colori, i colori dei caratteri, le dimensioni del testo e i colori a contrasto aggiuntivo per semplificare l'uso e i problemi di accessibilità.
ms.date: 12/17/2020
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
ms.openlocfilehash: fc40b2200f360f42e5276f36586714e90aabf87a
ms.sourcegitcommit: 541871db9065c4fb1b21c24f980c563991b183c7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2021
ms.locfileid: "129430534"
---
# <a name="how-to-change-fonts-colors-and-themes-in-visual-studio"></a>Procedura: Modificare tipi di carattere, colori e temi in Visual Studio

È possibile modificare i tipi di carattere e i colori in Visual Studio in molti modi. Ad esempio, è possibile modificare il tema di colore blu predefinito con il tema scuro (noto anche come "modalità scura"). È anche possibile selezionare un tema a contrasto aggiuntivo se più adatto alle proprie esigenze. È anche possibile modificare il tipo di carattere e le dimensioni predefinite del testo nell'IDE e nell'editor di codice.

## <a name="change-the-color-theme"></a>Modificare il tema colori

Ecco come modificare il tema dei colori della cornice IDE e delle finestre degli strumenti in Visual Studio.

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

1. Nell'elenco delle opzioni scegliere **Ambiente**  >  **generale**.

1. Nell'elenco **Tema** colore scegliere il tema  blu predefinito,  il tema Chiaro, il tema Scuro o il tema Blu **(Contrasto** aggiuntivo). 

   ![Screenshot della finestra di dialogo Opzioni per modificare il tema dei colori](media/fonts-colors-theme.png "Screenshot della finestra di dialogo Opzioni che è possibile usare per modificare il tema dei colori")

    > [!NOTE]
    > Quando si modifica un tema a colori, il testo nell'IDE ripristina i tipi di carattere e le dimensioni predefiniti o precedentemente personalizzati per tale tema.

    :::moniker range="vs-2017"

    > [!TIP]
    > È possibile creare e modificare temi Visual Studio personalizzati installando l'Editor tema colori per Visual Studio [2017.](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor)

    :::moniker-end

    :::moniker range="vs-2019"

    > [!TIP]
    > È possibile creare e modificare i temi Visual Studio personalizzati installando Visual Studio [Color Theme Designer.](https://marketplace.visualstudio.com/items?itemName=ms-madsk.ColorThemeDesigner)

    :::moniker-end

## <a name="change-fonts-and-text-size"></a>Modificare i tipi di carattere e le dimensioni del testo

È possibile modificare il tipo di carattere e le dimensioni del testo per tutte le finestre degli strumenti e della cornice IDE o solo per determinate finestre o elementi di testo. È anche possibile modificare il tipo di carattere e le dimensioni del testo nell'editor.

### <a name="to-change-the-font-and-text-size-in-the-ide"></a>Per modificare il tipo di carattere e le dimensioni del testo nell'IDE

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

1. Nell'elenco delle opzioni scegliere **Tipi di carattere** e colori  >  **dell'ambiente**.

1. **Nell'elenco Mostra impostazioni per** scegliere **Ambiente**.

   ![Screenshot della finestra di dialogo Opzioni per modificare tipi di carattere e colori nell'IDE](media/fonts-colors-environment.png "Screenshot della finestra di dialogo Opzioni per modificare tipi di carattere e colori nell'IDE")

    > [!NOTE]
    > Se si intende modificare il tipo di carattere solo per le finestre degli strumenti, nell'elenco **Mostra impostazioni per** scegliere **Tutte le finestre degli strumenti di testo**.

1. Modificare le **opzioni Carattere** e **Dimensioni** per modificare il tipo di carattere e le dimensioni del testo per l'IDE.

1. Selezionare l'elemento appropriato in **Elementi di visualizzazione**, quindi modificare le opzioni **Primo piano elemento** e **Sfondo elemento**.

### <a name="to-change-the-font-and-text-size-in-the-editor"></a>Per modificare il tipo di carattere e le dimensioni del testo nell'editor

1. Sulla barra dei menu scegliere **Opzioni**  >  **strumenti**.

1. Nell'elenco delle opzioni scegliere **Tipi di carattere** e colori  >  **dell'ambiente**.

1. **Nell'elenco Mostra impostazioni per** selezionare Editor di **testo**.

   ![Screenshot della finestra di dialogo Opzioni per modificare tipi di carattere e colori nell'editor](media/fonts-colors-text-editor.png "Screenshot della finestra di dialogo Opzioni per modificare i tipi di carattere e i colori nell'editor")

1. Modificare le **opzioni Carattere** **e Dimensioni** per modificare il tipo di carattere e le dimensioni del testo per l'editor.

1. Selezionare l'elemento appropriato in **Elementi di visualizzazione**, quindi modificare le opzioni **Primo piano elemento** e **Sfondo elemento**.

Per altre informazioni, vedere modificare i [tipi di carattere e i colori per la pagina dell'editor.](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)

## <a name="accessibility-options"></a>Opzioni di accessibilità

Se si ha una visione bassa, sono disponibili opzioni per il tema a colori. È possibile usare un'opzione  a contrasto elevato per tutte le app e l'interfaccia utente in un computer o un'opzione di contrasto aggiuntivo solo per Visual Studio.

### <a name="use-windows-high-contrast"></a>Usare Windows contrasto elevato

Usare una delle procedure seguenti per attivare o disattivare l'Windows a contrasto elevato:

- In Windows o in qualsiasi applicazione Microsoft premere IL TASTO MAIUSC + **DI** + **SINISTRA.**

- In Windows scegliere **Avvia Impostazioni**  >    >  **Accessibilità**  >  **contrasto elevato**.

    > [!WARNING]
    > L Windows di contrasto elevato influisce su tutte le applicazioni e l'interfaccia utente del computer.

### <a name="use-visual-studio-extra-contrast"></a>Usare Visual Studio contrasto aggiuntivo

Usare le procedure seguenti per attivare o disattivare l'Visual Studio di contrasto aggiuntivo:

1. Sulla barra dei menu in Visual Studio strumenti scegliere Opzioni strumenti e quindi, nell'elenco delle  >  opzioni, scegliere **Generale**  >  **ambiente**.

1. **Nell'elenco a** discesa Tema colore scegliere il tema **Blu (contrasto aggiuntivo)** e quindi scegliere **OK.**

Per altre informazioni sulle altre opzioni Visual Studio accessibilità disponibili, vedere la pagina Funzionalità di accessibilità [di Visual Studio.](../ide/reference/accessibility-features-of-visual-studio.md)

> [!TIP]
> Se è disponibile un'opzione di accessibilità per i colori o i tipi di carattere che si  pensa possa essere utile, ma non è attualmente disponibile in Visual Studio, fare clic su Suggerisci una funzionalità nel Visual Studio [Developer Community](https://aka.ms/feedback/suggest?space=8). Per altre informazioni su questo forum e sul suo funzionamento, vedere la pagina [Suggerire una funzionalità.](../ide/suggest-a-feature.md)

## <a name="next-steps"></a>Passaggi successivi

Per altre informazioni su tutti gli elementi dell'interfaccia utente per cui è possibile modificare combinazioni di tipi di carattere e colori, vedere la pagina Tipi di carattere e [colori, Ambiente,](../ide/reference/fonts-and-colors-environment-options-dialog-box.md) finestra di dialogo Opzioni.

## <a name="see-also"></a>Vedi anche

- [Procedura: Modificare tipi di carattere e colori per l'editor in Visual Studio](../ide/reference/how-to-change-fonts-and-colors-in-the-editor.md)
- [Funzionalità dell'editor Visual Studio codice](../ide/writing-code-in-the-code-and-text-editor.md)
- [Personalizzare l Visual Studio IDE e l'editor](../ide/quickstart-personalize-the-ide.md)
