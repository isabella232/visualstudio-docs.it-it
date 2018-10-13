---
title: Le app di eseguire Windows Store nel computer locale | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b460d1eecfe96cddce27926ee8e31aae258d8dcf
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188385"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Eseguire applicazioni Windows Store in un computer locale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica solo a Windows] (.. /Image/windows_only_content.png "windows_only_content")  
  
 Per eseguire il debug, test o analisi delle prestazioni su un'app Windows Store, puoi eseguire l'app sullo stesso computer che ospita Visual Studio. Se lo schermo del dispositivo è abilitato per il tocco, puoi verificare la funzionalità completa dell'app, altrimenti dovrai limitarti ai movimenti con il mouse e la tastiera.  
  
##  <a name="BKMK_In_this_topic"></a> In questo argomento  
 Puoi acquisire informazioni su:  
  
 [Come eseguire in un computer locale](#BKMK_How_to_run_on_a_local_machine)  
  
 [Viene illustrato come passare tra un'app di Windows Store e Visual Studio su un solo monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
##  <a name="BKMK_How_to_run_on_a_local_machine"></a> Come eseguire in un computer locale  
 Per eseguire l'app nel computer locale, selezionare **computer locale** dall'elenco a discesa accanto al pulsante Avvia debug nel debugger **Standard** sulla barra degli strumenti.  
  
 ![Eseguire sul computer locale](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Se non è possibile visualizzare il **Standard** sulla barra degli strumenti, fare clic sul **View** dal menu **barre degli strumenti**e quindi fare clic su **Standard**.  
  
 La scelta adottata nell'elenco a discesa viene mantenuta nel file delle proprietà del progetto e diventa la destinazione di esecuzione predefinita.  
  
 Puoi anche impostare la destinazione di esecuzione direttamente nel file delle proprietà del progetto. Fare clic sul nome del progetto in **Esplora soluzioni** e quindi scegliere **proprietà**. Effettua una delle seguenti operazioni:  
  
-   Nei progetti c# e Visual Basic, fare clic su **Debug** e quindi selezionare **computer locale** dal **dispositivo di destinazione** elenco a discesa.  
  
     ![C&#35; pagina delle proprietà progetto Visual Basic e](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
-   Nei progetti C++ e JavaScript, espandere la **le proprietà di configurazione** nodo, fare clic su **Debugging**e quindi selezionare **Debugger locale** dal **Debugger Per avviare** elenco.  
  
     ![C&#43; &#43; e pagina delle proprietà di progetto JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
##  <a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Viene illustrato come passare tra un'app di Windows Store e Visual Studio su un solo monitor  
 **Per passare da un'istanza in esecuzione di un'app Windows Store da Visual Studio**  
  
 Quando esegui un'app Windows Store su un computer locale e usi un solo monitor, potresti voler tornare a Visual Studio lasciando in esecuzione l'app. L'app potrebbe essere in uno stato che non può essere raggiunto da un punto di interruzione, ad esempio potrebbe essere in attesa di un evento o inclusa in un ciclo lungo o infinito. Per tornare a Visual Studio, premi ALT+TAB.



