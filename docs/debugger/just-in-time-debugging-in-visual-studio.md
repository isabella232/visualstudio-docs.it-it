---
title: Disabilitare il debugger JUST-In-Time | Microsoft Docs
description: La finestra di dialogo Debugger JUST-In-Time può essere visualizzata quando si verifica un errore in un'app. Informazioni sulle operazioni che è possibile eseguire in questo caso e sui modi per impedirlo.
ms.custom: SEO-VS-2020
ms.date: 05/23/2018
ms.topic: troubleshooting
helpviewer_keywords:
- debugging [Visual Studio], Just-In-Time
- Just-In-Time debugging
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: b9d0c820877d30d0228c996538e320508dad2661
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122080780"
---
# <a name="disable-the-just-in-time-debugger"></a>Disabilitare il debugger JIT

La finestra di dialogo Debugger JUST-In-Time può essere visualizzata quando si verifica un errore in un'app in esecuzione e impedire all'app di continuare.

Il debugger JUST-In-Time offre la possibilità di avviare Visual Studio per eseguire il debug dell'errore. È necessario aver installato Visual Studio un altro debugger selezionato per visualizzare informazioni dettagliate sull'errore o provare a eseguirne il debug.

Se si è già un utente Visual Studio e si vuole provare a eseguire il debug dell'errore, vedere Eseguire il debug con il [debugger JUST-In-Time.](../debugger/debug-using-the-just-in-time-debugger.md) Se non è possibile correggere l'errore o si vuole evitare l'apertura del debugger JIT, è possibile disabilitare il debug JIT [da Visual Studio](debug-using-the-just-in-time-debugger.md#BKMK_Enabling).

Se l'Visual Studio è stata installata ma non è più installata, potrebbe essere necessario disabilitare il debug JIT dal Registro [di Windows .](debug-using-the-just-in-time-debugger.md#disable-just-in-time-debugging-from-the-windows-registry)

Se non è installato Visual Studio, è possibile impedire il debug JIT disabilitando il debug degli script o il debug sul lato server.

- Se si sta tentando di eseguire un'app Web, disabilitare il debug degli script:

  In Windows **Pannello di controllo** Rete e Opzioni Internet selezionare Disabilita debug  >    >   **script (Internet Explorer)** e Disabilita debug **script (altro).** I passaggi e le impostazioni esatti dipendono dalla versione di Windows e dal browser.

  ![Opzioni Internet JIT](../debugger/media/jitinternetoptions.png "Opzioni Internet JIT")

- Se si ospita un'app Web ASP.NET in IIS, disabilitare il debug lato server:

  1. Nella visualizzazione Delle **funzionalità di** Gestione IIS, nella sezione **ASP.NET** fare doppio clic  su **Compilazione .NET** oppure selezionarla e quindi selezionare Apri funzionalità nel **riquadro** Azioni.
  1. In **Debug**  >  **del** comportamento selezionare **False.** I passaggi sono diversi nelle versioni precedenti di IIS.

Dopo aver disabilitato il debug JIT, l'app potrebbe essere in grado di gestire l'errore ed essere eseguita normalmente.

Se l'app presenta ancora un errore non gestito, è possibile che venga visualizzato un messaggio di errore o che l'app si arresti in modo anomalo o smetta di rispondere. L'app non verrà eseguita normalmente fino a quando non viene corretto l'errore. È possibile provare a contattare il proprietario dell'app e chiedere di risolverlo.
