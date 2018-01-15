---
title: Distribuire un'estensione del modello di livello | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dependency diagrams, deploying extensions
- layer models, deploying extensions
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 060cf2551f6c79259c7094d52f35db92f9ebcfef
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2018
---
# <a name="deploy-a-layer-model-extension"></a>Distribuire un'estensione del modello di livello
Altri utenti di Visual Studio possono installare estensioni di modellazione del livello creati tramite Visual Studio.  
  
## <a name="installing-your-extension"></a>Installazione dell'estensione  
 L'estensione viene compilata in un file VSIX, che è possibile installare in altri computer. È anche possibile installarla nel computer di sviluppo, per renderla disponibile nell'istanza principale di Visual Studio.  
  
#### <a name="to-install-the-extension"></a>Per installare l'estensione  
  
1.  Nel progetto che contiene **source.vsix.manifest**aprire **bin\\ \***  in Esplora File.  
  
2.  Copia il  **\*VSIX** file nel computer in cui si desidera installare l'estensione.  
  
3.  Nel computer di destinazione fare doppio clic sul file con estensione VSIX in Esplora risorse.  
  
     Verrà aperto il programma di installazione di VSIX.  
  
#### <a name="to-uninstall-the-extension"></a>Per disinstallare l'estensione  
  
1.  In Visual Studio, sul **strumenti** menu, fare clic su **estensioni e aggiornamenti**.  
  
2.  Fare clic sul nome dell'estensione e quindi fare clic su **Disinstalla**.  
  
## <a name="installing-an-extension-on-a-team-foundation-build-server"></a>Installazione di un'estensione in un server Team Foundation Build  
 Nei server [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] non viene in genere installato Visual Studio, quindi non è possibile installare VSIX facendo doppio clic su di esso. L'installazione di [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] include alcuni componenti che consentono l'esecuzione di un'estensione VSIX, ma è necessario installarla manualmente.  
  
#### <a name="to-install-your-layer-extension-on-a-includeesprbuildmiscincludesesprbuildmdmd-server"></a>Per installare l'estensione del livello in un server [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]  
  
1.  Copia il **VSIX** file dal computer di sviluppo per la [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] computer.  
  
     Inserire il file VSIX in uno dei percorsi seguenti:  
  
    -   Per installare per tutti gli utenti e i servizi:  
  
         %ProgramFiles%\Microsoft Visual Studio [versione]\Common7\IDE\Extensions\Microsoft  
  
    -   Per installare solo per il servizio di rete che esegue [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)]:  
  
         %WinDir%\ServiceProfiles\NetworkService\AppData\Local\Microsoft\VisualStudio\\\Extensions\Microsoft [versione]  
  
    -   Se si è configurato [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)] per l'esecuzione in modalità interattiva come un utente specifico, è possibile installarla solo per quell'utente:  
  
         %LocalAppData%\Microsoft\VisualStudio\\\Extensions\Microsoft [versione]  
  
        > [!NOTE]
        >  % LocalAppData % è in genere *DriveName*: gli utenti*UserName*AppDataLocal.  
  
2.  Espandere ogni file VSIX in una cartella nello stesso percorso:  
  
    1.  Modificare l'estensione del nome di file da **VSIX** a **zip**.  
  
    2.  Estrarre il contenuto del file ZIP in una cartella.  
  
    3.  Eliminare il file ZIP.  
  
3.  Riavviare [!INCLUDE[esprbuild](../misc/includes/esprbuild_md.md)].
