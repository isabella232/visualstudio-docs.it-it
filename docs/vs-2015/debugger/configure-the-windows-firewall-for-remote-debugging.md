---
title: Configurare la Windows Firewall per il debug remoto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 66e3230a-d195-4473-bbce-8ca198516014
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f232446ed699bd7cc034e4b6d6148b665830cf2d
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85535525"
---
# <a name="configure-the-windows-firewall-for-remote-debugging"></a>Configurare Windows Firewall per il debug remoto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo argomento illustra come configurare il firewall per abilitare il debug remoto nei computer che eseguono i sistemi operativi seguenti:  
  
- Windows 7  
  
- Windows 8/8.1  
  
- Windows 10  
  
- Windows Server 2008 (R2)  
  
- Windows Server 2012  
  
- Windows Server 2012 R2  
  
  Se la rete su cui si esegue il debug non è protetta da un firewall, questa configurazione non è necessaria. In caso contrario, è necessario modificare la configurazione del firewall sia nel computer che ospita Visual Studio, sia nel computer remoto di cui si esegue il debug.  
  
  **IPSec** : se la rete richiede che le comunicazioni avvengano tramite IPSec, è necessario aprire porte aggiuntive sia sul computer host di Visual Studio sia sul computer remoto.  
  
  **Server Web** : se si esegue il debug di un server Web remoto, è necessario aprire una porta supplementare sul computer remoto.  
  
  Tenere presente che non è necessario che entrambi i computer eseguano lo stesso sistema operativo. Ad esempio, il computer di Visual Studio può eseguire Windows 10 e il computer remoto può eseguire Windows Server 2012 R2.  
  
## <a name="to-configure-windows-firewall-on-the-visual-studio-computer"></a>Per configurare Windows Firewall nel computer di Visual Studio  
 Le istruzioni per configurare Windows firewall sono leggermente diverse a seconda del sistema operativo. In Windows 7 o Windows Server 2008 viene usato il termine **programma** , mentre in Windows 8/8.1, Windows 10 e Windows Server 2012, viene usato il termine **app** .  Nei passaggi seguenti si userà il termine **app**.  
  
1. Aprire la pagina di Windows Firewall. A questo scopo digitare **Windows Firewall** nella casella di ricerca del menu **Start**.  
  
2. Fai clic su **Consenti app o funzionalità attraverso Windows Firewall**.  
  
3. Nell'elenco **App e funzionalità consentite** cercare **Visual Studio Remote Debugger Discovery**. Se è elencato, assicurarsi che sia selezionato e che siano selezionati anche uno o più tipi di rete.  
  
4. Se **Visual Studio Remote Debugger Discovery** non è incluso nell'elenco, fare clic su **Consenti un'altra app**. Se non viene ancora visualizzato nella finestra **Aggiungi un'app** , fare clic su **Sfoglia** e passare a ** \<Visual Studio installation directory> \Common7\IDE\Remote debugger**. Individuare la cartella appropriata per l'applicazione (x86, x64, Appx) e quindi selezionare **msvsmon.exe**. Fare quindi clic su **Aggiungi**.  
  
5. Nell'elenco **App e funzionalità consentite** selezionare **Visual Studio Remote Debugging Monitor**. Selezionare uno o più tipi di rete (**di dominio, casa/lavoro (privata), pubblica**) con cui si vuole che Remote Debugging Monitor comunichi. Tra i tipi deve essere inclusa la rete a cui è connesso il computer di Visual Studio.  
  
## <a name="to-open-a-port-on-the-visual-studio-computer-to-enable-discovery"></a>Per aprire una porta nel computer di Visual Studio per abilitare l'individuazione  
 È necessario consentire la porta UDP 3702 in ingresso per abilitare l'individuazione dei computer che eseguono il debugger remoto. Per aggiungerla, vedere la procedura per configurare le porte in un firewall.  
  
## <a name="to-configure-the-windows-firewall-of-the-remote-computer-for-remote-debugging"></a>Per configurare il firewall di Windows nel computer remoto per il debug remoto  
 I componenti di debug remoto possono essere installati nel computer remoto o eseguiti da una directory condivisa. Il firewall del computer remoto deve essere configurato in entrambi i casi. I componenti di debug remoto si trovano in:  
  
 **\<Visual Studio installation directory>Debugger \Common7\IDE\Remote**  
  
 Le istruzioni per configurare Windows firewall sono leggermente diverse a seconda del sistema operativo. In Windows 7 o Windows Server 2008 viene usato il termine **programma** , mentre in Windows 8/8.1, Windows 10 e Windows Server 2012, viene usato il termine **app** .  Nei passaggi seguenti si userà il termine **app**.  
  
1. Aprire la pagina di Windows Firewall. A questo scopo digitare **Windows Firewall** nella casella di ricerca del menu **Start**.  
  
2. Fai clic su **Consenti app o funzionalità attraverso Windows Firewall**.  
  
3. Nell'elenco **App e funzionalità consentite** cercare **Visual Studio Remote Debugging Monitor**. Se è elencato, assicurarsi che sia selezionato e che siano selezionati anche uno o più tipi di rete.  
  
4. Se **Visual Studio Remote Debugging Monitor** non è incluso nell'elenco, fare clic su **Consenti un'altra app**. Se non viene ancora visualizzato nella **finestra Aggiungi un'app**, fare clic su **Sfoglia** e passare a ** \<Visual Studio installation directory> \Common7\IDE\Remote debugger**. Individuare la cartella appropriata per l'applicazione (x86, x64, Appx) e quindi selezionare **msvsmon.exe**. Fare quindi clic su **Aggiungi**.  
  
5. Nell'elenco **App consentite** selezionare **Visual Studio Remote Debugging Monitor**. Selezionare uno o più tipi di rete (**di dominio, casa/lavoro (privata), pubblica**) con cui si vuole che Remote Debugging Monitor comunichi. Tra i tipi deve essere inclusa la rete a cui è connesso il computer di Visual Studio.  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging"></a>Porte nel computer remoto che abilitano il debug remoto  
  
|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|  
|-|-|-|-|
|3702|In uscita|UDP|Richiesto per Remote Debugger Discovery.|  
|4020||TCP|Per Visual Studio 2015. Il numero di porta aumenta di 2 per ogni versione di Visual Studio. Per altre informazioni, vedere Assegnazioni di porta per Visual Studio Remote Debugger.|  
|4021||TCP|Per Visual Studio 2015. Il numero di porta aumenta di 2 per ogni versione di Visual Studio. Per altre informazioni, vedere Assegnazioni di porta per Visual Studio Remote Debugger.|  
  
## <a name="ports-on-the-remote-computer-that-enable-remote-debugging-with-managed-or-native-compatibility-mode"></a>Porte nel computer remoto che abilitano il debug remoto con la modalità di compatibilità nativa o gestita  
  
|**Ports**|**In ingresso/in uscita**|**Protocollo**|**Descrizione**|  
|-|-|-|-|  
|135, 139, 445|In uscita|TCP|Obbligatorio.|  
|137, 138|In uscita|UDP|Obbligatorio.|  
|500, 4500|In uscita|UDP|Necessario se i criteri del dominio richiedono che la comunicazione di rete avvenga tramite IPSec.|  
|80|In uscita|TCP|Richiesto per il debug di server Web.|  
  
## <a name="how-to-configure-ports-in-windows-firewall"></a>Come configurare le porte in Windows Firewall  
  
1. Nel menu **Start** cercare **Windows Firewall con sicurezza avanzata**.  
  
2. Fare clic su **Regole connessioni in entrata** o **Regole connessioni in uscita** , quindi fare clic su **Nuova regola** nell'elenco **Azioni** .  
  
3. Nella pagina **tipo di regola** selezionare **porta** e quindi fare clic su **Avanti**.  
  
4. Nella pagina **Protocollo e porte** selezionare il protocollo di porta (TCP o UDP). Selezionare **Porte locali specifiche** e immettere uno o più numeri di porta da abilitare per il protocollo. Separare i numeri con virgole. Quindi fare clic su **Next**.  
  
5. Nella pagina **Azione** selezionare **Consenti la connessione** e quindi fare clic su **Avanti**.  
  
6. Nella pagina **Profilo** selezionare uno o più tipi di rete da abilitare per la porta. Il tipo selezionato deve includere la rete a cui è connesso il computer remoto. Quindi fare clic su **Next**.  
  
7. Nella pagina **Nome** digitare un nome per la regola e quindi fare clic su **Fine**.  
  
8. Verrà visualizzata la nuova regola nell'elenco **regole in ingresso** o **regole** in uscita.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug remoto](../debugger/remote-debugging.md)
