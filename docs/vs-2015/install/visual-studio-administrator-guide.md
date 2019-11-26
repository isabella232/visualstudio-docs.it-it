---
title: Guida dell'amministratore di Visual Studio | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
helpviewer_keywords:
- network installation, Visual Studio
- administrator guide, Visual Studio
- installing Visual Studio, administrator guide
ms.assetid: 4af353f5-6cfd-4ebe-bcfb-f42306e451a0
caps.latest.revision: 76
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a59f9f2cb2548d6d40670832e66d4df5c83680df
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295917"
---
# <a name="visual-studio-administrator-guide"></a>Visual Studio Administrator Guide
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere la [Guida dell'amministratore di Visual Studio](/visualstudio/install/visual-studio-administrator-guide).

È possibile distribuire Visual Studio 2015 su una rete purché ogni computer di destinazione soddisfi i [requisiti minimi di installazione](https://visualstudio.microsoft.com/vs/older-downloads/). È possibile creare una condivisione di rete eseguendo il file di installazione con l'opzione /layout, come descritto nella pagina [Creare un'installazione offline di Visual Studio](../install/create-an-offline-installation-of-visual-studio.md), quindi copiarla dal computer locale alla condivisione di rete. Se si usa un file ISO, è possibile montare l'immagine ISO e condividerla o copiare l'immagine ISO in una condivisione di rete.  
  
 Si noti che le installazioni da una condivisione di rete "ricordano" la posizione di origine da cui provengono. Ciò significa che per il ripristino di un computer client potrebbe essere necessario tornare alla condivisione di rete client da cui è stato installato in origine il client. Scegliere con attenzione il percorso di rete in modo che si allinei alla durata di esecuzione dei client di Visual Studio 2015 prevista all'interno dell'organizzazione.  
  
## <a name="detection-and-servicing-keys"></a>Chiavi di rilevamento e di manutenzione  
 Le sottochiavi di rilevamento nel Registro di sistema consentono di determinare se un prodotto di Visual Studio è già installato in un computer. Usare queste chiavi di rilevamento in una distribuzione automatizzata per determinare se è necessario procedere con l'installazione.  Vedere [rilevamento dei requisiti di sistema](../extensibility/internals/detecting-system-requirements.md)[rilevamento dei requisiti di sistema].  
  
## <a name="avoiding-reboots"></a>Evitare i riavvii  
 È possibile ridurre i riavvii assicurandosi di soddisfare i requisiti appropriati di Visual Studio prima di distribuire Visual Studio. Per il .NET Framework, potrebbe essere necessario riavviare i computer che eseguono Windows 8 se si distribuisce Visual Studio 2015 senza prima installare il .NET Framework 4,6.  
  
 Per l'emulazione di dispositivi Windows e Android può essere necessario riavviare i computer se la funzionalità Hyper-V di Windows non è già attivata. Per lo sviluppo Web può essere necessario riavviare i computer se la funzionalità Server Web di Windows non è già attivata. Per lo sviluppo di Office può essere necessario riavviare i computer se la funzionalità Windows Identity Foundation di Windows non è già attivata. riavviare i computer se la funzionalità Server Web di Windows non è già attivata. Per lo sviluppo di Office può essere necessario riavviare i computer se la funzionalità Windows Identity Foundation di Windows non è già attivata. Per altre informazioni su come automatizzare il rilevamento e l'installazione delle funzionalità di Windows, vedere la pagina relativa all' [installazione di un ruolo del server su un server che esegue un'installazione Server Core di Windows Server 2008 R2](https://technet.microsoft.com/library/ee441260(v=ws.10).aspx).  
  
## <a name="error-return-codes"></a>Codici di errore restituiti  
 La tabella seguente riporta codici di errore importanti. È possibile usare questi codici di errore nell'automazione per decidere se è necessario un riavvio e se l'installazione è riuscita. Se si riceve un codice di errore, prendere in considerazione le procedure di risoluzione dei problemi nella pagina [installare Visual Studio](../install/install-visual-studio-2015.md) .  
  
|Stato dell'installazione|Riavvio non richiesto|Riavvio richiesto|Descrizione|  
|------------------|--------------------------|----------------------|-----------------|  
|Success|0x00000000 [0]|0x00000bc2 [3010]|Installazione riuscita.|  
|Blocco|0x80044000 [-2147205120]|0x8004C000 [-2147172352]|Se l'unico blocco da segnalare è "Riavvio in sospeso", il valore restituito è il valore Incompleto-Richiesto riavvio (0x80048bc7).|  
|Cancel|0x00000642 [1602]|0x80048642 [-2147187134]|Quando viene restituito il valore di riavvio, il codice restituito è 1602.|  
|Incompleto-Richiesto riavvio|N/D|0x80048bc7 [-2147185721]|Per completare l'installazione, è necessario riavviare.|  
|Errore|0x00000643 [1603]|0x80048643 [-2147187133]|Quando viene restituito il valore di riavvio, il codice restituito è 1603.|  
  
## <a name="interactive-administrator-installer"></a>Programma di installazione interattivo per l'amministratore  
 Se si sta creando un programma di installazione interattivo sopra l'installazione di Visual Studio, è possibile visualizzare lo stato di avanzamento dal programma di installazione di Visual Studio. Il programma di installazione di Visual Studio 2015 è basato sulla tecnologia chainer open source di Windows Installer XML (WiX), nota anche come "masterizzazione". La tecnologia di masterizzazione supporta due protocolli di comunicazione: netfx4 e masterizzazione. Per un breve riferimento, vedere la descrizione dell'attributo del protocollo nella documentazione per l'elemento ExePackage in [wixtoolset.org](https://wixtoolset.org/). Per l'integrazione potrebbe essere necessaria una revisione dell'implementazione open source di WiX di questo attributo del protocollo.  
  
## <a name="controlling-what-is-installed"></a>Controllo dei componenti installati  
 Se si vuole controllare cosa può installare l'utente finale esistono due opzioni: l'installazione del file dell'amministratore e le opzioni da riga di comando. Selezionare l'installazione del file dell'amministratore se l'obiettivo è quello di limitare le scelte dell'utente finale nell'esperienza di installazione di Visual Studio. Selezionare i parametri della riga di comando se si intende creare una configurazione iniziale ma si vuole consentire all'utente finale di personalizzare la propria esperienza di installazione di Visual Studio.  
  
 Per altre informazioni sull'esperienza relativa al file dell'amministratore, vedere [How to: Create and Run an Unattended Installation of Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md) e [How to: Automatically apply product keys when deploying Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md).  Per altre informazioni sui controlli della riga di comando, vedere la pagina [usare i parametri della riga di comando per installare Visual Studio](../install/use-command-line-parameters-to-install-visual-studio.md) .  
  
## <a name="specifying-customer-feedback-settings"></a>Specifica delle impostazioni dei commenti e suggerimenti del cliente  

Per impostazione predefinita, l'installazione di Visual Studio consente l'invio di commenti dei clienti. È possibile configurare Visual Studio per disabilitare i suggerimenti dei clienti nei singoli computer modificando in stringa "0" il valore della chiave seguente del Registro di sistema:  
  
**HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM**  
**OptIn**  
  
Ad esempio, modificare il valore in HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\VisualStudio\SQM OptIn="0"  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Argomento|Descrizione|  
|-----------|-----------------|  
|[Procedura: Installare una versione specifica di Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md)|Viene descritto come installare configurazioni specifiche della versione corrente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|  
|[Procedura: Creare ed eseguire un'installazione automatica di Visual Studio](../install/how-to-create-and-run-an-unattended-installation-of-visual-studio.md)|Viene descritto come installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] in modalità automatica.|  
|[Procedura: Applicare automaticamente i codici Product Key durante la distribuzione di Visual Studio](../install/how-to-automatically-apply-product-keys-when-deploying-visual-studio.md)|Viene descritto come applicare i codici Product Key durante la distribuzione in più computer.|  
|[Guida dell'amministratore di Help Viewer](../ide/help-viewer-administrator-guide.md)|Fornisce informazioni su come gestire le installazioni della guida locale per gli ambienti di rete che dispongono o non dispongono di accesso a Internet.|  
|[Installare Visual Studio](../install/install-visual-studio-2015.md)|Vengono fornite istruzioni e collegamenti ad argomenti in cui viene descritto come installare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].|