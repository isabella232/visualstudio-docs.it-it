---
title: Visualizzare i file eseguibili e DLL
titleSuffix: Visual Studio Modules window
ms.custom: seodec18
ms.date: 11/04/2018
ms.topic: conceptual
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
ms.openlocfilehash: 0425929908f17b33de71a49b03ae8de729f28309
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681895"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Visualizzare i file eseguibili e DLL nella finestra moduli (C#, C++, Visual Basic, F#)

Durante il debug di Visual Studio, il **moduli** finestra elenca e Visualizza informazioni sui file eseguibili e DLL (*.exe* file) usata dall'applicazione.

> [!NOTE]
> La finestra moduli non è disponibile per il debug di script o SQL.

## <a name="use-the-modules-window"></a>Usare la finestra Moduli

Per aprire la finestra moduli, durante il debug, selezionare **Debug** > **Windows** > **moduli** (o premere **Ctrl + Alt + U** ).

Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento. Per ordinare in base a qualsiasi colonna di finestra, selezionare l'intestazione nella parte superiore della colonna.

## <a name="load-symbols"></a>Caricare i simboli

Il **stato simboli** colonna il **moduli** finestra Mostra quali moduli sono caricati i simboli di debug. Se lo stato è **caricamento simboli ignorato**, **non è possibile trovare o aprire il file PDB**, o **caricamento disabilitato dall'impostazione include/exclude**, è possibile caricare i simboli manualmente. Per altre informazioni sul caricamento e l'utilizzo di simboli, vedere [specificare i simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

**Per caricare i simboli manualmente:**

1. Nel **moduli** finestra, pulsante destro del mouse il modulo per i simboli non sono stati caricati.

   - Selezionare **informazioni sul caricamento simboli** per informazioni dettagliate sui motivi per cui non è stato caricato i simboli.

   - Selezionare **caricare i simboli** per caricare i simboli manualmente.

1. Se non vengono caricati i simboli, selezionare **impostazioni simboli** per aprire il **opzioni** finestra di dialogo e specificare o modificare percorsi di caricamento dei simboli.

   È possibile scaricare i simboli dai server dei simboli pubblici Microsoft o da altri server o caricare i simboli da una cartella nel computer. Per informazioni dettagliate, vedere [specificare i percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior).

**Per modificare le impostazioni del comportamento di caricamento dei simboli:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo.

1. Selezionare **delle impostazioni dei simboli**.

1. Selezionare **carica tutti i simboli**, o selezionare i moduli da includere o escludere.

1. Scegliere **OK**. Le modifiche effettive nella sessione di debug successiva.

**Per modificare il comportamento per un modulo specifico di caricamento dei simboli:**

1.  Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo.

1.  Nel menu di scelta rapida, selezionare o deselezionare **Carica sempre automaticamente**. Le modifiche effettive nella sessione di debug successiva.

## <a name="see-also"></a>Vedere anche
- [Interruzione dell'esecuzione](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)