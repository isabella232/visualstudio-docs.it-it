---
title: Remote Debug degli errori e risoluzione dei problemi | Microsoft Docs
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
ms.openlocfilehash: 078551111223f11b38f3192075caa9ddfabaf18c
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043339"
---
# <a name="remote-debugging-errors-and-troubleshooting"></a>Errori e risoluzione dei problemi relativi al debug remoto

Potrebbe riscontrare gli errori seguenti durante il tentativo di eseguire il debug remoto.

- [Errore: Non è possibile eseguire automaticamente l'istruzione nel server](../debugger/error-unable-to-automatically-step-into-the-server.md)

- [Errore: Microsoft Visual Studio Remote Debugging Monitor (MSVSMON.EXE) non sembra essere in esecuzione sul computer remoto.](/visualstudio/debugger/error-remote-debugging-monitor-msvsmon-exe-does-not-appear-to-be-running)

- [Unable to Connect to the Microsoft Visual Studio Remote Debugging Monitor](../debugger/unable-to-connect-to-the-microsoft-visual-studio-remote-debugging-monitor.md)

- [Errore: Il computer remoto non viene visualizzato in una finestra di dialogo Connessioni remote](../debugger/error-remote-machine-does-not-appear-in-a-remote-connections-dialog.md)

## <a name="run-the-remote-debugger-as-an-administrator"></a>Eseguire il debugger remoto come amministratore

Potrebbero riscontrare problemi se non si esegue il debugger remoto come amministratore. Ad esempio, si verifichi l'errore seguente: "Di Visual Studio Remote Debugger (MSVSMON. Con estensione EXE) ha privilegi sufficienti per il debug del processo". Se si esegue il debugger remoto come un'applicazione (non un servizio), può vedere le [account utente diverso](error-the-microsoft-visual-studio-remote-debugging-monitor-on-the-remote-computer-is-running-as-a-different-user.md) errore.

### <a name="when-running-the-remote-debugger-as-a-service"></a>Quando si esegue il debugger remoto come servizio

Quando si esegue il debugger remoto come servizio s, è consigliabile eseguirlo come amministratore per diversi motivi:

- Il servizio debugger remoto consente solo le connessioni da parte degli amministratori, quindi esistono **alcun** nuovi rischi per la sicurezza dovuti a eseguirlo come amministratore.

- È possibile evitare gli errori di risultati quando l'utente di Visual Studio ha più diritti per eseguire il debug di un processo del debugger remoto stesso.

- Per semplificare l'installazione e configurazione del debugger remoto.

Sebbene sia possibile eseguire il debug senza eseguire il debugger remoto come amministratore, esistono diversi requisiti per eseguire questa operazione in modo corretto e spesso richiedono passaggi di configurazione più avanzati del servizio.

- L'account in uso nel computer remoto deve avere il **accesso come servizio** privilegio. Vedere la sezione "Per aggiungere accesso come servizio" nel [non è possibile connettersi nuovamente](error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer.md) articolo di errore.

- L'account deve disporre dei diritti per eseguire il debug del processo di destinazione. Per ottenere questi diritti, è necessario eseguire il debugger remoto con lo stesso account del processo da sottoporre a debug. (L'alternativa più semplice consiste nell'eseguire il servizio come amministratore). 

- L'account deve essere in grado di connettersi nuovamente per (vale a dire, eseguire l'autenticazione con) nel computer di Visual Studio in rete. In un dominio, è più semplice connettersi nuovamente se il debugger remoto viene eseguito con l'account sistema locale o servizio di rete predefiniti o un account di dominio. Gli account predefiniti sono elevati privilegi di sicurezza che possono implicare problemi di sicurezza.

### <a name="when-running-the-remote-debugger-as-an-application-normal-mode"></a>Quando si esegue il debugger remoto come un'applicazione (modalità normale)

Se si sta tentando di connettersi al proprio processo senza privilegi elevati (ad esempio una normale applicazione), non è importante se si esegue il debugger remoto come amministratore.

Si vuole eseguire il debugger remoto come amministratore in diversi scenari:

- Si desidera connettersi a processi in esecuzione come utente diverso (ad esempio, quando il debug di IIS), o

- Si sta tentando di avviare un altro processo e il processo di cui che si vuole avviare sia un amministratore.

È effettuare **non** da eseguire come amministratore se si vuole avviare i processi e il processo di cui si vuole avviare deve **non** sia un amministratore.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)