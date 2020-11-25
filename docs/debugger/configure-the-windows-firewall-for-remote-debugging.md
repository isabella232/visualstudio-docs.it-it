---
title: Configurare Windows Firewall per il debug remoto | Microsoft Docs
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0fa5d60d7fe662cff31b54bf3a13c203f4b6d8c9
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/25/2020
ms.locfileid: "95970084"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configurare Windows Firewall per il debug remoto

In una rete protetta da Windows Firewall, è necessario configurare il firewall per consentire il debug remoto. Visual Studio e gli strumenti di debug remoto tentano di aprire le porte del firewall corrette durante l'installazione o l'avvio, ma potrebbe essere necessario aprire le porte o consentire le app manualmente.

In questo argomento viene descritto come configurare Windows Firewall per abilitare il debug remoto in Windows 10, 8/8.1 e 7; e i computer Windows Server 2012 R2, 2012 e 2008 R2. Visual Studio e il computer remoto non devono necessariamente eseguire lo stesso sistema operativo. Ad esempio, il computer di Visual Studio può eseguire Windows 10 e il computer remoto può eseguire Windows Server 2012 R2.

>[!NOTE]
>Le istruzioni per la configurazione di Windows Firewall differiscono leggermente per sistemi operativi diversi e per le versioni precedenti di Windows. Le impostazioni di Windows 8/8.1, Windows 10 e Windows Server 2012 usano l' *app* Word, mentre Windows 7 e windows Server 2008 usano il *programma* Word.

## <a name="configure-ports-for-remote-debugging"></a>Configurare le porte per il debug remoto

Visual Studio e il debugger remoto tentano di aprire le porte corrette durante l'installazione o l'avvio. Tuttavia, in alcuni scenari, ad esempio un firewall di terze parti, potrebbe essere necessario aprire le porte manualmente.

**Per aprire una porta:**

1. Nel menu **Start** di Windows cercare e aprire **Windows Firewall con sicurezza avanzata**. In Windows 10, si tratta di **Windows Defender Firewall con sicurezza avanzata**.

1. Per una nuova porta in ingresso, selezionare **Regole connessioni in entrata** e quindi selezionare **nuova regola**. Per una regola in uscita, selezionare invece **regole in uscita** .

1. Nella **creazione guidata nuova regola connessioni in ingresso** selezionare **porta** e quindi fare clic su **Avanti**.

1. Selezionare **TCP** o **UDP**, a seconda del numero di porta delle tabelle seguenti.

1. In **porte locali specifiche**, immettere un numero di porta dalle tabelle seguenti e fare clic su **Avanti**.

1. Selezionare **Consenti la connessione** e quindi fare clic su **Avanti**.

1. Selezionare uno o più tipi di rete da abilitare, incluso il tipo di rete per la connessione remota, quindi fare clic su **Avanti**.

1. Aggiungere un nome per la regola (ad esempio, **msvsmon**, **IIS** o **distribuzione Web**), quindi selezionare **fine**.

   La nuova regola dovrebbe essere visualizzata e selezionata nell'elenco **regole in ingresso** o **regole** in uscita.

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porte nel computer remoto che abilitano il debug remoto

Per il debug remoto, è necessario che le porte seguenti siano aperte nel computer remoto:

::: moniker range="vs-2017"

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|4022|In arrivo|TCP|Per Visual Studio 2017. Il numero di porta viene incrementato di 2 per ogni versione di Visual Studio. Per altre informazioni, vedere [assegnazioni di porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4023|In arrivo|TCP|Per Visual Studio 2017. Il numero di porta viene incrementato di 2 per ogni versione di Visual Studio. Questa porta viene usata solo per eseguire il debug remoto di un processo a 32 bit da una versione a 64 bit del debugger remoto. Per altre informazioni, vedere [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|In uscita|UDP|Opzionale Obbligatorio per l'individuazione del debugger remoto.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|4024|In arrivo|TCP|Per Visual Studio 2019. Il numero di porta viene incrementato di 2 per ogni versione di Visual Studio. Per altre informazioni, vedere [assegnazioni di porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|4025|In arrivo|TCP|Per Visual Studio 2019. Il numero di porta viene incrementato di 2 per ogni versione di Visual Studio. Questa porta viene usata solo per eseguire il debug remoto di un processo a 32 bit da una versione a 64 bit del debugger remoto. Per altre informazioni, vedere [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|In uscita|UDP|Opzionale Obbligatorio per l'individuazione del debugger remoto.|

::: moniker-end

Se si seleziona **Usa modalità di compatibilità gestita** in **strumenti**  >  **Opzioni**  >  **debug**, aprire queste porte aggiuntive del debugger remoto. La modalità di compatibilità gestita del debugger consente una versione legacy di Visual Studio 2010 del debugger.

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|135, 139, 445|In uscita|TCP|Obbligatorio.|
|137, 138|In uscita|UDP|Obbligatorio.|

Se i criteri di dominio richiedono che le comunicazioni di rete vengano eseguite tramite IPSec, è necessario aprire porte aggiuntive sia nei computer Visual Studio che in quelli remoti. Per eseguire il debug su un server Web IIS remoto, aprire la porta 80 nel computer remoto.

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|500, 4500|In uscita|UDP|Necessario se i criteri del dominio richiedono che la comunicazione di rete avvenga tramite IPSec.|
|80|In uscita|TCP|Richiesto per il debug di server Web.|

Per consentire app specifiche attraverso Windows Firewall, vedere [configurare il debug remoto tramite Windows Firewall](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurare il debug remoto tramite Windows Firewall

È possibile installare gli strumenti di debug remoto nel computer remoto o eseguirli da una cartella condivisa. In entrambi i casi, il firewall del computer remoto deve essere configurato correttamente.

In un computer remoto, gli strumenti di debug remoto sono disponibili in:

*\<Visual Studio installation directory\>\\\\ \\ Debugger remoto IDE Common7\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Consenti e configura il debugger remoto tramite Windows Firewall

1. Nel menu **Start** di Windows cercare e aprire **Windows Firewall** o **Windows Defender Firewall**.

1. Selezionare **Consenti un'app tramite Windows Firewall**.

1. Se il **debugger remoto** o **Visual Studio Remote Debugger** non viene visualizzato in **app e funzionalità consentite**, selezionare **Cambia impostazioni**, quindi selezionare **Consenti un'altra app**.

1. Se l'app del debugger remoto non è ancora elencata nella finestra di dialogo **Aggiungi un'app** , selezionare **Sfoglia** e passare a * \<Visual Studio installation directory\> \\ Common7 \\ IDE \\ Remote Debugger \\ \<x86*, *x64*, or *Appx*\> , a seconda dell'architettura appropriata per l'app. Selezionare *msvsmon.exe*, quindi selezionare **Aggiungi**.

1. Nell'elenco delle **app** selezionare il **debugger remoto** appena aggiunto. Selezionare **tipi di rete**, quindi selezionare uno o più tipi di rete, incluso il tipo di rete per la connessione remota.

1. Selezionare **Aggiungi** e quindi **OK**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Risolvere i problemi relativi alla connessione di debug remoto

Se non è possibile connettersi all'app con il debugger remoto, assicurarsi che le porte, i protocolli, i tipi di rete e le impostazioni dell'app del firewall per il debug remoto siano tutti corretti.

- Nel menu **Start** di Windows cercare e aprire **Windows Firewall** e selezionare **Consenti un'app tramite Windows Firewall**. Verificare che **debugger remoto** o **Visual Studio Remote Debugger** sia visualizzato nell'elenco **app e funzionalità consentite** con una casella di controllo selezionata e che siano selezionati i tipi di rete corretti. In caso contrario, [aggiungere le app e le impostazioni corrette](#configure-remote-debugging-through-windows-firewall).

- Nel menu **Start** di Windows cercare e aprire **Windows Firewall con sicurezza avanzata**. Verificare che **debugger remoto** o **Visual Studio Remote Debugger** venga visualizzato in **regole in ingresso** (e, facoltativamente, regole in **uscita**) con un'icona di segno di spunta verde e che tutte le impostazioni siano corrette.

  - Per visualizzare o modificare le impostazioni delle regole, fare clic con il pulsante destro del mouse sull'app **debugger remoto** nell'elenco e scegliere **Proprietà**. Utilizzare le schede **Proprietà** per abilitare o disabilitare la regola oppure modificare i numeri di porta, i protocolli o i tipi di rete.
  - Se l'app del debugger remoto non viene visualizzata nell'elenco regole, [aggiungere e configurare le porte corrette](#configure-ports-for-remote-debugging).

## <a name="see-also"></a>Vedi anche

- [Debug remoto](../debugger/remote-debugging.md)
- [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md)
