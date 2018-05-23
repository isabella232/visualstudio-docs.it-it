---
title: Preferenze di stile per il codice di Visual Studio
ms.date: 03/10/2017
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.workload:
- multiple
ms.openlocfilehash: 6dd046fa8a01cde7abdc33484da3ff8227eda966
ms.sourcegitcommit: 046a9adc5fa6d6d05157204f5fd1a291d89760b7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/11/2018
---
# <a name="code-style-preferences"></a>Preferenze di stile per il codice

Per impostare preferenze di stile per il codice per i progetti C# e Visual Basic, aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**. Selezionare **Editor di testo** > **C#** o **Base** > **Stile codice** > **Generale**. Le opzioni impostate in questa finestra sono valide per il computer locale.

Quando viene selezionata, ogni voce dell'elenco visualizza un'anteprima della preferenza:

![Opzioni di stile di codice](media/code-style-quick-actions-dialog.png)

## <a name="preference-and-severity"></a>Preferenza e gravità

Per ogni voce è possibile impostare i valori **Preferenza** e **Gravità** usando i menu a discesa disponibili per ogni riga. La gravità può essere impostata su **Nessuno**, **Suggerimento**, **Avviso** o **Errore**. Se si vogliono abilitare le [Azioni rapide](../ide/quick-actions.md) per uno stile di codice, assicurarsi che l'opzione **Gravità** sia impostata su un valore diverso da **Nessuno**. L'icona a forma di lampadina delle Azioni rapide ![icona lampadina piccola](media/vs2015_lightbulbsmall.png) viene visualizzata quando si usa uno stile non preferito ed è possibile scegliere un'opzione nell'elenco Azioni rapide per riscrivere automaticamente il codice con lo stile preferito.

## <a name="editorconfig-files"></a>File EditorConfig

Per .NET è possibile gestire le impostazioni relative agli stili di codice anche con un file [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). Le impostazioni nel file EditorConfig hanno la precedenza sulle opzioni selezionate nella finestra di dialogo **Opzioni**. È possibile usare un file EditorConfig per applicare e configurare lo stile di scrittura del codice per l'intero repository o per l'intero progetto.

## <a name="see-also"></a>Vedere anche

- [Azioni rapide](../ide/quick-actions.md)
- [Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)