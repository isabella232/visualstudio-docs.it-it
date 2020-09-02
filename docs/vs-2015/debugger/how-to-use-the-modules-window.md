---
title: 'Procedura: utilizzare la finestra moduli | Microsoft Docs'
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
ms.openlocfilehash: b592515692e23dce49c125c7895bd158904b653f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696133"
---
# <a name="how-to-use-the-modules-window"></a>Procedura: utilizzare la finestra Moduli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
> Questa funzionalità non è disponibile per il debug di script o SQL.  
  
 La finestra **moduli** elenca le dll e il file exe utilizzati dal programma e visualizza le informazioni rilevanti per ciascuna di esse.  
  
### <a name="to-display-the-modules-window-in-break-mode-or-in-run-mode"></a>Per visualizzare la finestra Moduli in modalità di interruzione o di esecuzione  
  
- Scegliere **finestre**dal menu **debug** , quindi fare clic su **moduli**.  
  
     Per impostazione predefinita, nella finestra **Moduli** i moduli sono ordinati in base all'ordine di caricamento. È tuttavia possibile ordinare i moduli in base a qualsiasi colonna.  
  
### <a name="to-sort-by-any-column"></a>Per eseguire l'ordinamento in base a una colonna  
  
- Fare clic sul pulsante nella parte superiore della colonna.  
  
     È possibile caricare i simboli o specificare un percorso di simboli dalla finestra **moduli** usando il menu di scelta rapida.  
  
## <a name="loading-symbols"></a>Caricamento dei simboli  
 Nella finestra **moduli** è possibile visualizzare i moduli con i simboli di debug caricati. Queste informazioni vengono visualizzate nella colonna **stato simboli** . Se lo stato è **ignorato loadingCannot trovare o aprire il file PDB**oppure il **Caricamento disabilitato dall'impostazione Includi/Escludi**, è possibile indirizzare il debugger per scaricare i simboli dai server dei simboli pubblici Microsoft o per caricare i simboli da una directory di simboli nel computer. Per altre informazioni, vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)  
  
#### <a name="to-load-symbols-manually"></a>Per caricare i simboli manualmente  
  
1. Nella finestra **moduli** fare clic con il pulsante destro del mouse su un modulo per il quale non sono stati caricati i simboli.  
  
2. Scegliere **Carica simboli da** , quindi fare clic su server dei simboli **Microsoft** o **percorso simboli**.  
  
#### <a name="to-change-symbol-load-settings"></a>Per modificare le impostazioni di caricamento dei simboli  
  
1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse su un modulo.  
  
2. Fare clic su **Impostazioni simboli**.  
  
     È ora possibile modificare le impostazioni di caricamento dei simboli, come descritto in [specificare i percorsi dei simboli e il comportamento di caricamento](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md#BKMK_Specify_symbol_locations_and_loading_behavior). Riavviare la sessione di debug per rendere effettive le modifiche.  
  
#### <a name="to-change-symbol-load-behavior-for-a-specific-module"></a>Per modificare il comportamento di caricamento dei simboli per un modulo specifico  
  
1. Nella finestra **Moduli** fare clic con il pulsante destro del mouse sul modulo.  
  
2. Scegliere **impostazioni automatiche di caricamento simboli** , quindi fare clic su **carica sempre manualmente** o per **impostazione predefinita**. Riavviare la sessione di debug per rendere effettive le modifiche.  
  
## <a name="see-also"></a>Vedere anche  
 [Esecuzione di interruzioni](https://msdn.microsoft.com/30fc4643-f337-4651-b1ff-f2de2c098d40)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
