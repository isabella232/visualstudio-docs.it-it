---
description: Questo errore indica che il servizio debugger remoto è in esecuzione con un account utente che non può eseguire l'autenticazione quando tenta di connettersi al computer da cui si esegue il debug.
title: Il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer
titleSuffix: ''
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 86458f6e892187e74c59b40c668148de0280f7e14d199165585409a884095e1c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420079"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Errore: il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer
Questo errore indica che il servizio debugger remoto è in esecuzione con un account utente che non può eseguire l'autenticazione quando tenta di connettersi al computer da cui si esegue il debug. Questo errore può verificarsi quando si esegue il debug remoto usando il motore di debug legacy e il debugger remoto viene eseguito come servizio.

 Nella tabella riportata di seguito sono indicati gli account in grado di accedere al computer:

|Scenario|Account LocalSystem|Account di dominio|Account locali con lo stesso nome utente e la stessa password in entrambi i computer|
|-|-|-|-|
|Entrambi i computer nello stesso dominio|Sì|Sì|Sì|
|Entrambi i computer in domini con trust bidirezionale|No|No|Sì|
|Uno o entrambi i computer in un gruppo di lavoro|No|No|Sì|
|Computer in domini diversi|No|No|Sì|

 Inoltre:

- L'account utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio deve essere un account amministrativo nel computer remoto in modo da poter eseguire il debug di qualsiasi processo.

- È anche necessario assegnare a questo account il privilegio `Log on as a service` nel computer remoto che utilizza lo strumento di amministrazione **Criteri di sicurezza locali**.

- Se si intende utilizzare un accesso al computer con account locale, è necessario eseguire il servizio Debugger remoto di Visual Studio con un account locale.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Assicurarsi che il servizio Debugger remoto di Visual Studio sia configurato in modo corretto nel computer remoto. Per altre informazioni, vedere [Debug remoto](../debugger/remote-debugging.md).

2. Eseguire il servizio Debugger remoto utilizzando un account in grado di accedere al computer host del debugger, come indicato nella tabella precedente.

### <a name="to-add-log-on-as-a-service-privilege"></a>Per aggiungere un privilegio "Accesso come servizio"

1. Nel menu **Start** scegliere **Pannello di controllo**.

2. Se necessario, nel Pannello di controllo scegliere **Passa alla visualizzazione classica**.

3. Fare doppio clic su **Strumenti di amministrazione**.

4. Nella finestra Strumenti di amministrazione fare doppio clic su **Criteri di sicurezza locali**.

5. Nella finestra **Impostazioni sicurezza locale** espandere la cartella **Criteri locali**.

6. Scegliere **Assegnazione diritti utente**.

7. Nella colonna **Criteri** fare doppio clic su **Accedi come servizio** per visualizzare le assegnazioni dei criteri di gruppo locali correnti nella finestra di dialogo **Accedi come servizio**.

8. Per aggiungere nuovi utenti, fare clic sul pulsante **Aggiungi utente o gruppo**.

9. Al termine, scegliere **OK**.

### <a name="to-work-around-this-error"></a>Per risolvere il problema

- Eseguire Remote Debugging Monitor come applicazione anziché come servizio.

## <a name="see-also"></a>Vedi anche
- [Errori di debug remoto e risoluzione dei problemi](../debugger/remote-debugging-errors-and-troubleshooting.md)
- [Debug remoto](../debugger/remote-debugging.md)
