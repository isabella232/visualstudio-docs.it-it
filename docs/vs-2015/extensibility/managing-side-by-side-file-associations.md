---
title: Gestire le associazioni di File Side-by-Side | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 171342bf920c2cf1e56da78f5cc7a4bb6d87ea0c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51764776"
---
# <a name="managing-side-by-side-file-associations"></a>Gestione delle associazioni di file side-by-side
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se il pacchetto VSPackage fornisce associazioni di file, è necessario decidere come gestire le installazioni side-by-side in cui una determinata versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] deve essere richiamato per aprire un file. Formati di file incompatibili composta il problema.  
  
 Gli utenti si aspettano una nuova versione di un prodotto sia compatibile con le versioni precedenti, in modo che i file esistenti possono essere caricati in una nuova versione senza perdita di dati. In teoria, il pacchetto VSPackage possa entrambi caricare e salvare i formati di file di versioni precedenti. Se non è true, si deve offrire aggiornare il formato di file per la nuova versione del pacchetto VSPackage. Lo svantaggio di questo approccio è che il file aggiornato non può essere aperto in una versione precedente.  
  
 Per evitare questo problema, è possibile modificare le estensioni quando i formati di file diventano non compatibili. Ad esempio, la versione 1 del pacchetto VSPackage è stato possibile usare l'estensione, .mypkg10 e la versione 2 è stato possibile usare l'estensione, .mypkg20. Questa differenza identifica il pacchetto VSPackage che apre un file specifico. Se si aggiungono pacchetti VSPackage più recente per l'elenco dei programmi che sono associati a un'estensione precedente, gli utenti possono fare doppio clic su file e scegliere di aprirla in un VSPackage più recente. A questo punto, il pacchetto VSPackage può offrire aggiornare il file nel nuovo formato o aprire il file e mantenere la compatibilità con le versioni precedenti del pacchetto VSPackage.  
  
> [!NOTE]
>  È possibile combinare questi approcci. Ad esempio, è possibile offrire compatibilità con le versioni precedenti, caricando un file meno recente e offrono aggiornare il formato di file quando l'utente lo salva.  
  
## <a name="facing-the-problem"></a>Rivolta verso il problema  
 Se si desidera più pacchetti VSPackage side-by-side per usare la stessa estensione, è necessario scegliere la versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] associato con l'estensione. Ecco due alternative:  
  
- Aprire il file nella versione più recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] installato nel computer dell'utente.  
  
   In questo approccio, il programma di installazione è responsabile di determinare la versione più recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] che inclusa nella voce del Registro di sistema scritta per l'associazione del file. In un pacchetto Windows Installer, è possibile includere azioni personalizzate per impostare una proprietà che indica la versione più recente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
  > [!NOTE]
  >  In questo contesto, "latest" significa "versione supportata più recente." Queste voci di programma di installazione non rileva automaticamente una versione successiva di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Le voci [requisiti di sistema di rilevamento](../extensibility/internals/detecting-system-requirements.md) e nella [comandi che devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md) sono simili a quelli presentati in questo articolo e sono necessarie per supportare versioni aggiuntive di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
   Le righe seguenti nella tabella CustomAction impostare la proprietà DEVENV_EXE_LATEST sia una proprietà impostata dal AppSearch e tabelle RegLocator illustrate in [comandi che devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md). Le righe della tabella InstallExecuteSequence pianificare le azioni personalizzate nelle prime fasi della sequenza di esecuzione. Valori nel rendere colonna condizione il lavoro per la logica:  
  
  - Visual Studio .NET 2002 è la versione più recente, se si tratta della versione presente solo.  
  
  - Visual Studio .NET 2003 è l'ultima versione solo se è presente e [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] non è presente.  
  
  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Se si tratta della versione presente soltanto, è la versione più recente.  
  
    Il risultato finale è che DEVENV_EXE_LATEST contiene il percorso della versione più recente di devenv.exe.  
  
  ### <a name="customaction-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Righe della tabella CustomAction che determinano la versione più recente di Visual Studio  
  
  |Operazione|Tipo|Origine|destinazione|  
  |------------|----------|------------|------------|  
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|  
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|  
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|  
  
  ### <a name="installexecutesequence-table-rows-that-determine-the-latest-version-of-visual-studio"></a>Righe della tabella InstallExecuteSequence che determinano la versione più recente di Visual Studio  
  
  |Operazione|Condizione|Sequence|  
  |------------|---------------|--------------|  
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 E NON (DEVENV_EXE_2003 O DEVENV_EXE_2005)|410|  
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 E NON DEVENV_EXE_2005|420|  
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|  
  
   È possibile utilizzare la proprietà DEVENV_EXE_LATEST nella tabella del Registro di sistema del pacchetto Windows Installer per scrivere il HKEY_CLASSES_ROOT*ProgId*valore predefinito della chiave ShellOpenCommand, [DEVENV_EXE_LATEST] "%1"  
  
- Eseguire un programma di avvio condivisa che può effettuare la scelta migliore rispetto alle versioni di VSPackage disponibili.  
  
   Gli sviluppatori di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] scelto questo approccio per gestire i requisiti complessi dei formati più delle soluzioni e progetti risultanti da molte versioni di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. In questo approccio, si registra un programma di avvio come il gestore dell'estensione. L'utilità di avvio esamina il file e decide quale versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e il pacchetto VSPackage può gestire il file in questione. Ad esempio, se un utente apre un file che è stato salvato da una determinata versione del pacchetto VSPackage, l'utilità di avvio può avviare tale pacchetto VSPackage nella versione corrisponda di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Inoltre, un utente è stato possibile configurare l'utilità di avvio per avviare sempre la versione più recente. Un'utilità di avvio potrebbe anche richiedere all'utente di aggiornare il formato del file. Se il formato del file include un numero di versione, l'utilità di avvio è stato possibile comunicare un utente se il formato di file da una versione successiva a quella di una o più dei VSPackage installati.  
  
   L'utilità di avvio deve essere un componente di Windows Installer che è condiviso con tutte le versioni del pacchetto VSPackage. Questo processo consente di verificare che la versione più recente viene sempre installata e non viene rimosso fino a quando non vengono disinstallate tutte le versioni del pacchetto VSPackage. In questo modo, le associazioni di file e le altre voci del Registro di sistema del componente dell'utilità di avvio vengono conservati anche se si disinstalla una versione del pacchetto VSPackage.  
  
## <a name="uninstall-and-file-associations"></a>Disinstallare e le associazioni di File  
 Disinstallazione di un pacchetto VSPackage che scrive le voci del Registro di sistema per le associazioni di file consente di rimuovere le associazioni di file. Pertanto, l'estensione non dispone di alcun programmi associati. Programma di installazione di Windows non viene "ripristinato" le voci del Registro di sistema che sono stati aggiunti durante l'installazione di VSPackage. Ecco alcuni modi per risolvere le associazioni di file dell'utente:  
  
-   Usare un componente condiviso dell'utilità di avvio come descritto in precedenza.  
  
-   Chiedere all'utente di eseguire un ripristino della versione del pacchetto VSPackage che l'utente desidera l'associazione al file il proprietario.  
  
-   Fornire un programma eseguibile separato che riscrive le voci del Registro di sistema appropriate.  
  
-   Fornire una configurazione opzioni pagina o finestra di dialogo che consente agli utenti di scegliere le associazioni di file e recuperare le associazioni perse. Indicare agli utenti di eseguirlo dopo la disinstallazione.  
  
## <a name="see-also"></a>Vedere anche  
 [La registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)   
 [Registrazione di verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)

