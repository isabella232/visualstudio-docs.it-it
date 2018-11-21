---
title: Visualizzare i valori dei registri nel Debugger di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5f236bf43d3667cd4263d205c4588593a973824d
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257169"
---
# <a name="view-register-values-and-use-the-registers-window-in-the-visual-studio-debugger-c-c-visual-basic-f"></a>Visualizzare i valori di registrare e usare la finestra registri nel Debugger di Visual Studio (C#, C++, Visual Basic, F#)
La finestra Registri è disponibile solo se è abilitato il debug a livello di indirizzo nel **le opzioni** della finestra di dialogo **debug** nodo **generale** categoria.  
  
 Il **registra** finestra viene visualizzato il contenuto. Se si mantengono le **registra** finestra aperta durante l'esecuzione del programma, è possibile visualizzare le modifiche dei valori durante l'esecuzione di codice. I valori modificati di recente sono visualizzati in rosso. È possibile modificare i valori dei registri. Per altre informazioni, vedere [procedura: modificare un valore di registro](../debugger/how-to-edit-a-register-value.md).  
  
 Per evitare confusione, il **registra** finestra i registri sono organizzati in gruppi, che variano in base alla piattaforma e del processore tipo. È possibile visualizzare o nascondere i gruppi desiderati. Per altre informazioni, vedere [procedura: visualizzare e nascondere gruppi di registri](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Per un'introduzione generale a concetti di base registri e la finestra registri, vedere [nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
### <a name="to-display-the-registers-window"></a>Per visualizzare la finestra Registri  
  
-   Nel **Debug** menu, scegliere **Windows**e quindi scegliere **registra** (oppure scegliere **Ctrl** + **Alt**   +  **G**).  
  
     Il debugger deve essere in esecuzione o in modalità di interruzione.  
  
    > [!NOTE]
    >  Le informazioni relative ai registri non sono disponibili per le applicazioni SQL o script.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md)   
 [Visualizzazione dei dati nel Debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md)