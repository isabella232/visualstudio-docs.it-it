---
title: 'Procedura: utilizzare la finestra registri | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.registers
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
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
caps.latest.revision: 42
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 233092af638824c462a6d9a47865a1c6f5fd9397
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697472"
---
# <a name="how-to-use-the-registers-window"></a>Procedura: utilizzare la finestra Registri
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La finestra Registri è disponibile solo se il debug a livello di indirizzo è stato attivato nel nodo **Debug** della categoria **Generale** nella finestra di dialogo **Opzioni**.  
  
 Nella finestra **registri** viene visualizzato il contenuto del registro. Se si mantiene aperta la finestra **registri** durante l'esecuzione del programma, è possibile visualizzare le modifiche ai valori del registro durante l'esecuzione del codice. I valori modificati di recente sono visualizzati in rosso. È possibile modificare i valori dei registri. Per altre informazioni, vedere [procedura: modificare un valore di registro](../debugger/how-to-edit-a-register-value.md).  
  
 Per evitare confusione, nella finestra **Registri** i registri sono organizzati in gruppi che variano secondo la piattaforma e il tipo di processore. È possibile visualizzare o nascondere i gruppi desiderati. Per altre informazioni, vedere [How to: display and Hide Register groups](../debugger/how-to-display-and-hide-register-groups.md).  
  
 Per un'introduzione generale ai concetti sottostanti ai registri e alla finestra registri, vedere [nozioni di base sul debug: finestra registri](../debugger/debugging-basics-registers-window.md).  
  
> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-display-the-registers-window"></a>Per visualizzare la finestra Registri  
  
- Scegliere **finestre**dal menu **debug** , quindi selezionare **registri**.  
  
     Il debugger deve essere in esecuzione o in modalità di interruzione.  
  
    > [!NOTE]
    > Le informazioni relative ai registri non sono disponibili per le applicazioni SQL o script.  
  
## <a name="see-also"></a>Vedere anche  
 [Nozioni fondamentali di debug: finestra registri](../debugger/debugging-basics-registers-window.md)   
 [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)   
 [Nozioni fondamentali di debug: finestra Registri](../debugger/debugging-basics-registers-window.md)
