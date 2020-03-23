---
title: Errori di debug remoto e risoluzione dei problemi Documenti Microsoft
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
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302091"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errori e risoluzione dei problemi relativi al debug remoto

È possibile riscontrare i seguenti errori quando si tenta di eseguire il debug in remoto.

- [Errore: impossibile eseguire automaticamente l'istruzione sul server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.](error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running.md)

- [Impossibile connettersi a Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Errore: il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Eseguire il debugger remoto come amministratore

Se non si esegue il debugger remoto, è possibile che si verifichino problemi. Ad esempio, è possibile che venga visualizzato il seguente errore: "Il Debugger remoto di Visual Studio (MSVSMON. EXE) non dispone di privilegi sufficienti per eseguire il debug di questo processo." Se si esegue il debugger remoto come applicazione (non un servizio), è possibile che venga visualizzato l'errore [dell'account utente diverso.](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md)

### <a name="when-running-the-remote-debugger-as-a-service"></a>Quando si esegue il debugger remoto come servizioWhen running the remote debugger as a service

Quando si esegue il debugger remoto come servizio s, è consigliabile eseguirlo come amministratore per diversi motivi:When running the remote debugger as s service, we recommend running it as an administrator for several reasons:

- Il servizio debugger remoto consente solo connessioni da parte degli amministratori, pertanto **non** sono previsti nuovi rischi per la sicurezza introdotti eseguendolo come amministratore.

- Può impedire gli errori che si verificano quando l'utente di Visual Studio dispone di più diritti per eseguire il debug di un processo rispetto al debugger remoto stesso.

- Per semplificare l'installazione e la configurazione del debugger remoto.

Sebbene sia possibile eseguire il debug senza eseguire il debugger remoto come amministratore, esistono diversi requisiti per il corretto funzionamento e spesso richiedono passaggi di configurazione del servizio più avanzati.

- L'account utilizzato nel computer remoto deve disporre del **privilegio di accesso come servizio.** Vedere la procedura in "Per aggiungere l'accesso come servizio" nell'articolo di errore [Impossibile connettersi.](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md)

- L'account deve disporre dei diritti per eseguire il debug del processo di destinazione. Per ottenere questi diritti, è necessario eseguire il debugger remoto con lo stesso account del processo di cui eseguire il debug. L'alternativa più semplice consiste nell'eseguire il servizio come amministratore. 

- L'account deve essere in grado di connettersi nuovamente al computer di Visual Studio in rete. In un dominio, è più semplice connettersi di nuovo se il debugger remoto è in esecuzione con gli account di sistema locale o di servizio di rete incorporati o un account di dominio. Gli account predefiniti dispongono di privilegi di sicurezza elevati che possono rappresentare un rischio per la sicurezza.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Quando si esegue il debugger remoto come applicazione (modalità normale)

Se si sta tentando di connettersi al proprio processo non con privilegi elevati (ad esempio un'applicazione normale), non importa se si esegue il debugger remoto come amministratore.

Si desidera eseguire il debugger remoto come amministratore in diversi scenari:

- Si desidera connettersi ai processi in esecuzione come un altro utente (ad esempio durante il debug di IIS) o

- Si sta tentando di avviare un altro processo e il processo che si desidera avviare è un amministratore.

**Non** si desidera eseguire come amministratore se si desidera avviare i processi e il processo che si desidera avviare **non** deve essere un amministratore.

## <a name="see-also"></a>Vedere anche
- [Debug remoto](../debugger/remote-debugging.md)