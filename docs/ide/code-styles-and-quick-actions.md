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
ms.openlocfilehash: a7a478e8d3575e70a11ec776d59337ae93e7a677
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "57873360"
---
# <a name="code-style-preferences"></a>Preferenze di stile per il codice

Per impostare preferenze di stile per il codice per i progetti C# e Visual Basic, aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**. Nella finestra di dialogo **Opzioni** selezionare **Editor di testo** > [**C#** oppure **Basic**] > **Stile codice** > **Generale**. Quando viene selezionata, ogni voce dell'elenco visualizza un'anteprima della preferenza:

![Opzioni di stile di codice](media/code-style-quick-actions-dialog.png)

Le opzioni impostate in questa finestra sono applicabili all'account di personalizzazione di Visual Studio e non vengono associate a un progetto o una codebase in particolare. Inoltre, non vengono applicate in fase di compilazione, neanche nelle compilazioni con di integrazione continua (CI). Se si vogliono associare le preferenze di stile per il codice al progetto e fare in modo che gli stili vengano applicati durante la compilazione, specificare le preferenze in un [file .editorconfig](#editorconfig-files).

> [!NOTE]
> Questo argomento si applica a Visual Studio in Windows. Per Visual Studio per Mac, vedere [Comportamento dell'editor in Visual Studio per Mac](/visualstudio/mac/editor-behavior).

## <a name="preference-and-severity"></a>Preferenza e gravità

Per ogni voce è possibile impostare i valori **Preferenza** e **Gravità** usando i menu a discesa disponibili per ogni riga. La gravità può essere impostata su **Nessuno**, **Suggerimento**, **Avviso** o **Errore**. Se si vogliono abilitare le [Azioni rapide](../ide/quick-actions.md) per uno stile di codice, assicurarsi che l'opzione **Gravità** sia impostata su un valore diverso da **Nessuno**. L'icona a forma di lampadina **lampadina**, di lampadina di errore ![lampadina di errore](media/screwdriver.png) o di cacciavite **cacciavite** di ![Azioni rapide](media/light-bulb-dropdown.png) viene visualizzata quando si usa uno stile non preferito ed è possibile scegliere un'opzione nell'elenco ![Azioni rapide](media/error-bulb.png) per riscrivere automaticamente il codice con lo stile preferito.

## <a name="editorconfig-files"></a>File EditorConfig

È possibile specificare le impostazioni di stile del codice per .NET anche mediante l'aggiunta di un file [EditorConfig](../ide/editorconfig-code-style-settings-reference.md) al progetto. Questi file sono associati una codebase anziché a un account di personalizzazione di Visual Studio. Le impostazioni nel file EditorConfig hanno la precedenza sulle opzioni selezionate nella finestra di dialogo **Opzioni**. Usare un file EditorConfig quando si vogliono imporre stili di codice per tutti i collaboratori del repository o del progetto.

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