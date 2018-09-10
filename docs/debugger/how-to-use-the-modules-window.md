---
title: Visualizzare le DLL e file eseguibili nel Debugger | Microsoft Docs
ms.custom: H1Hack27Feb2017
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f582c435239c83503b179d6bb5e142936a41cb4b
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279011"
---
# <a name="view-dlls-and-executables-using-the-modules-window-in-the-visual-studio-debugger"></a>Visualizzare le DLL e file eseguibili tramite la finestra moduli nel Debugger di Visual Studio
 
Il **moduli** finestra sono elencate le DLL e file eseguibili (EXE) che vengono utilizzati dal programma e Visualizza informazioni rilevanti per ognuno. 

> [!NOTE]
>  Questa funzionalità non è disponibile per il debug di script o SQL. 
  
### <a name="to-display-the-modules-window"></a>Per visualizzare la finestra moduli  
  
-   Durante il debug, selezionare **Debug > Windows** e quindi fare clic su **moduli**.  
  
     Per impostazione predefinita, il **moduli** finestra sono ordinati in base all'ordine di caricamento. È tuttavia possibile ordinare i moduli in base a qualsiasi colonna.  
  
### <a name="to-sort-by-any-column"></a>Per eseguire l'ordinamento in base a una colonna  
  
-   Fare clic sul pulsante nella parte superiore della colonna.  
  
     È possibile caricare i simboli o specificare un percorso simboli dal **moduli** finestra usando il menu di scelta rapida.  
  
## <a name="loading-symbols"></a>Caricamento dei simboli  
 Nel **moduli** finestra, è possibile vedere quali moduli sono caricati i simboli di debug. Queste informazioni sono visualizzate le **stato simboli** colonna. Se lo stato è indicato **Skipped loadingCannot trovare o aprire il file PDB**, o **caricamento disabilitato dall'impostazione include/exclude**, è possibile usare il debugger per scaricare i simboli dai simboli pubblici Microsoft i server o per caricare i simboli da una directory di simboli nel computer. Per altre informazioni, vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Per caricare i simboli manualmente  
  
1.  Nel **moduli** finestra, pulsante destro del mouse un modulo per il quale non sono stati caricati i simboli.  
  
2.  Puntare **Carica simboli da** e quindi fare clic su **server dei simboli Microsoft** oppure **percorso dei simboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Per modificare le impostazioni di caricamento dei simboli  
  
1.  Nel **moduli** finestra, fare doppio clic su qualsiasi modulo MSIL.  
  
2.  Fare clic su **delle impostazioni dei simboli**.  
  
     È ora possibile modificare le impostazioni di caricamento di simboli, come descritto in [specificare i percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Riavviare la sessione di debug per rendere effettive le modifiche.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Per modificare il comportamento di caricamento dei simboli per un modulo specifico  
  
1.  Nel **moduli** finestra, fare clic sul modulo.  
  
2.  Puntare **impostazioni caricamento automatico simboli** e quindi fare clic su **Carica sempre manualmente** oppure **predefinito**. Riavviare la sessione di debug per rendere effettive le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Interruzione dell'esecuzione](/previous-versions/visualstudio/visual-studio-2010/7z9se2d8(v=vs.100))   
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)