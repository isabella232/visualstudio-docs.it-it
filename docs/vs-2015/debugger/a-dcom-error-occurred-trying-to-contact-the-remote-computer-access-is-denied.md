---
title: Errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato. | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.remote.dcom_access_denied
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
helpviewer_keywords:
- remote debugging, DCOM error
- remote DCOM access denied error
- DCOM, access errors
ms.assetid: 9d7dfc1b-9fe0-4f54-9c50-9c0e0f8358c5
caps.latest.revision: 30
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ec23d23934268ebb50699bc1de3d17b75d357d3a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51770279"
---
# <a name="a-dcom-error-occurred-trying-to-contact-the-remote-computer-access-is-denied"></a>Errore DCOM durante il tentativo di contattare il computer remoto. Accesso negato.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il debug remoto usa DCOM per la comunicazione tra i computer locale e remoto nelle situazioni seguenti:  
  
- Il debugger è impostato sulla **modalità di compatibilità nativa** oppure è selezionata l'opzione **Modalità di compatibilità gestita** nella pagina **Strumenti / Opzioni / Debug**   
  
- Si esegue il debug di codice C++ (C++ /CLI) gestito.  
  
- In Visual Studio 2013, quando è selezionata l'opzione **Abilita Modifica e continuazione nativo** nella pagina **Strumenti / Opzioni / Debug**  
  
- Alcuni scenari di debug di terze parti  
  
  Questo errore si verifica quando il processo di Visual Studio non è in grado di autenticarsi (o le credenziali fornite sono ritenute insufficienti) rispetto al processo del debugger remoto su DCOM. Una o più delle soluzioni seguenti possono risolvere il problema:  
  
- Disattivare  **Usa modalità di compatibilità nativa** e **Modalità di compatibilità gestita**.  
  
- In Visual Studio 2013 disattivare **Abilita Modifica e continuazione nativo**.  
  
- Riavviare entrambi i computer.  
  
- Se il debug remoto richiede l'immissioni di credenziali, selezionare l'opzione per salvarle.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



