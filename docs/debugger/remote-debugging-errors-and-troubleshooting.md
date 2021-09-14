---
title: Errori di debug remoto e risoluzione dei | Microsoft Docs
description: Visualizzare i collegamenti agli errori di debug remoto comuni in Visual Studio. Informazioni su come eseguire il debugger remoto come amministratore.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugger, errors
- debugging errors
- remote debugging, troubleshooting
- troubleshooting remote debugging
- errors [debugger], remote debugging
- remote debugging, errors
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 3a111fef09a702cc122b391d2d1f864d0bf5117d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627905"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errori e risoluzione dei problemi relativi al debug remoto

Quando si tenta di eseguire il debug in modalità remota, è possibile che si sia verificati gli errori seguenti.

- [Errore: impossibile eseguire automaticamente l'istruzione sul server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Impossibile accedere Connessione'Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Errore: il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Eseguire il debugger remoto come amministratore

Si potrebbero verificare problemi se non si esegue il debugger remoto come amministratore. Ad esempio, potrebbe essere visualizzato l'errore seguente: "Il Visual Studio Remote Debugger (MSVSMON.EXE) ha privilegi insufficienti per eseguire il debug di questo processo". Se si esegue il debugger remoto come applicazione (non come servizio), è possibile che venga visualizzato [l'errore dell'account](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) utente diverso.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Quando si esegue il debugger remoto come servizio

Quando si esegue il debugger remoto come servizio, è consigliabile eseguire il debugger come amministratore per diversi motivi:

- Il servizio debugger remoto consente solo le  connessioni degli amministratori, quindi non sono introdotti nuovi rischi per la sicurezza eseguendolo come amministratore.

- Può impedire errori che si verificano quando l Visual Studio utente ha più diritti per eseguire il debug di un processo rispetto al debugger remoto stesso.

- Per semplificare l'installazione e la configurazione del debugger remoto.

Sebbene sia possibile eseguire il debug senza eseguire il debugger remoto come amministratore, esistono diversi requisiti per il corretto funzionamento e spesso richiedono passaggi di configurazione del servizio più avanzati.

- L'account in uso nel computer remoto deve avere il **privilegio di accesso come** servizio. Vedere la procedura descritta in "Per aggiungere l'accesso come servizio" nell'articolo [impossibile connettersi all'errore.](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)

- L'account deve disporre dei diritti per eseguire il debug del processo di destinazione. Per ottenere questi diritti, è necessario eseguire il debugger remoto con lo stesso account del processo di cui eseguire il debug. L'alternativa più semplice consiste nell'eseguire il servizio come amministratore. 

- L'account deve essere in grado di connettersi nuovamente al computer Visual Studio rete. In un dominio è più semplice connettersi se il debugger remoto è in esecuzione con gli account di sistema locale o di servizio di rete predefiniti o un account di dominio. Gli account predefiniti hanno privilegi di sicurezza elevati che possono presentare un rischio per la sicurezza.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Quando si esegue il debugger remoto come applicazione (modalità normale)

Se si sta tentando di connettersi a un processo non con privilegi elevati, ad esempio un'applicazione normale, non è importante se si esegue il debugger remoto come amministratore.

Si vuole eseguire il debugger remoto come amministratore in diversi scenari:

- Si vuole connettersi a processi in esecuzione come un altro utente (ad esempio durante il debug di IIS) o

- Si sta tentando di avviare un altro processo e il processo da avviare è un amministratore.

Non si **vuole** eseguire come amministratore se si vogliono avviare processi e il processo da avviare non deve **essere** un amministratore.

## <a name="see-also"></a>Vedi anche
- [Debug remoto](../debugger/remote-debugging.md)