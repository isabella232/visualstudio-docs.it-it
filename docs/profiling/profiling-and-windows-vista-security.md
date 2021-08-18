---
title: Profilatura e sicurezza in Windows Vista | Microsoft Docs
description: A seconda delle impostazioni di Autorizzazioni di accesso utente disponibili, un singolo utente potrebbe disporre dell'autorizzazione di sicurezza per profilare un processo nel computer.
ms.date: 11/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools,security
- performance tools, security
ms.assetid: 842112fc-b886-4801-8cd7-a25b314b0393
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 381cffa54c1dc0446b3e0e2cbc9fa897643e5058
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122060804"
---
# <a name="profiling-and-windows-vista-security"></a>Profilatura e sicurezza in Windows Vista

A seconda delle impostazioni delle autorizzazioni di accesso utente di [!INCLUDE[wiprlhext](../debugger/includes/wiprlhext_md.md)] rese disponibili dall'amministratore di un computer, un singolo utente potrebbe disporre dell'autorizzazione di sicurezza necessaria per profilare un processo in quel computer. Gli esempi seguenti illustrano le possibili differenze tra i diversi tipi di utenti:

- Se l'amministratore ha impostato l'avvio del driver e del servizio, alcuni utenti possono accedere a funzionalità di profilatura avanzate.

- Gli utenti di dominio possono accedere soltanto ad esempi di profilatura.

- Alcuni utenti possono negare l'accesso alla profilatura a tutti gli altri utenti.

  Per altre informazioni, vedere le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).

## <a name="cross-session-profiling"></a>Profilatura tra sessioni

La *profilatura tra sessioni* è una funzionalità per la profilatura di un processo eseguito in una sessione utente diversa. Ad esempio, la maggior parte dei servizi viene eseguita nella sessione 0 e gli utenti non possono effettuare esecuzioni direttamente nella sessione 0. Usando il pulsante **Associa a processo** nella barra degli strumenti di Esplora prestazioni o l'opzione `/attach` dello strumento della riga di comando VSPerfCmd, è possibile profilare la maggior parte dei processi in sessioni utente diverse.

È possibile visualizzare un elenco dei processi disponibili impostando le opzioni di visibilità relative alla profilatura tra processi. Queste opzioni sono disponibili nella finestra **Associa a processo** visualizzata quando si seleziona **Associa a processo**:

- **Mostra i processi di tutti gli utenti**

  Quando questa opzione non è selezionata, nell'elenco vengono visualizzati solo i processi di proprietà dell'utente corrente. Altrimenti l'elenco visualizza i processi di tutti gli utenti.

- **Mostra processi in tutte le sessioni**

  Quando questa opzione non è selezionata, nell'elenco vengono visualizzati i processi della sessione corrente. Altrimenti l'elenco visualizza i processi di tutte le sessioni.

## <a name="see-also"></a>Vedi anche

- [Cenni preliminari](../profiling/overviews-performance-tools.md)
- [VSPerfCmd](../profiling/vsperfcmd.md)
- [Procedura: eseguire la connessione a un processo in esecuzione](/previous-versions/visualstudio/visual-studio-2010/c6wf8e4z\(v\=vs.100\))
