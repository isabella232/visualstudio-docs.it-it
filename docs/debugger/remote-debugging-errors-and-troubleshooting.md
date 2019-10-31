---
title: Errori e risoluzione dei problemi di debug remoto | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b413ce193e6761d515de5bc5ef30fae8e18a3a3
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2019
ms.locfileid: "73187510"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errori e risoluzione dei problemi relativi al debug remoto

È possibile che si verifichino gli errori seguenti quando si tenta di eseguire il debug in modalità remota.

- [Error: Unable to Automatically Step Into the Server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Errore: il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Eseguire il debugger remoto come amministratore

Se non si esegue il debugger remoto come amministratore, è possibile che si verifichino problemi. Ad esempio, è possibile che venga visualizzato l'errore seguente: "il Visual Studio Remote Debugger (MSVSMON. EXE) non dispone di privilegi sufficienti per eseguire il debug del processo ". Se il debugger remoto viene eseguito come un'applicazione (non come servizio), è possibile che venga visualizzato un errore diverso per l' [account utente](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) .

### <a name="when-running-the-remote-debugger-as-a-service"></a>Quando si esegue il debugger remoto come servizio

Quando si esegue il debugger remoto come servizio, è consigliabile eseguirlo come amministratore per diversi motivi:

- Il servizio debugger remoto consente solo le connessioni dagli amministratori, quindi non **sono stati** introdotti nuovi rischi per la sicurezza eseguendolo come amministratore.

- Può impedire errori che si verificano quando l'utente di Visual Studio dispone di più diritti per eseguire il debug di un processo rispetto al debugger remoto stesso.

- Per semplificare l'installazione e la configurazione del debugger remoto.

Sebbene sia possibile eseguire il debug senza eseguire il debugger remoto come amministratore, esistono diversi requisiti per eseguire correttamente questa operazione e spesso richiedono passaggi di configurazione dei servizi più avanzati.

- L'account in uso nel computer remoto deve disporre del privilegio **di accesso come servizio** . Vedere i passaggi in "per aggiungere l'accesso come servizio" nell'articolo [non è possibile connettere](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) l'errore.

- L'account deve disporre dei diritti per eseguire il debug del processo di destinazione. Per ottenere questi diritti, è necessario eseguire il debugger remoto con lo stesso account del processo di cui eseguire il debug. L'alternativa più semplice consiste nell'eseguire il servizio come amministratore. 

- L'account deve essere in grado di connettersi (ovvero eseguire l'autenticazione con) il computer che esegue Visual Studio tramite la rete. In un dominio, è più semplice connettersi di nuovo se il debugger remoto è in esecuzione con l'account di sistema locale o di servizio di rete predefinito o con un account di dominio. Gli account predefiniti hanno privilegi di sicurezza elevati che possono rappresentare un rischio per la sicurezza.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Quando si esegue il debugger remoto come applicazione (modalità normale)

Se si sta tentando di connettersi a un processo non con privilegi elevati (ad esempio, un'applicazione normale), non è importante se il debugger remoto viene eseguito come amministratore.

Si vuole eseguire il debugger remoto come amministratore in diversi scenari:

- Si desidera eseguire la connessione a processi in esecuzione con un altro utente, ad esempio durante il debug di IIS, oppure

- Si sta provando ad avviare un altro processo e il processo che si vuole avviare è un amministratore.

**Non si desidera eseguire** come amministratore se si desidera avviare i processi e il processo che si desidera avviare **non** deve essere un amministratore.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)