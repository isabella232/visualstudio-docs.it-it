---
title: Opzioni di stile di codice e pulizia del codice
description: Informazioni su come configurare Visual Studio per applicare le preferenze di stile del codice usando i comandi di pulizia del codice (Visual Studio 2019) e Format Document (Visual Studio 2017).
ms.custom: SEO-VS-2020
ms.date: 04/25/2019
ms.topic: conceptual
author: mikejo5000
ms.author: mikejo
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 9172fff2dde1528c5ea382aea996d316e0738ea0
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189745"
---
# <a name="code-style-preferences"></a>Preferenze di stile per il codice

È possibile definire le impostazioni per lo stile di codice a livello di singolo progetto usando un [file EditorConfig](#code-styles-in-editorconfig-files) oppure per tutto il codice modificato in Visual Studio nella pagina [**Opzioni**](#code-styles-in-the-options-dialog-box) dell'editor di testo. Per il codice C#, è anche possibile configurare Visual Studio in modo da applicare queste preferenze di stile di codice usando i comandi **Pulizia del codice** (Visual Studio 2019) e **Formatta documento** (Visual Studio 2017).

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Comportamento dell'editor in Visual Studio per Mac](/visualstudio/mac/editor-behavior).

## <a name="code-styles-in-editorconfig-files"></a>Stili di codice nei file EditorConfig

È possibile specificare le [impostazioni relative agli stili di codice](/dotnet/fundamentals/code-analysis/code-style-rule-options) per .NET mediante l'aggiunta di un file [EditorConfig](create-portable-custom-editor-options.md) al progetto. I file EditorConfig sono associati a una codebase anziché a un account di personalizzazione di Visual Studio. Le impostazioni in un file EditorConfig hanno la precedenza sugli stili di codice specificati nella finestra di dialogo **Opzioni**. Usare un file EditorConfig quando si vogliono imporre stili di codice per tutti i collaboratori del repository o del progetto.

::: moniker range=">=vs-2019"

È possibile popolare manualmente il file EditorConfig oppure generarlo automaticamente in base alle impostazioni per gli stili del codice specificate nella finestra di dialogo **Opzioni** di Visual Studio. Questa pagina di opzioni è disponibile in **strumenti**  >  **Opzioni**  >  **editor di testo** > [**C#** o **Basic**] > **stile di codice**  >  **generale**. Fare clic su **Genera file con estensione editorconfig dalle impostazioni** per generare automaticamente un file con estensione *editorconfig* per lo stile di codifica in base alle impostazioni in questa pagina **Opzioni**.

![Generare un file con estensione editorconfig dalle impostazioni in Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

## <a name="code-styles-in-the-options-dialog-box"></a>Stili di codice nella finestra di dialogo Opzioni

Per impostare le preferenze di stile per il codice per tutti i progetti C# e Visual Basic, aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** selezionare **Editor di testo** > [**C#** oppure **Basic**] > **Stile codice** > **Generale**.

Quando viene selezionata, ogni voce dell'elenco visualizza un'anteprima della preferenza:

::: moniker range="vs-2017"

![Opzioni di stile di codice](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opzioni di stile di codice](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Le opzioni impostate in questa finestra sono applicabili all'account di personalizzazione di Visual Studio e non vengono associate a un progetto o una codebase in particolare. Inoltre, non vengono applicate in fase di compilazione, neanche nelle compilazioni con di integrazione continua (CI). Se si vogliono associare le preferenze di stile per il codice al progetto e fare in modo che gli stili vengano applicati durante la compilazione, specificare le preferenze in un [file con estensione editorconfig](#code-styles-in-editorconfig-files) associato al progetto.

### <a name="preference-and-severity"></a>Preferenza e gravità

Per ogni impostazione di stile del codice in questa pagina è possibile impostare i valori **Preferenza** e **Gravità** usando i menu a discesa disponibili per ogni riga. La gravità può essere impostata su **Solo refactoring**, **Suggerimento**, **Avviso** o **Errore**. Se si vogliono abilitare le [Azioni rapide](../ide/quick-actions.md) per uno stile di codice, assicurarsi che l'opzione **Gravità** sia impostata su un valore diverso da **Solo refactoring**. La lampadina **azioni rapide** :::image type="icon" source="media/light-bulb-dropdown.png"::: , la lampadina di errore o l'icona del :::image type="icon" source="media/error-bulb.png"::: cacciavite :::image type="icon" source="media/screwdriver.png"::: viene visualizzata quando viene usato uno stile non preferito ed è possibile scegliere un'opzione nell'elenco **azioni rapide** per riscrivere automaticamente il codice nello stile preferito.

::: moniker range=">=vs-2019"

## <a name="enforce-code-styles-on-build"></a>Applicare stili di codice alla compilazione

A partire da Visual Studio 2019 versione 16,8, che include .NET 5,0 RC2 SDK, è possibile [applicare le convenzioni di codifica .NET sulla compilazione](/dotnet/fundamentals/productivity/code-analysis#code-style-analysis) per tutti i progetti .NET. In fase di compilazione, le violazioni di stile del codice .NET verranno visualizzate come avvisi o errori con un prefisso "IDE". In questo modo è possibile applicare rigorosamente stili di codice coerenti nella codebase.

::: moniker-end

## <a name="apply-code-styles"></a>Applicare stili di codice

::: moniker range="vs-2017"

È possibile configurare il comando **Formatta documento** (**Modifica** > **Avanzate** > **Formatta documento**) in modo da applicare le impostazioni per gli stili di codice (da un file EditorConfig o con le opzioni **Stile codice**) insieme alla normale formattazione, ad esempio i rientri. Se è presente un file con estensione *editorconfig* per il progetto, queste impostazioni hanno la precedenza.

> [!NOTE]
> L'applicazione degli stili di codice tramite il comando **Formatta documento** è disponibile solo per i file di codice C#. Si tratta di una funzionalità sperimentale.

Configurare le impostazioni da applicare con **Formatta documento** nella [pagina delle opzioni Formattazione](reference/options-text-editor-csharp-formatting.md#format-document-settings).

![Impostazioni degli stili di codice per Formatta documento in Visual Studio 2017](media/format-document-settings-experiment.png)

> [!TIP]
> Le regole configurate con una gravità di **nessuno** non partecipano alla pulizia del codice, ma possono essere applicate singolarmente tramite il menu **azioni rapide e refactoring** .

La prima volta che si attiva il comando **Formatta documento**, una barra informazioni gialla richiede all'utente di configurare le impostazioni di pulizia del codice.

::: moniker-end

::: moniker range=">=vs-2019"

Per i file di codice C#, Visual Studio 2019 contiene un pulsante di **pulizia del codice** nella parte inferiore dell'editor (tastiera: **CTRL** + **K**, **CTRL** + **E**) per applicare stili di codice da un file EditorConfig o dalla pagina Opzioni di **stile del codice** . Se è presente un file con estensione *editorconfig* per il progetto, queste impostazioni hanno la precedenza.

![Eseguire la pulizia del codice in Visual Studio 2019](media/execute-code-cleanup.png)

> [!TIP]
> Le regole configurate con una gravità di **nessuno** non partecipano alla pulizia del codice, ma possono essere applicate singolarmente tramite il menu **azioni rapide e refactoring** .

Configurare innanzitutto gli stili di codice da applicare (in uno dei due profili) nella finestra di dialogo **Configura Pulizia del codice**. Per aprire questa finestra di dialogo, fare clic sulla freccia di espansione accanto all'icona a forma di scopa di Pulizia del codice e quindi scegliere **Configura Pulizia del codice**.

![Configurare Pulizia del codice in Visual Studio 2019](media/configure-code-cleanup.png)

Dopo aver configurato la pulizia del codice, è possibile fare clic sull'icona a forma di scopa oppure premere **CTRL** + **K**, **CTRL** + **E** per eseguire la pulizia del codice. È anche possibile eseguire la pulizia del codice per l'intero progetto o soluzione. Fare clic con il pulsante destro del mouse sul nome del progetto o della soluzione in **Esplora soluzioni**, selezionare **Analizza ed esegui pulizia del codice** e quindi selezionare **Esegui pulizia del codice**.

![Eseguire Pulizia del codice per l'intero progetto o soluzione](media/run-code-cleanup-project-solution.png)

Se si vogliono applicare le impostazioni per gli stili di codice ogni volta che si salva un file, è disponibile l'estensione [Code Cleanup on Save](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.CodeCleanupOnSave).

::: moniker-end

## <a name="see-also"></a>Vedere anche

- [Azioni rapide](../ide/quick-actions.md)
- [Impostazioni della convenzione di codifica .NET per EditorConfig](/dotnet/fundamentals/code-analysis/code-style-rule-options)
- [Comportamento dell'editor (Visual Studio per Mac)](/visualstudio/mac/editor-behavior)
