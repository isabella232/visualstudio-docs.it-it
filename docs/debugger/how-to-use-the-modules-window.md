---
title: Visualizza file eseguibili e dll
description: Visualizzare le dll e gli eseguibili (file con estensione exe) usati dall'app nella finestra moduli durante una sessione di debug in Visual Studio.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0471aa25b14111271e6f9219e8e849eed49f113f
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98150561"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Visualizzare le dll e gli eseguibili nella finestra moduli (C#, C++, Visual Basic, F #)

Durante il debug di Visual Studio, la finestra **moduli** elenca e visualizza informazioni sulle dll e i file eseguibili (file con *estensione exe* ) usati dall'app.

> [!NOTE]
> La finestra moduli non è disponibile per il debug di script o SQL.

## <a name="use-the-modules-window"></a>Usare la finestra Moduli

Per aprire la finestra moduli, durante il debug, selezionare **debug**  >    >  **moduli** Windows (oppure premere **CTRL + ALT + U**).

Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento. Per eseguire l'ordinamento in base a qualsiasi colonna della finestra, selezionare l'intestazione nella parte superiore della colonna.

## <a name="load-symbols"></a>Caricare i simboli

Nella colonna **stato simbolo** della finestra **moduli** vengono visualizzati i moduli con i simboli di debug caricati. Se lo stato viene **ignorato** durante il caricamento dei simboli, **non è possibile trovare o aprire il file PDB oppure il** **caricamento è disabilitato dall'impostazione Includi/Escludi**. è possibile caricare i simboli manualmente. Per ulteriori informazioni sul caricamento e sull'utilizzo dei simboli, vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Per caricare i simboli manualmente:**

1. Nella finestra **moduli** fare clic con il pulsante destro del mouse sul modulo per il quale non sono stati caricati i simboli.

   - Selezionare **informazioni sul caricamento** dei simboli per informazioni dettagliate sul motivo per cui i simboli non sono stati caricati.

   - Selezionare **Carica simboli** per caricare manualmente i simboli.

1. Se i simboli non vengono caricati, selezionare **Impostazioni simboli** per aprire la finestra di dialogo **Opzioni** e specificare o modificare i percorsi di caricamento dei simboli.

   È possibile scaricare i simboli dai server di simboli Microsoft pubblici o da altri server oppure caricare i simboli da una cartella nel computer. Per informazioni dettagliate, vedere [specificare i percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Per modificare le impostazioni del comportamento di caricamento dei simboli:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo.

1. Selezionare **Impostazioni simboli**.

1. Selezionare **carica tutti i simboli** oppure selezionare i moduli da includere o escludere.

1. Selezionare **OK**. Le modifiche diventano effettive nella successiva sessione di debug.

**Per modificare il comportamento di caricamento dei simboli per un modulo specifico:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo.

1. Nel menu di scelta rapida selezionare o deselezionare **carica sempre automaticamente**. Le modifiche diventano effettive nella successiva sessione di debug.

## <a name="see-also"></a>Vedere anche
- [Interruzione dell'esecuzione](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)