---
title: 'Procedura: Disabilitare il processo di hosting | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- hosting process, disabling
- vshost.exe, disabling the hosting process
ms.assetid: 9157488d-737f-454b-8d8d-36f99de38bb0
caps.latest.revision: 12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 92e4fb1ae7cf7acf387eb9387284534eb55c1066
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60040015"
---
# <a name="how-to-disable-the-hosting-process"></a>Procedura: disabilitare il processo di hosting
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le chiamate ad alcune API possono essere influenzate quando il processo di hosting è abilitato. In questi casi è necessario disabilitare il processo di hosting per restituire i risultati corretti.  
  
### <a name="to-disable-the-hosting-process"></a>Per disabilitare il processo di hosting  
  
1. Aprire un progetto eseguibile in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. I progetti che non producono file eseguibili (ad esempio librerie di classi o progetti di servizio) non dispongono di questa opzione.  
  
2. Scegliere **Proprietà** dal menu **Progetto**.  
  
3. Fare clic sulla scheda **Debug**.  
  
4. Deselezionare la casella di controllo **Abilita processo di hosting di Visual Studio**.  
  
   Quando il processo di hosting viene disabilitato, diverse funzionalità di debug non sono disponibili o presentano prestazioni ridotte. Per altre informazioni, vedere [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md).  
  
   In generale, quando il processo di hosting viene disabilitato:  
  
- Aumenta il tempo necessario per avviare il debug di applicazioni [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].  
  
- La valutazione dell'espressione della fase di progettazione non è disponibile.  
  
- Il debug parzialmente attendibile non è disponibile.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug e processo di hosting](../debugger/debugging-and-the-hosting-process.md)   
 [Processo di hosting (vshost.exe)](../ide/hosting-process-vshost-exe.md)   
 [Uso di build in fase di sviluppo di applicazioni](http://msdn.microsoft.com/c9497d62-3b7b-4449-88e8-cf27acc9efe6)
