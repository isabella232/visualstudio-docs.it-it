---
title: Configurare Windows firewall per il debug remoto | Microsoft Docs
description: Configurare Windows firewall per il debug remoto. Configurare le porte per il debug remoto. Risolvere i problemi relativi alla connessione di debug remoto.
ms.custom: SEO-VS-2020
ms.date: 10/31/2018
ms.topic: how-to
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: ae4a3ea65c9db713bcbdb9a9d9b1027767614b21
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122031406"
---
# <a name="configure-windows-firewall-for-remote-debugging"></a>Configurare Windows firewall per il debug remoto

In una rete protetta da Windows, il firewall deve essere configurato per consentire il debug remoto. Visual Studio e gli strumenti di debug remoto tentano di aprire le porte del firewall corrette durante l'installazione o l'avvio, ma potrebbe anche essere necessario aprire le porte o consentire le app manualmente.

Questo argomento descrive come configurare il firewall Windows per abilitare il debug remoto in Windows 10, 8/8.1 e 7; e Windows Server 2012 computer R2, 2012 e 2008 R2. Il Visual Studio e il computer remoto non devono eseguire lo stesso sistema operativo. Ad esempio, il computer di Visual Studio può eseguire Windows 10 e il computer remoto può eseguire Windows Server 2012 R2.

>[!NOTE]
>Le istruzioni per la configurazione del firewall Windows sono leggermente diverse nei diversi sistemi operativi e nelle versioni precedenti di Windows. Windows 8/8.1, Windows 10 e Windows Server 2012 usano la parola *app*, mentre Windows 7 e Windows Server 2008 usano la parola *programma*.

## <a name="configure-ports-for-remote-debugging"></a>Configurare le porte per il debug remoto

Visual Studio e il debugger remoto tentano di aprire le porte corrette durante l'installazione o l'avvio. Tuttavia, in alcuni scenari, ad esempio un firewall di terze parti, potrebbe essere necessario aprire le porte manualmente.

**Per aprire una porta:**

1. Nel menu **Windows Start** cercare e aprire Windows Firewall con **sicurezza avanzata.** In Windows 10, questo è **Windows Defender firewall con sicurezza avanzata.**

1. Per una nuova porta in ingresso, selezionare **Regole in ingresso e** quindi nuova **regola.** Per una regola in uscita, selezionare **invece Regole in** uscita.

1. Nella **Creazione guidata nuova regola connessioni in entrata** selezionare **Porta** e quindi selezionare **Avanti.**

1. Selezionare **TCP o** **UDP,** a seconda del numero di porta delle tabelle seguenti.

1. In **Porte locali specifiche** immettere un numero di porta dalle tabelle seguenti e selezionare **Avanti.**

1. Selezionare **Consenti connessione** e quindi Selezionare **Avanti.**

1. Selezionare uno o più tipi di rete da abilitare, incluso il tipo di rete per la connessione remota, quindi selezionare **Avanti.**

1. Aggiungere un nome per la regola , ad esempio **msvsmon**, **IIS** **o Distribuzione Web**, quindi selezionare **Fine**.

   La nuova regola verrà visualizzata e selezionata **nell'elenco Regole in ingresso** o Regole **in** uscita .

**Per aprire una porta tramite PowerShell:**

Per Windows firewall, è possibile usare i comandi di PowerShell, ad [esempio New-NetFirewallRule](/powershell/module/netsecurity/new-netfirewallrule?view=win10-ps).

Nell'esempio seguente viene aperta la porta 4024 per il debugger remoto nel computer remoto. Il percorso da usare potrebbe essere diverso.

```ps
New-NetFirewallRule -DisplayName "msvsmon" -Direction Inbound -Program "Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Remote Debugger\x86\msvsmon.exe" -LocalPort 4024 -Protocol TCP -Authentication Required -Action Allow
```

### <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porte nel computer remoto che abilitano il debug remoto

Per il debug remoto, nel computer remoto devono essere aperte le porte seguenti:

::: moniker range="vs-2017"

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|4022|In arrivo|TCP|Per Visual Studio 2017. Il numero di porta incrementa di 2 per ogni Visual Studio versione. Per altre informazioni, vedere Visual Studio [porte del debugger remoto.](../debugger/remote-debugger-port-assignments.md)|
|4023|In arrivo|TCP|Per Visual Studio 2017. Il numero di porta incrementa di 2 per ogni Visual Studio versione. Questa porta viene usata solo per eseguire il debug remoto di un processo a 32 bit da una versione a 64 bit del debugger remoto. Per altre informazioni, vedere [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|In uscita|UDP|(Facoltativo) Obbligatorio per l'individuazione del debugger remoto.|

::: moniker-end

::: moniker range=">= vs-2019"

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|4024|In arrivo|TCP|Per Visual Studio 2019. Il numero di porta incrementa di 2 per ogni Visual Studio versione. Per altre informazioni, vedere Visual Studio [porte del debugger remoto.](../debugger/remote-debugger-port-assignments.md)|
|4025|In arrivo|TCP|Per Visual Studio 2019. Il numero di porta incrementa di 2 per ogni Visual Studio versione. Questa porta viene usata solo per eseguire il debug remoto di un processo a 32 bit da una versione a 64 bit del debugger remoto. Per altre informazioni, vedere [Assegnazioni delle porte del debugger remoto di Visual Studio](../debugger/remote-debugger-port-assignments.md).|
|3702|In uscita|UDP|(Facoltativo) Obbligatorio per l'individuazione del debugger remoto.|

::: moniker-end

Se si seleziona Usa **modalità di compatibilità gestita** in **Strumenti**  >  **Opzioni**  >  **debug**, aprire queste porte aggiuntive del debugger remoto. La modalità di compatibilità gestita dal debugger abilita una versione legacy Visual Studio 2010 del debugger.

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|135, 139, 445|In uscita|TCP|Obbligatorio.|
|137, 138|In uscita|UDP|Obbligatorio.|

Se i criteri di dominio richiedono che la comunicazione di rete sia eseguita tramite IPSec, è necessario aprire porte aggiuntive sia nel Visual Studio che nei computer remoti. Per eseguire il debug in un server Web IIS remoto, aprire la porta 80 nel computer remoto.

|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|
|-|-|-|-|
|500, 4500|In uscita|UDP|Necessario se i criteri del dominio richiedono che la comunicazione di rete avvenga tramite IPSec.|
|80|In uscita|TCP|Richiesto per il debug di server Web.|

Per consentire app specifiche tramite il firewall Windows remoto, vedere Configurare il [debug remoto tramite Windows Firewall](#configure-remote-debugging-through-windows-firewall).

## <a name="configure-remote-debugging-through-windows-firewall"></a>Configurare il debug remoto tramite Windows firewall

È possibile installare gli strumenti di debug remoto nel computer remoto o eseguirli da una cartella condivisa. In entrambi i casi, il firewall del computer remoto deve essere configurato correttamente.

In un computer remoto, gli strumenti di debug remoto sono in:

*\<Visual Studio installation directory\>\\Debugger remoto \\ dell'IDE Common7 \\\\\<x86*, *x64*, or *Appx*\>

### <a name="allow-and-configure-the-remote-debugger-through-windows-firewall"></a>Consentire e configurare il debugger remoto tramite Windows firewall

1. Nel Windows **Start** cercare e aprire Windows **firewall** o **Windows Defender Firewall**.

1. Selezionare **Consenti un'app tramite Windows firewall.**

1. Se **Debugger remoto o** **Visual Studio Remote Debugger** non viene visualizzato **in** App e funzionalità consentite, selezionare Modifica impostazioni **e** quindi selezionare **Consenti un'altra app.**

1. Se l'app debugger remoto non è ancora elencata nella finestra di dialogo Aggiungi **un'app,** selezionare Sfoglia e passare a * Debugger remoto IDE Common7 , a seconda dell'architettura appropriata per \<Visual Studio installation directory\> \\ \\ \\ \\ \<x86*, *x64*, or *Appx*\> l'app. Selezionare *msvsmon.exe* e quindi **aggiungi**.

1. **Nell'elenco** App selezionare il **debugger** remoto appena aggiunto. Selezionare **Tipi di** rete e quindi selezionare uno o più tipi di rete, incluso il tipo di rete per la connessione remota.

1. Selezionare **Aggiungi** e quindi **OK**.

## <a name="troubleshoot-the-remote-debugging-connection"></a><a name="troubleshooting"></a>Risolvere i problemi relativi alla connessione di debug remoto

Se non è possibile connettersi all'app con il debugger remoto, assicurarsi che le porte, i protocolli, i tipi di rete e le impostazioni dell'app del firewall di debug remoto siano tutti corretti.

- Nel menu Windows **Start** cercare e aprire Windows **Firewall** e selezionare Consenti un'app tramite Windows **Firewall**. Assicurarsi che **Remote Debugger** **o Visual Studio Remote Debugger** nell'elenco **App** e funzionalità consentite con una casella di controllo selezionata e che siano selezionati i tipi di rete corretti. In caso contrario, [aggiungere le app e le impostazioni corrette.](#configure-remote-debugging-through-windows-firewall)

- Nel menu Windows **Start** cercare e aprire Windows **Firewall con sicurezza avanzata**. Assicurarsi che **Debugger remoto** **o Visual Studio Remote Debugger** in Regole **in** ingresso (e, facoltativamente, Regole in uscita) con un'icona a forma di segno di spunta verde e che tutte le impostazioni siano corrette. 

  - Per visualizzare o modificare le impostazioni delle regole, fare clic con il pulsante destro del mouse sull'app **Debugger** remoto nell'elenco e scegliere **Proprietà**. Usare le **schede** Proprietà per abilitare o disabilitare la regola o modificare i numeri di porta, i protocolli o i tipi di rete.
  - Se l'app debugger remoto non viene visualizzata nell'elenco delle regole, [aggiungere e configurare le porte corrette.](#configure-ports-for-remote-debugging)

## <a name="see-also"></a>Vedi anche

- [Debug remoto](../debugger/remote-debugging.md)
- [Visual Studio di porta del debugger remoto](../debugger/remote-debugger-port-assignments.md)
