---
title: Eseguire App UWP nel computer locale | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: uwp
ms.openlocfilehash: 63cb81c9bc168ad0bda8d675c0bf0bbde3759eff
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="run-uwp-apps-on-the-local-machine"></a>Eseguire App UWP nel computer locale
![Si applica solo a Windows](../debugger/media/windows_only_content.png "windows_only_content")  
  
 Per eseguire il debug, test o eseguire l'analisi delle prestazioni in un'app UWP, è possibile eseguire l'app nello stesso computer che ospita Visual Studio. Se lo schermo del dispositivo è abilitato per il tocco, puoi verificare la funzionalità completa dell'app, altrimenti dovrai limitarti ai movimenti con il mouse e la tastiera.  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a>Modalità di esecuzione in un computer locale  
 Per eseguire l'app nel computer locale, selezionare **computer locale** dall'elenco a discesa accanto al pulsante Avvia debug del debugger **Standard** barra degli strumenti.  
  
 ![Eseguire sul computer locale](../debugger/media/vsrun_f5_local.png "VSRUN_F5_Local")  
  
 Se non è possibile visualizzare il **Standard** sulla barra degli strumenti, fare clic su di **vista** dal menu **barre degli strumenti**e quindi fare clic su **Standard**.  
  
 La scelta adottata nell'elenco a discesa viene mantenuta nel file delle proprietà del progetto e diventa la destinazione di esecuzione predefinita.  
  
 Puoi anche impostare la destinazione di esecuzione direttamente nel file delle proprietà del progetto. Fare doppio clic sul nome del progetto in **Esplora** e quindi scegliere **proprietà**. Effettua una delle seguenti operazioni:  
  
-   Nei progetti c# e Visual Basic, fare clic su **Debug** e quindi selezionare **computer locale** dal **dispositivo di destinazione** elenco a discesa.  
  
     ![C &#35; pagina proprietà del progetto Visual Basic e](../debugger/media/vsrun_cs_vb_projprop_local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   In progetti C++ e JavaScript Espandi il **le proprietà di configurazione** nodo, fare clic su **debug**, quindi selezionare **Debugger locale** dal **Debugger Per avviare** elenco.  
  
     ![C &#43; &#43; pagina delle proprietà di progetto JavaScript e](../debugger/media/vsrun_cpp_js_projprop_local.png "VSRUN_CPP_JS_ProjProp_Local")  