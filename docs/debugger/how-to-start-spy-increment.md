---
title: 'Procedura: Avviare Spy + + | Microsoft Docs'
ms.date: 12/16/2018
ms.topic: conceptual
helpviewer_keywords:
- Spy++, starting
ms.assetid: 1d36813a-dc2a-4fda-9b3d-a38928a62ced
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 84e16c5d540aa59ae0c5d56ccb311618ab311bd9
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54993457"
---
# <a name="how-to-start-spy"></a>Procedura: Avviare Spy++

È possibile avviare Spy + + da Visual Studio o un prompt dei comandi.  
  
 Quando si avvia Spy + +, se viene visualizzato un messaggio per chiedere l'autorizzazione per apportare modifiche al computer, selezionare **Sì**.  
  
> [!NOTE]
>  È possibile eseguire solo un'istanza di Spy + +. Se si tenta di avviare una seconda istanza, verifica semplicemente l'istanza attualmente in esecuzione ottenere lo stato attivo.

## <a name="prerequisites"></a>Prerequisiti

Spy + + richiede i componenti seguenti. È possibile selezionare questi componenti di installazione di Visual Studio selezionando il **singoli componenti** scheda e quindi selezionando i componenti seguenti.

* In debug e test, selezionare **strumenti di profilatura C++**
* Nell'attività di sviluppo, selezionare **le funzionalità core di Visual Studio C++**

Se sono state apportate modifiche, seguire le istruzioni per installare questi componenti.
  
## <a name="start-spy-from-visual-studio"></a>Avviare Spy + + da Visual Studio
  
Nel **degli strumenti** dal menu **Spy + +**.  
  
Poiché Spy + + viene eseguito in modo indipendente, dopo averla avviata è possibile chiudere Visual Studio.  
  
> [!NOTE]
>  Quando vengono registrati i messaggi con Spy + +, è possibile che il sistema operativo più lenta.  
  
## <a name="start-spy-at-a-command-prompt"></a>Spy + + partono da un prompt dei comandi  
  
1.  In una finestra del prompt dei comandi, passare alla cartella che contiene spyxx.exe. In genere, il percorso di questa cartella è... \\ *Cartella di installazione di visual Studio*\Common7\Tools\\.  
  
2.  Immettere **spyxx.exe**. 
  
## <a name="see-also"></a>Vedere anche  
 [Uso di Spy++](../debugger/using-spy-increment.md)   
 [Visualizzazioni di Spy++](../debugger/spy-increment-views.md)   
 [riferimenti per Spy++](../debugger/spy-increment-reference.md)