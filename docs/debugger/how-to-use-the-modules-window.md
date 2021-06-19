---
title: Visualizzare DLL ed eseguibili
description: Visualizzare DLL ed eseguibili (.exe file) che l'app usa nella finestra Moduli durante una sessione di debug in Visual Studio.
ms.custom: SEO-VS-2020
titleSuffix: Visual Studio Modules window
ms.date: 11/04/2018
ms.topic: how-to
f1_keywords:
- vs.debug.modules
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f82b8a5051cf1c338c4b1aab6e78209fb2bc08b0
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385409"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Visualizzare DLL ed eseguibili nella finestra Moduli (C#, C++, Visual Basic, F#)

Durante Visual Studio debug, nella **finestra Moduli** vengono elencate e visualizzate informazioni sulle DLL e sui file eseguibili *(.exe* file) utilizzati dall'app.

> [!NOTE]
> La finestra Moduli non è disponibile per il debug di SQL o script.

## <a name="use-the-modules-window"></a>Usare la finestra Moduli

Per aprire la finestra Moduli, mentre si esegue il debug, selezionare **Debug**  >  **moduli Windows**  >   (oppure premere **CTRL+ALT+U).**

Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento. Per ordinare in base a qualsiasi colonna della finestra, selezionare l'intestazione nella parte superiore della colonna.

## <a name="load-symbols"></a>Caricare i simboli

La **colonna Stato simbolo** nella finestra **Moduli** mostra i moduli con simboli di debug caricati. Se lo stato è **Skipped loading symbols**, **Cannot find or open the PDB file** o Loading disabled by **include/exclude setting**, è possibile caricare i simboli manualmente. Per altre informazioni sul caricamento e sull'uso dei simboli, vedere [Specificare il simbolo (con estensione pdb) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Per caricare i simboli manualmente:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo per cui i simboli non sono stati caricati.

   - Selezionare **Informazioni sul caricamento dei** simboli per informazioni dettagliate sul motivo per cui i simboli non sono stati caricati.

   - Selezionare **Carica simboli** per caricare manualmente i simboli.

1. Se i simboli non vengono caricati, selezionare  **Impostazioni** simboli per aprire la finestra di dialogo Opzioni e specificare o modificare le posizioni di caricamento dei simboli.

   È possibile scaricare i simboli dai server di simboli Microsoft pubblici o da altri server oppure caricare i simboli da una cartella nel computer. Per informazioni dettagliate, vedere [Specificare i percorsi dei simboli e il comportamento di caricamento.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)

**Per modificare le impostazioni del comportamento di caricamento dei simboli:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo.

1. Selezionare **Impostazioni simboli**.

1. Selezionare **Carica tutti i simboli** oppure selezionare i moduli da includere o escludere.

1. Selezionare **OK**. Le modifiche vengono applicate nella sessione di debug successiva.

**Per modificare il comportamento di caricamento dei simboli per un modulo specifico:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo.

1. Nel menu di scelta rapida selezionare o deselezionare **Carica sempre automaticamente**. Le modifiche vengono applicate nella sessione di debug successiva.

## <a name="see-also"></a>Vedi anche
- [Interruzione dell'esecuzione](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Visualizzazione dei dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Specificare il simbolo (con estensione pdb) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)