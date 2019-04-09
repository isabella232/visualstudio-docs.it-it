---
title: Preferenze di stile per il codice
ms.date: 03/12/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 689bdb62d5a4bc9aea21da67e8e5e844660756d6
ms.sourcegitcommit: b14b7a938a2aba9fcce4d5e813aadf2040b0dcda
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/29/2019
ms.locfileid: "58647310"
---
# <a name="code-style-preferences"></a>Preferenze di stile per il codice

Per impostare preferenze di stile per il codice per i progetti C# e Visual Basic, aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** selezionare **Editor di testo** > [**C#** oppure **Basic**] > **Stile codice** > **Generale**.

Quando viene selezionata, ogni voce dell'elenco visualizza un'anteprima della preferenza:

::: moniker range="vs-2017"

![Opzioni di stile di codice](media/code-style-quick-actions-dialog.png)

::: moniker-end

::: moniker range=">=vs-2019"

![Opzioni di stile di codice](media/vs-2019/code-style-quick-actions-dialog.png)

::: moniker-end

Le opzioni impostate in questa finestra sono applicabili all'account di personalizzazione di Visual Studio e non vengono associate a un progetto o una codebase in particolare. Inoltre, non vengono applicate in fase di compilazione, neanche nelle compilazioni con di integrazione continua (CI). Se si vogliono associare le preferenze di stile per il codice al progetto e fare in modo che gli stili vengano applicati durante la compilazione, specificare le preferenze in un [file .editorconfig](#editorconfig-files).

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Comportamento dell'editor in Visual Studio per Mac](/visualstudio/mac/editor-behavior).

## <a name="editorconfig-files"></a>File EditorConfig

È possibile specificare le impostazioni di stile del codice per .NET anche mediante l'aggiunta di un file [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) al progetto.

::: moniker range=">=vs-2019"

Fare clic su **Generate .editorconfig file from settings** (Genera file editorconfig dalle impostazioni) per generare automaticamente un file con estensione editorconfig per lo stile di codifica in base alle opzioni impostate in questa pagina **Opzioni**.

![Generare un file con estensione editorconfig dalle impostazioni in Visual Studio 2019](media/vs-2019/generate-editorconfig-file-small.png)

::: moniker-end

I file EditorConfig sono associati a una codebase anziché a un account di personalizzazione di Visual Studio. Le impostazioni in un file EditorConfig hanno la precedenza sulle opzioni selezionate nella finestra di dialogo **Opzioni**. Usare un file EditorConfig quando si vogliono imporre stili di codice per tutti i collaboratori del repository o del progetto.

## <a name="preference-and-severity"></a>Preferenza e gravità

Per ogni impostazione di stile del codice in questa pagina è possibile impostare i valori **Preferenza** e **Gravità** usando i menu a discesa disponibili per ogni riga. La gravità può essere impostata su **Nessuno**, **Suggerimento**, **Avviso** o **Errore**. Se si vogliono abilitare le [Azioni rapide](../ide/quick-actions.md) per uno stile di codice, assicurarsi che l'opzione **Gravità** sia impostata su un valore diverso da **Nessuno**. L'icona a forma di lampadina **lampadina**, di lampadina di errore ![lampadina di errore](media/screwdriver.png) o di cacciavite **cacciavite** di ![Azioni rapide](media/light-bulb-dropdown.png) viene visualizzata quando si usa uno stile non preferito ed è possibile scegliere un'opzione nell'elenco ![Azioni rapide](media/error-bulb.png) per riscrivere automaticamente il codice con lo stile preferito.

## <a name="format-document-command"></a>Comando Formatta documento

È possibile configurare il comando **Formatta documento**, in **Modifica** > **Avanzate** > **Formatta documento**, per eseguire la pulizia del codice aggiuntivo in un file, ad esempio per rimuovere e ordinare using o applicare le preferenze di stile del codice. È possibile definire le impostazioni che si desidera applicare con **Formatta documento** nella [pagina delle opzioni Formattazione](reference/options-text-editor-csharp-formatting.md#format-document-settings).

La pulizia del codice rispetta le impostazioni configurate in un file *editorconfig* o in mancanza di tale regola o file, quelle impostate in **Strumenti** > **Opzioni** > **Editor di testo** > **C#** > [**Stile codice** oppure **Formattazione**].

La prima volta che si attiva il comando **Formatta documento** in Visual Studio, una barra informazioni gialla richiede all'utente di configurare le impostazioni di pulizia del codice.

> [!TIP]
> Le regole configurate con livello di gravità **Nessuno** non partecipano alla pulizia del codice, ma possono essere applicate singolarmente tramite il menu **Azioni rapide e refactoring**.

## <a name="see-also"></a>Vedere anche

- [Azioni rapide](../ide/quick-actions.md)
- [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)
- [Comportamento dell'editor (Visual Studio per Mac)](/visualstudio/mac/editor-behavior)