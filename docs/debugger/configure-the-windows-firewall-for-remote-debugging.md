---
title: Configurare Windows Firewall per debug remoto | Microsoft Docs
ms.date: 10/31/2018
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6daa7667c26e2394e86833f6d0ce633ea9a4a168
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56637334"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configurare Windows Firewall per debug remoto

In una rete protetta da Windows Firewall, il firewall deve essere configurato in modo da consentire il debug remoto. Visual Studio e gli strumenti di debug remoti tentano di aprire le porte del firewall corrette durante l'installazione o l'avvio, ma potrebbe essere anche necessario aprire porte o consentire alle App manualmente.

In questo argomento viene descritto come configurare Windows firewall per abilitare il debug remoto in Windows 10, 8/8.1 e 7. e i computer Windows Server 2012 R2, 2012 e 2008 R2. Di Visual Studio e un computer remoto non è necessario essere in esecuzione lo stesso sistema operativo. Ad esempio, il computer di Visual Studio può eseguire Windows 10 e il computer remoto può eseguire Windows Server 2012 R2.

>[!NOTE]
>Le istruzioni per configurare il firewall di Windows sono leggermente diverse in sistemi operativi diversi e versioni precedenti di Windows. Le impostazioni di Windows 8/8.1, Windows 10 e Windows Server 2012 usano la parola *app*, mentre Windows 7 e Windows Server 2008 utilizza la parola *programma*.

## <a name="configure-ports-for-remote-debugging"></a>Configurare le porte per il debug remoto

Visual Studio e il debugger remoto tenta di aprire le porte corrette durante l'installazione o l'avvio. In alcuni scenari, ad esempio un firewall di terze parti, tuttavia, potrebbe essere necessario aprire le porte manualmente.

**Per aprire una porta:**

1. In Windows **avviare** menu, cercare e aprire **Windows Firewall con sicurezza avanzata**. In Windows 10, si tratta **Windows Defender Firewall con sicurezza avanzata**.

1. Per una nuova porta in ingresso, selezionare **regole connessioni in entrata** e quindi selezionare **nuova regola**. Per una regola in uscita, selezionare **regole in uscita** invece.

1. Nel **nuova creazione guidata regola in ingresso**, selezionare **porta**e quindi selezionare **Next**.

1. Selezionare uno **TCP** oppure **UDP**, a seconda il numero di porta delle tabelle seguenti.

1. Sotto **porte locali specifiche**, immettere un numero di porta delle tabelle seguenti e selezionare **successivo**.

1. Selezionare **Consenti solo connessioni**, quindi selezionare **successivo**.

1. Selezionare uno o più tipi di rete da abilitare, incluso il tipo di rete per la connessione remota e quindi selezionare **successivo**.

1. Aggiungere un nome per la regola (ad esempio, **msvsmon**, **IIS**, o **distribuzione Web**), quindi selezionare **fine**.

   La nuova regola dovrebbe essere visualizzato e seleziona nel **regole connessioni in entrata** oppure **regole connessioni in uscita** elenco.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porte nel computer remoto che abilitano il debug remoto

Per eseguire il debug remoto, le porte seguenti devono essere aperte nel computer remoto:

|**Porte**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|4022|In ingresso|TCP|Per Visual Studio 2017. La porta numero aumenta di 2 per ogni versione di Visual Studio. Per altre informazioni, vedere [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|In ingresso|TCP|Per Visual Studio 2017. La porta numero aumenta di 2 per ogni versione di Visual Studio. Questa porta viene solo usata per remote debug di un processo a 32 bit da una versione a 64 bit del debugger remoto. Per altre informazioni, vedere [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|In uscita|UDP|(Facoltativo) Richiesto per remote debugger discovery.|

Se si seleziona **utilizza modalità di compatibilità gestita** sotto **Tools** > **opzioni** > **debug**, aprire Queste porte aggiuntivi del debugger remoto. Modalità di compatibilità gestita debugger consente una legacy, la versione di Visual Studio 2010 del debugger.

|**Porte**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|135, 139, 445|In uscita|TCP|Obbligatorio.|
|137, 138|In uscita|UDP|Obbligatorio.|

Se i criteri del dominio richiedono la comunicazione di rete deve essere eseguita tramite IPSec, è necessario aprire porte aggiuntive sul computer remoto e Visual Studio. Per eseguire il debug in un server web IIS remoto, aprire la porta 80 sul computer remoto.

|**Porte**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|500, 4500|In uscita|UDP|Necessario se i criteri del dominio richiedono che la comunicazione di rete avvenga tramite IPSec.|
|80|In uscita|TCP|Richiesto per il debug di server Web.|

Per autorizzare App specifiche attraverso il firewall di Windows, vedere [Configura debug remoto attraverso Windows Firewall](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurare il debug remoto attraverso il firewall di Windows

È possibile installare gli strumenti di debug remoti nel computer remoto o eseguiti da una cartella condivisa. In entrambi i casi, il firewall del computer remoto deve essere configurato correttamente.

In un computer remoto, gli strumenti di debug remoti sono:

*\<Directory di installazione di Visual Studio\>\\Common7\\IDE\\Remote Debugger\\\<x86*, *x64*, o  *AppX*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Consentire e configurare il debugger remoto attraverso Windows Firewall

1. In Windows **avviare** menu, cercare e aprire **Windows Firewall**, o **Windows Defender Firewall**.

1. Selezionare **consentire a un'app tramite Windows Firewall**.

1.  Se **Remote Debugger** oppure **Visual Studio Remote Debugger** non viene visualizzato sotto **App e funzionalità consentite**, selezionare **modificare impostazioni**, quindi selezionare **Consenti un'altra app**.

1.  Se l'app del debugger remoto non è ancora presente nel **aggiungere un'app** finestra di dialogo, seleziona **Sfoglia**e passare a  *\<directory di installazione di Visual Studio\> \\Common7\\IDE\\Debugger remoto\\\<x86*, *x64*, o *Appx* \> , a seconda dell'architettura appropriata per l'app. Selezionare *msvsmon.exe*, quindi selezionare **Add**.

1.  Nel **Apps** elenco, selezionare la **Debugger remoto** appena aggiunto. Selezionare **tipi di rete**e quindi selezionare uno o più tipi di rete, incluso il tipo di rete per la connessione remota.

1.  Selezionare **Add**, quindi selezionare **OK**.

## <a name="troubleshooting"></a>Risolvere i problemi di connessione al debug remoto

Se è possibile collegare all'App con il debugger remoto, assicurarsi che le porte del firewall debug remoto, i protocolli, i tipi di rete e le impostazioni dell'app siano corrette.

- Nella finestra di Windows **avviare** menu, cercare e aprire **Windows Firewall**e selezionare **consentono a un'app tramite Windows Firewall**. Assicurarsi che **Remote Debugger** o **Visual Studio Remote Debugger** viene visualizzato nei **App e funzionalità consentite** elenco con una casella di controllo selezionata e i tipi di rete corrette sono selezionato. In caso contrario, [aggiungere le impostazioni e delle App corrette](#configure-remote-debugging-through-windows-firewall).

- Nella finestra di Windows **avviare** menu, cercare e aprire **Windows Firewall con sicurezza avanzata**. Assicurarsi che **Remote Debugger** oppure **Visual Studio Remote Debugger** viene visualizzato sotto **regole in entrata** (e, facoltativamente, **regole connessioni in uscita**) con un'icona di segno di spunta verde e che tutte le impostazioni siano corrette.

  - Per visualizzare o modificare le impostazioni delle regole, fare doppio clic il **Remote Debugger** app nell'elenco e selezionare **proprietà**. Usare la **proprietà** schede per abilitare o disabilitare la regola oppure modificare la porta numeri, protocolli o tipi di rete.
  - Se l'app del debugger remoto non compare nell'elenco delle regole [aggiungere e configurare le porte appropriate](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Vedere anche

- [Debug remoto](../debugger/remote-debugging.md)
- [Assegnazioni delle porte di Visual Studio remote debugger](../debugger/remote-debugger-port-assignments.md)
