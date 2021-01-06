---
title: Disabilitare il debugger JIT | Microsoft Docs
description: È possibile che la finestra di dialogo debugger JIT si apra quando si verifica un errore in un'app. Informazioni sulle operazioni che è possibile eseguire quando si verifica questo problema e su come evitarlo.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7904b4bbf56c0a547d9f7b1e94bb46af8dd48d98
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903896"
---
# <a name="disable-the-just-in-time-debugger"></a>Disabilitare il debugger JIT

È possibile che la finestra di dialogo debugger JIT si apra quando si verifica un errore in un'app in esecuzione e impedire che l'app continui.

Il debugger JIT offre la possibilità di avviare Visual Studio per eseguire il debug dell'errore. Per visualizzare informazioni dettagliate sull'errore o provare a eseguirne il debug, è necessario che sia installato Visual Studio o un altro debugger selezionato.

Se si è già un utente di Visual Studio e si vuole provare a eseguire il debug dell'errore, vedere [eseguire il debug usando il debugger JIT](../debugger/debug-using-the-just-in-time-debugger.md). Se non è possibile correggere l'errore o si vuole impedire l'apertura del debugger JIT, è possibile disabilitare il debug JIT [da Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Se Visual Studio è stato installato ma non più, potrebbe essere necessario [disabilitare il debug JIT dal registro di sistema di Windows](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry).

Se Visual Studio non è installato, è possibile impedire il debug JIT disabilitando il debug degli script o il debug sul lato server.

- Se si sta provando a eseguire un'app Web, disabilitare il debug degli script:

  In Opzioni Internet e rete del **Pannello di controllo** di Windows  >    >  selezionare **Disabilita debug script (Internet Explorer)** e **Disabilita debug script (altro)**. La procedura e le impostazioni esatte dipendono dalla versione di Windows e dal browser.

  ![Opzioni Internet JIT](../debugger/media/jitinternetoptions.png "Opzioni Internet JIT")

- Se si sta ospitando un'app Web ASP.NET in IIS, disabilitare il debug sul lato server:

  1. Nella **visualizzazione funzionalità** Gestione IIS, nella sezione **ASP.NET** , fare doppio clic su **compilazione .NET** oppure selezionarla e quindi selezionare **Apri funzionalità** nel riquadro **azioni** .
  1. In   >  **debug** comportamento selezionare **false**. I passaggi sono diversi nelle versioni precedenti di IIS.

Dopo aver disabilitato il debug JIT, l'app potrebbe essere in grado di gestire l'errore ed eseguire normalmente.

Se l'app ha ancora un errore non gestito, è possibile che venga visualizzato un messaggio di errore o che l'app si arresti in modo anomalo o interrompa la risposta. L'app non verrà eseguita normalmente fino a quando l'errore non viene risolto. È possibile provare a contattare il proprietario dell'app e chiedergli di correggerla.
