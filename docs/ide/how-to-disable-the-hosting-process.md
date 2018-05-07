---
title: 'Procedura: Disabilitare il processo di hosting | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 47264ef7f1a6a2bd1a4ad3da59f53836f9ebb902
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-disable-the-hosting-process"></a>How to: Disable the Hosting Process
Le chiamate ad alcune API possono essere influenzate quando il processo di hosting è abilitato. In questi casi è necessario disabilitare il processo di hosting per restituire i risultati corretti.  
  
### <a name="to-disable-the-hosting-process"></a>Per disabilitare il processo di hosting  
  
1.  Aprire un progetto eseguibile in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. I progetti che non producono file eseguibili (ad esempio librerie di classi o progetti di servizio) non dispongono di questa opzione.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
3.  Fare clic sulla scheda **Debug**.  
  
4.  Deselezionare la casella di controllo **Abilita processo di hosting di Visual Studio**.  
  
 Quando il processo di hosting viene disabilitato, diverse funzionalità di debug non sono disponibili o presentano prestazioni ridotte. Per altre informazioni, vedere [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md).  
  
 In generale, quando il processo di hosting viene disabilitato:  
  
-   Aumenta il tempo necessario per avviare il debug di applicazioni [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
-   La valutazione dell'espressione della fase di progettazione non è disponibile.  
  
-   Il debug parzialmente attendibile non è disponibile.  
  
## <a name="see-also"></a>Vedere anche

[Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md)   
[Processo di hosting (vshost.exe)](../ide/hosting-process-vshost-exe.md)