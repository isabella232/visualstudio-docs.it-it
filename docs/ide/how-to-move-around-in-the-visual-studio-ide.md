---
title: "Procedura: Spostarsi all'interno dell'IDE"
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: bdfae0808ff5daa10f8faa621e6af293543bce66
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53060252"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>Procedura: Spostarsi all'interno dell'IDE di Visual Studio

L'ambiente di sviluppo integrato (IDE) è stato progettato per consentire all'utente di passare da una finestra a un'altra e da un file a un altro in modi differenti, in base a preferenze o requisiti di progetto. È possibile scorrere tra file aperti nell'editor oppure scorrere tra tutte le finestre degli strumenti attive nell'IDE. È anche possibile passare direttamente a qualsiasi file aperto nell'editor, indipendentemente dall'ordine di accesso. Queste funzionalità consentono di aumentare la produttività, quando si utilizza l'IDE.

> [!NOTE]
> Le opzioni disponibili nelle finestre di dialogo e i nomi e i percorsi dei comandi di menu visualizzati potrebbero non corrispondere a quelli descritti in questo articolo, a seconda dell'edizione o delle impostazioni attive. Questo articolo è stato scritto considerando le impostazioni **Generali**. Per modificare le impostazioni, ad esempio per implementare le impostazioni **Generali** o **Visual C++**, scegliere **Strumenti** > **Importa/Esporta impostazioni** e quindi scegliere **Reimposta tutte le impostazioni**.

## <a name="keyboard-shortcuts"></a>Scelte rapide da tastiera

Quasi tutti i comandi dei menu di Visual Studio dispongono di un tasto di scelta rapida. È inoltre possibile creare tasti di scelta rapida personalizzati. Per altre informazioni, vedere [Identificazione e personalizzazione dei tasti di scelta rapida](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Passare da un file all'altro nell'editor

È possibile utilizzare diversi metodi per spostarsi tra i file aperti nell'editor. È possibile spostarsi tra file in base all'ordine di apertura, utilizzare lo strumento di spostamento dell'IDE per individuare il file attualmente aperto oppure aggiungere i file preferiti a una scheda, in modo che siano sempre visibili.

I comandi Posizione precedente e Posizione successiva consentono di scorrere tra i file aperti nell'editor, in base all'ordine di apertura. Questi comandi sono analoghi ai tasti Indietro e Avanti che consentono di visualizzare la cronologia di consultazione in Microsoft Internet Explorer.

### <a name="to-move-through-open-files-in-order-of-use"></a>Per spostarsi tra i file aperti in ordine di utilizzo

-   Per attivare i documenti aperti, a partire da quello che è stato toccato per ultimo, premere **CTRL**+**-**.

-   Per attivare i documenti aperti in ordine inverso, premere **CTRL**+**MAIUSC**+**-**.

    > [!NOTE]
    > **Posizione precedente** e **Posizione successiva** sono disponibili anche nel menu **Visualizza**.

È anche possibile passare a un file specifico aperto nell'editor (indipendentemente dall'ultimo accesso) usando lo **strumento di spostamento dell'IDE**, l'elenco **File attivi** nell'editor oppure la finestra di dialogo **Windows**.

Lo **strumento di spostamento dell'IDE** funziona in modo analogo allo strumento di selezione delle applicazioni di Windows. Non è disponibile dai menu. Per accedervi, è necessario utilizzare i tasti di scelta rapida. È possibile usare uno dei due comandi per accedere allo **strumento di spostamento dell'IDE** (illustrato di seguito) e passare da un file all'altro, in base all'ordine che si preferisce.

![Esplorazione dell'IDE di Visual Studio](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` consente di passare al file utilizzato più di recente, mentre `Window.NextDocumentWindowNav` consente di spostarsi in ordine inverso. Nelle **impostazioni generali per lo sviluppo** la combinazione **MAIUSC**+**ALT**+**F7** è assegnata a `Window.PreviousDocumentWindowNav`, mentre **ALT**+**F7** è assegnata a `Window.NextDocumentWindowNav`.

> [!NOTE]
> Se la combinazione di impostazioni in uso non dispone già di tasti di scelta rapida assegnati a questo comando, è possibile assegnare un comando personalizzato tramite la pagina **Tastiera** della finestra di dialogo **Opzioni**. Per altre informazioni, vedere [Identificazione e personalizzazione dei tasti di scelta rapida](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Per passare a file specifici nell'editor

-   Premere **CTRL**+**TAB** per visualizzare lo **strumento di navigazione dell'IDE**. Tenere premuto il tasto **CTRL** e premere ripetutamente **TAB** fino a quando non si seleziona il file a cui si intende accedere.

    > [!TIP]
    > Per invertire l'ordine di spostamento nell'elenco dei **file attivi**, tenere premuto **CTRL**+**MAIUSC** e premere **TAB**.

    \- oppure -

-   Nell'angolo superiore destro dell'editor, scegliere il pulsante **File attivi** e selezionare un file dell'elenco per aprirlo.

    \- oppure -

-   Nella barra dei menu scegliere **Finestra** > **Windows**.

-   Nell'elenco selezionare il file che si vuole visualizzare e scegliere **Attiva**.

## <a name="navigate-among-tool-windows-in-the-ide"></a>Passare da una finestra degli strumenti all'altra nell'IDE

Lo **strumento di spostamento dell'IDE** consente di scorrere le finestre degli strumenti aperte nell'IDE. È possibile usare uno dei due comandi per accedere allo **strumento di spostamento dell'IDE** e passare da una finestra degli strumenti all'altra, in base all'ordine che si preferisce. `Window.PreviousToolWindowNav` consente di passare al file utilizzato più di recente, mentre `Window.NextToolWindowNav` consente di spostarsi in ordine inverso. Nelle **impostazioni generali per lo sviluppo** la combinazione **MAIUSC**+**ALT**+**F7** è assegnata a `Window.PreviousDocumentWindowNav`, mentre **ALT**+**F7** è assegnata a `Window.NextDocumentWindowNav`.

> [!NOTE]
> Se la combinazione di impostazioni in uso non dispone già di tasti di scelta rapida assegnati a questo comando, è possibile assegnare un comando personalizzato tramite la pagina **Tastiera** della finestra di dialogo **Opzioni**. Per altre informazioni, vedere [Identificazione e personalizzazione dei tasti di scelta rapida](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>Per passare a una finestra degli strumenti specifica nell'IDE

-   Premere **ALT**+**F7** per visualizzare lo **strumento di navigazione dell'IDE**. Tenere premuto il tasto **ALT** e premere ripetutamente **F7** fino a quando non si seleziona la finestra alla quale si intende accedere.

    > [!TIP]
    > Per invertire l'ordine di spostamento nell'elenco **Finestra degli strumenti attivi**, tenere premuto **MAIUSC**+**ALT** e premere **F7**.

## <a name="see-also"></a>Vedere anche

- [Personalizzazione del layout delle finestre](../ide/customizing-window-layouts-in-visual-studio.md)
- [Tasti di scelta rapida predefiniti](../ide/default-keyboard-shortcuts-in-visual-studio.md)