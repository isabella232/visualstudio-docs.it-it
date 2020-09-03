---
title: Eseguire app di Windows Store nel computer locale | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e42a21a8-6423-4caf-b4dc-72b263e76019
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 031d764b95aa0f292702dde6167e0be9826270bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196311"
---
# <a name="run-windows-store-apps-on-the-local-machine"></a>Eseguire applicazioni Windows Store in un computer locale
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Si applica solo a Windows] (.. /Image windows_only_content.png "windows_only_content")  
  
 Per eseguire il debug, test o analisi delle prestazioni su un'app Windows Store, puoi eseguire l'app sullo stesso computer che ospita Visual Studio. Se lo schermo del dispositivo è abilitato per il tocco, puoi verificare la funzionalità completa dell'app, altrimenti dovrai limitarti ai movimenti con il mouse e la tastiera.  
  
## <a name="in-this-topic"></a><a name="BKMK_In_this_topic"></a> Contenuto dell'argomento  
 Puoi acquisire informazioni su:  
  
 [Come eseguire l'app su un computer locale](#BKMK_How_to_run_on_a_local_machine)  
  
 [Come passare tra un'app Windows Store e Visual Studio su un solo monitor](#BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor)  
  
## <a name="how-to-run-on-a-local-machine"></a><a name="BKMK_How_to_run_on_a_local_machine"></a> Come eseguire in un computer locale  
 Per eseguire l'app nel computer locale, selezionare **computer locale** dall'elenco a discesa accanto al pulsante Avvia debug sulla barra degli strumenti **standard** del debugger.  
  
 ![Effettuare l'esecuzione nel computer locale](../debugger/media/vsrun-f5-local.png "VSRUN_F5_Local")  
  
 Se la barra degli strumenti **standard** non è visibile, fare clic sul menu **Visualizza** , scegliere **barre degli strumenti**e quindi fare clic su **standard**.  
  
 La scelta adottata nell'elenco a discesa viene mantenuta nel file delle proprietà del progetto e diventa la destinazione di esecuzione predefinita.  
  
 Puoi anche impostare la destinazione di esecuzione direttamente nel file delle proprietà del progetto. Fare clic con il pulsante destro del mouse sul nome del progetto in **Esplora soluzioni** , quindi scegliere **Proprietà**. Effettua una delle seguenti operazioni:  
  
- In progetti C# e Visual Basic fare clic su **debug** , quindi selezionare **computer locale** nell'elenco a discesa **dispositivo di destinazione** .  
  
     ![&#35; C e pagina delle proprietà del progetto Visual Basic](../debugger/media/vsrun-cs-vb-projprop-local.png "VSRUN_CS_VB_ProjProp_Local")  
  
- Nei progetti C++ e JavaScript espandere il nodo **proprietà di configurazione** , fare clic su **debug**e quindi selezionare **debugger locale** dall'elenco **debugger da avviare** .  
  
     ![Pagina delle proprietà del progetto C&#43;&#43; e JavaScript](../debugger/media/vsrun-cpp-js-projprop-local.png "VSRUN_CPP_JS_ProjProp_Local")  
  
## <a name="how-to-switch-between-a-windows-store-app-and-visual-studio-on-a-single-monitor"></a><a name="BKMK_How_to_switch_between_a_Windows_Store_app_and_Visual_Studio_on_a_single_monitor"></a> Come passare da un'app di Windows Store a Visual Studio e viceversa in un singolo monitor  
 **Per passare da un'istanza in esecuzione di un'app Windows Store a Visual Studio**  
  
 Quando esegui un'app Windows Store su un computer locale e usi un solo monitor, potresti voler tornare a Visual Studio lasciando in esecuzione l'app. L'app potrebbe essere in uno stato che non può essere raggiunto da un punto di interruzione, ad esempio potrebbe essere in attesa di un evento o inclusa in un ciclo lungo o infinito. Per tornare a Visual Studio, premi ALT+TAB.
