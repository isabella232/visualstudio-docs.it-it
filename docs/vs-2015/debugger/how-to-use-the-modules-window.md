---
title: 'Procedura: Use the Modules Window | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.modules
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Modules window
- Modules window
- executable files, displaying while debugging
- debugging [Visual Studio], displaying modules
- DLLs, displaying while debugging
- modules, displaying
ms.assetid: d840fdca-b035-4452-b652-72580c831896
caps.latest.revision: 41
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b19237b94ed3d53c49f248e22b86d3af8180625
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63445046"
---
# <a name="how-to-use-the-modules-window"></a>Procedura: Utilizzare la finestra moduli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Questa funzionalità non è disponibile per il debug di script o SQL.  
  
 Il **moduli** finestra sono elencate le DLL ed EXE che vengono utilizzati dal programma e Visualizza informazioni rilevanti per ognuno.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Per visualizzare la finestra Moduli in modalità di interruzione o di esecuzione  
  
- Nel **Debug** menu, scegliere **Windows**e quindi fare clic su **moduli**.  
  
     Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento. È tuttavia possibile ordinare i moduli in base a qualsiasi colonna.  
  
### <a name="to-sort-by-any-column"></a>Per eseguire l'ordinamento in base a una colonna  
  
- Fare clic sul pulsante nella parte superiore della colonna.  
  
     È possibile caricare i simboli o specificare un percorso simboli dal **moduli** finestra usando il menu di scelta rapida.  
  
## <a name="loading-symbols"></a>Caricamento dei simboli  
 Nel **moduli** finestra, è possibile vedere quali moduli sono caricati i simboli di debug. Queste informazioni sono visualizzate le **stato simboli** colonna. Se lo stato è indicato **Skipped loadingCannot trovare o aprire il file PDB**, o **caricamento disabilitato dall'impostazione include/exclude**, è possibile usare il debugger per scaricare i simboli dai simboli pubblici Microsoft i server o per caricare i simboli da una directory di simboli nel computer. Per altre informazioni, vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Per caricare i simboli manualmente  
  
1. Nel **moduli** finestra, pulsante destro del mouse un modulo per il quale non sono stati caricati i simboli.  
  
2. Puntare **Carica simboli da** e quindi fare clic su **server dei simboli Microsoft** oppure **percorso dei simboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Per modificare le impostazioni di caricamento dei simboli  
  
1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo.  
  
2. Fare clic su **delle impostazioni dei simboli**.  
  
     È ora possibile modificare le impostazioni di caricamento di simboli, come descritto in [specificare i percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Riavviare la sessione di debug per rendere effettive le modifiche.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Per modificare il comportamento di caricamento dei simboli per un modulo specifico  
  
1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo.  
  
2. Puntare **impostazioni caricamento automatico simboli** e quindi fare clic su **Carica sempre manualmente** oppure **predefinito**. Riavviare la sessione di debug per rendere effettive le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Interruzione dell'esecuzione](http://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
