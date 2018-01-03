---
title: Preferenze di stile per il codice di Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 03/10/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.CSharp.Code_Style.General
- VS.ToolsOptionsPages.Text_Editor.Basic.Code_Style.General
ms.openlocfilehash: 24470f4fdb1a75d6ebd2743b2ade72e6195842b4
ms.sourcegitcommit: ebe9fb5eda724936f7a059d35d987c29dffdb50d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2017
---
# <a name="code-style-preferences"></a>Preferenze di stile per il codice

Per impostare preferenze di stile per il codice per i progetti C# e Visual Basic, aprire la finestra di dialogo **Opzioni** dal menu **Strumenti**. Selezionare **Editor di testo**, **C#** o **Basic**, **Stile codice**, **Generale**. Le opzioni impostate in questa finestra sono valide per il computer locale. Quando viene selezionata, ogni voce dell'elenco visualizza un'anteprima delle preferenze corrispondenti, come illustrato di seguito.

![Opzioni di stile di codice](media/code-style-quick-actions-dialog.png)

Per ogni voce è possibile impostare **Preferenza** e **Gravità** dal menu a discesa disponibile per ogni riga. La gravità può essere impostata su **Nessuna**, **Suggerimento**, **Avviso** o **Errore**. Visual Studio si comporterà nel modo opportuno. Se si vogliono usare [azioni rapide](quick-actions.md) con gli stili di codice per riscrivere automaticamente il codice secondo lo stile preferito, assicurarsi che l'impostazione sia diversa da **Nessuna**, in modo che l'icona Lampadina ![Icona Lampadina piccola](media/vs2015_lightbulbsmall.png "VS2017_LightBulbSmall") venga visualizzata quando vengono usati gli stili non preferiti. È quindi possibile applicare queste preferenze scegliendo l'icona Lampadina o premendo **Ctrl +.** quando il cursore si trova sulla riga di codice appropriata.

Per .NET è possibile gestire le impostazioni relative agli stili di codice anche con un file [EditorConfig](../ide/editorconfig-code-style-settings-reference.md). In questo caso, le impostazioni nel file EditorConfig hanno la precedenza sulle opzioni selezionate nella finestra di dialogo **Opzioni**. È possibile usare un file EditorConfig per applicare e configurare lo stile di scrittura del codice per l'intero repository o per l'intero progetto.

## <a name="see-also"></a>Vedere anche

[Azioni rapide](quick-actions.md)  
[Impostazioni delle convenzioni per la scrittura del codice .NET per EditorConfig](../ide/editorconfig-code-style-settings-reference.md)