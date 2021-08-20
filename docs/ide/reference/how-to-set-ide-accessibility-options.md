---
title: 'Procedura: Impostare le opzioni di accessibilità IDE'
description: Informazioni su come impostare le opzioni di accessibilità di Visual Studio che semplificano l'utilizzo dell'ambiente di sviluppo integrato (IDE) per tutti gli utenti, inclusi quelli ipovedenti e con destrezza manuale limitata.
ms.date: 08/23/2019
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: how-to
helpviewer_keywords:
- accessibility [Visual Studio]
ms.assetid: ddc96c4c-0600-46c1-8267-7dce4c44ad24
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 4963066cfd2347bff219845c74522915652ef28f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122151522"
---
# <a name="how-to-set-ide-accessibility-options"></a>Procedura: Impostare le opzioni di accessibilità IDE

Visual Studio offre funzionalità che facilitano la lettura e la scrittura per gli utenti con problemi di vista e difficoltà motorie. È ad esempio possibile modificare le dimensioni e il colore del testo negli editor, modificare le dimensioni del testo e dei pulsanti sulle barre degli strumenti e modificare le impostazioni per completare una funzione o un'istruzione.

Visual Studio supporta anche i layout di tastiera Dvorak, che consentono di accedere più facilmente ai caratteri usati con maggiore frequenza. È anche possibile personalizzare i tasti di scelta rapida predefiniti disponibili in Visual Studio. Per altre informazioni, vedere [Identificazione e personalizzazione dei tasti di scelta rapida](../../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella presente Guida e possono variare a seconda delle impostazioni attive o dell'edizione. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../environment-settings.md#reset-settings).

::: moniker range="vs-2017"

> [!TIP]
> Per altre informazioni sugli aggiornamenti di accessibilità recenti, visitare il post di blog sui [miglioramenti dell'accessibilità di Visual Studio 2017 (versione 15.3)](https://devblogs.microsoft.com/visualstudio/accessibility-improvements-in-visual-studio-2017-version-15-3/).

::: moniker-end

## <a name="editors-dialogs-and-tool-windows"></a>Editor, finestre di dialogo e finestre degli strumenti

Per impostazione predefinita, le finestre di dialogo e le finestre degli strumenti in Visual Studio usano le stesse dimensioni di carattere e gli stessi colori del sistema operativo. Le impostazioni relative ai colori per il frame dell'IDE, le finestre di dialogo, le barre degli strumenti e le finestre degli strumenti si basano su una combinazione di colori: chiara o scura. È possibile modificare il tema colori corrente nella [finestra di dialogo Opzioni: Ambiente > Generale](../../ide/reference/general-environment-options-dialog-box.md).

È anche possibile visualizzare finestre popup nella visualizzazione Codice dell'editor. Queste finestre possono indicare i membri disponibili per l'oggetto corrente e i parametri necessari per completare una funzione o un'istruzione e possono essere utili se l'utente ha difficoltà di digitazione, ma interferiscono con lo stato attivo nell'editor del codice, creando problemi per alcuni utenti.

Di seguito viene descritto come disattivare le finestre popup:

1. Scegliere **Opzioni** dal menu **Strumenti**.

1. Scegliere **Editor di testo** Tutti i  >  **linguaggi**  >  **Generale**.

1. Deselezionare le caselle di controllo **Elenco membri automatico** e **Informazioni parametri**.

È possibile ridisporre le finestre nell'ambiente di sviluppo integrato (IDE, Integrated Development Environment) in base alle proprie esigenze. È possibile ancorare, rendere mobile, nascondere o nascondere automaticamente ogni finestra degli strumenti. Per altre informazioni su come modificare i layout delle finestre, vedere [Personalizzare il layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md).

### <a name="change-the-size-of-text"></a>Modificare le dimensioni del testo

È possibile modificare le impostazioni per le finestre degli strumenti basate su testo, ad esempio le finestre **Comando**, **Immediato** e **Output** usando **Strumenti** > **Opzioni** > **Ambiente** > **Tipi di carattere e colori**.

Quando si seleziona **[Tutte le finestre degli strumenti di testo]** nell'elenco a discesa **Mostra impostazioni per**, l'impostazione predefinita viene indicata come **Predefinita** negli elenchi a discesa **Primo piano elemento** e **Sfondo elemento**. Per modificare queste impostazioni, scegliere il pulsante **Personalizza**.

È anche possibile modificare le impostazioni di visualizzazione del testo nell'editor. Ecco come.

1. Scegliere **Opzioni** dal menu **Strumenti**.

1. Scegliere **Tipi di** carattere e colori  >  **dell'ambiente.**

1. Selezionare un'opzione nel menu a discesa **Mostra impostazioni per**.

    Per modificare le dimensioni dei caratteri del testo in un editor, scegliere **Editor di testo**.

    Per modificare le dimensioni dei caratteri del testo nelle finestre degli strumenti basate su testo, scegliere **[Tutte le finestre degli strumenti di testo]**.

    Per modificare le dimensioni dei caratteri del testo delle descrizioni comandi in un editor, scegliere **Descrizione comando editor**.

    Per modificare le dimensioni dei caratteri del testo degli elementi popup di completamento istruzioni, scegliere **Completamento istruzioni**.

1. In **Elementi visualizzati** selezionare **Testo normale**.

1. In **Carattere** selezionare un nuovo tipo di carattere.

1. In **Dimensioni** selezionare nuove dimensioni del carattere.

    > [!TIP]
    > Per reimpostare le dimensioni del testo per le finestre degli strumenti basate su testo e per gli editor, scegliere **Usa impostazioni predefinite**.

7. Scegliere **OK**.

### <a name="change-the-colors-that-are-used-in-the-ide"></a>Modificare i colori usati nell'ambiente IDE

È possibile modificare i colori predefiniti per il testo, gli indicatori di margine, lo spazio e gli elementi di codice nell'editor. Ecco come.

1. Scegliere **Opzioni** dal menu **Strumenti**.

1. Nella cartella **Ambiente** scegliere **Tipi di carattere e colori**.

1. In **Mostra impostazioni per** scegliere **Editor di testo**.

1. In **Elementi visualizzati** selezionare un elemento di cui si vuole modificare la visualizzazione, ad esempio **Testo normale**, **Margine indicatore**, **Spazio vuoto visibile**, **Nome attributo HTML** o **Attributo XML**.

1. Selezionare le impostazioni di visualizzazione delle opzioni seguenti: **Primo piano elemento**, **Sfondo elemento** e **Grassetto**.

1. Scegliere **OK**.

> [!TIP]
> Per usare i colori a contrasto elevato per tutte le finestre dell'applicazione nel sistema operativo, premere **ALT di** sinistra + **MAIUSC sinistro** + **PRTSCN.** Se Visual Studio è aperto, chiuderlo e riaprirlo per implementare correttamente i colori a contrasto elevato.

## <a name="toolbars"></a>Barre degli strumenti

Per migliorare l'usabilità e l'accessibilità delle barre degli strumenti, è possibile aggiungere testo ai pulsanti di queste ultime.

### <a name="to-assign-text-to-toolbar-buttons"></a>Per assegnare testo ai pulsanti delle barre degli strumenti

1. Scegliere **Personalizza** dal menu **Strumenti**.

1. Nella finestra di dialogo **Personalizza** fare clic sulla scheda **Comandi**.

1. Selezionare **Barra degli strumenti**, quindi scegliere il nome della barra degli strumenti che contiene il pulsante per il quale si vuole visualizzare testo.

1. Selezionare il comando che si vuole modificare nell'elenco.

1. Scegliere **Modifica selezione**.

1. Scegliere **Icona e testo**.

### <a name="to-modify-the-displayed-text-in-a-button"></a>Per modificare il testo visualizzato in un pulsante

1. Selezionare di nuovo **Modifica selezione**.

1. Accanto a In **nome** specificare una nuova didascalia per il pulsante selezionato.

## <a name="see-also"></a>Vedi anche

* [Funzionalità di accessibilità di Visual Studio](../../ide/reference/accessibility-features-of-visual-studio.md)
* [Accessibilità per Visual Studio per Mac](/visualstudio/mac/accessibility/)
* [Risorse per la progettazione di applicazioni accessibili](../../ide/reference/resources-for-designing-accessible-applications.md)
