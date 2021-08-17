---
title: Visualizzare DLL ed eseguibili
description: Visualizzare DLL ed eseguibili (file .exe) che l'app usa nella finestra Moduli durante una sessione di debug in Visual Studio.
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
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 164b61c55fef81d2327ed8b5b803360724f15a4df872935400519b1da6cd5ca7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453287"
---
# <a name="view-dlls-and-executables-in-the-modules-window-c-c-visual-basic-f"></a>Visualizzare DLL ed eseguibili nella finestra Moduli (C#, C++, Visual Basic, F#)

Durante Visual Studio debug, la  finestra Moduli elenca e visualizza le informazioni sulle DLL e i file eseguibili *(file*.exe) utilizzati dall'app.

> [!NOTE]
> La finestra Moduli non è disponibile per il debug SQL script.

## <a name="use-the-modules-window"></a>Usare la finestra Moduli

Per aprire la finestra Moduli, durante il debug, selezionare Debug  >  **Windows**  >  **Moduli** (o premere **CTRL+ALT+U).**

Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento. Per ordinare in base a qualsiasi colonna della finestra, selezionare l'intestazione nella parte superiore della colonna.

## <a name="load-symbols"></a>Caricare i simboli

La **colonna Stato simbolo** nella finestra **Moduli** mostra i moduli in cui sono caricati i simboli di debug. Se lo stato è **Skipped loading symbols**(Caricamento ignorato), Cannot find or open the PDB file (Impossibile trovare o aprire il **file PDB)** o Loading disabled by include/exclude (Caricamento disabilitato dall'impostazione **include/exclude),** è possibile caricare i simboli manualmente. Per altre informazioni sul caricamento e sull'uso dei simboli, vedere Specificare i file di simboli (con estensione [pdb) e di origine.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)

**Per caricare manualmente i simboli:**

1. Nella finestra **Moduli fare** clic con il pulsante destro del mouse sul modulo per cui non sono stati caricati i simboli.

   - Selezionare **Informazioni sul caricamento dei** simboli per informazioni dettagliate sul motivo per cui i simboli non sono stati caricati.

   - Selezionare **Carica simboli** per caricare i simboli manualmente.

1. Se i simboli non vengono caricati, selezionare Simbolo  **Impostazioni** per aprire la finestra di dialogo Opzioni e specificare o modificare i percorsi di caricamento dei simboli.

   È possibile scaricare i simboli dai server di simboli Microsoft pubblici o da altri server oppure caricare i simboli da una cartella nel computer. Per informazioni dettagliate, vedere [Specificare i percorsi dei simboli e il comportamento di caricamento.](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior)

**Per modificare le impostazioni del comportamento di caricamento dei simboli:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo.

1. Selezionare **Simbolo Impostazioni**.

1. Selezionare **Carica tutti i simboli** oppure selezionare i moduli da includere o escludere.

1. Selezionare **OK**. Le modifiche vengono applicate nella sessione di debug successiva.

**Per modificare il comportamento di caricamento dei simboli per un modulo specifico:**

1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo.

1. Nel menu di scelta rapida selezionare o deselezionare **Carica sempre automaticamente.** Le modifiche vengono applicate nella sessione di debug successiva.

## <a name="see-also"></a>Vedi anche
- [Interruzione dell'esecuzione](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))
- [Visualizzazione dei dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
- [Specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)