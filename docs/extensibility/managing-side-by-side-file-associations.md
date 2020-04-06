---
title: Gestione delle associazioni di file side-by-side Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6c284fe7ef4c2d07051a8524860583cb634e13bf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702766"
---
# <a name="manage-side-by-side-file-associations"></a>Gestire le associazioni di file side-by-side

Se il pacchetto VSPackage fornisce associazioni di file, è necessario decidere come gestire [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] le installazioni side-by-side in cui una particolare versione di deve essere richiamata per aprire un file. Formati di file incompatibili aggravano il problema.

Gli utenti si aspettano che una nuova versione di un prodotto sia compatibile con le versioni precedenti, in modo che i file esistenti possano essere caricati in una nuova versione senza perdere dati. Idealmente, il pacchetto VSPackage può caricare e salvare i formati di file delle versioni precedenti. Se questo non è vero, si dovrebbe offrire di aggiornare il formato di file alla nuova versione del pacchetto VSPackage. Lo svantaggio di questo approccio è che il file aggiornato non può essere aperto nella versione precedente.

Per evitare questo problema, è possibile modificare le estensioni quando i formati di file diventano incompatibili. Ad esempio, la versione 1 del pacchetto VSPackage potrebbe utilizzare l'estensione *,mypkg10*, e la versione 2 potrebbe utilizzare l'estensione *,mypkg20*. Questa differenza identifica il pacchetto VSPackage che apre un file specifico. Se si aggiungono PACKAGE VS più recenti all'elenco dei programmi associati a un'estensione precedente, gli utenti possono fare clic con il pulsante destro del mouse sul file e scegliere di aprirlo in un VSPackage più recente. A questo punto, il pacchetto VSPackage può offrire per aggiornare il file al nuovo formato o aprire il file e mantenere la compatibilità con le versioni precedenti del pacchetto VSPackage.

> [!NOTE]
> È possibile combinare questi approcci. Ad esempio, è possibile offrire la compatibilità con le versioni precedenti caricando un file meno recente e offrire l'aggiornamento del formato di file quando l'utente lo salva.

## <a name="face-the-problem"></a>Affrontare il problema

Se si desidera che più VSPackage side-by-side per utilizzare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la stessa estensione, è necessario scegliere la versione di che è associata all'estensione. Ecco due alternative:

- Aprire il file nella [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] versione più recente di installata nel computer dell'utente.

   In questo approccio, il programma di installazione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è responsabile per determinare la versione più recente di e incluso che nella voce del Registro di sistema scritta per l'associazione di file. In un pacchetto di Windows Installer è possibile includere azioni personalizzate [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]per impostare una proprietà che indichi la versione più recente di .

  > [!NOTE]
  > In questo contesto, "ultima" significa "ultima versione supportata". Queste voci di installazione non rileveranno automaticamente una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Le voci in [Rilevamento dei requisiti di sistema](../extensibility/internals/detecting-system-requirements.md) e nei comandi che devono essere [eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md) sono simili a quelle presentate qui e sono necessarie per supportare versioni aggiuntive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

   Le righe seguenti nella tabella CustomAction impostano la proprietà DEVENV_EXE_LATEST come proprietà impostata dalle tabelle AppSearch e RegLocator descritte in [Comandi che devono essere eseguiti dopo l'installazione.](../extensibility/internals/commands-that-must-be-run-after-installation.md) Le righe della tabella InstallExecuteSequence pianificano le azioni personalizzate all'inizio della sequenza di esecuzione. I valori nella colonna Condizione rendono il funzionamento della logica:Values in the Condition column make the logic work:

  - Visual Studio .NET 2002 è la versione più recente se è l'unica versione presente.

  - Visual Studio .NET 2003 è la versione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] più recente solo se è presente e non è presente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]è la versione più recente se è l'unica versione presente.

    Il risultato finale è che DEVENV_EXE_LATEST contiene il percorso della versione più recente di devenv.exe.

  **Righe della tabella CustomAction che determinano la versione più recente di Visual Studio**

  |Azione|Type|Source (Sorgente)|Destinazione|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence table rows that determine the latest version of Visual Studio**

  |Azione|Condizione|Sequenza|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 AND NOT (DEVENV_EXE_2003 OR DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 E NON DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   È possibile utilizzare la proprietà DEVENV_EXE_LATEST nella tabella Registry del pacchetto di Windows Installer per scrivere il valore predefinito della chiave ***ProgId*ShellOpenCommand di HKEY_CLASSES_ROOT,** [DEVENV_EXE_LATEST] "%1"

- Eseguire un programma di avvio condiviso che può fare la scelta migliore tra le versioni disponibili VSPackage.

   Gli sviluppatori [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di ha scelto questo approccio per gestire i requisiti complessi [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]dei molteplici formati di soluzioni e progetti che derivano da molte versioni di . In questo approccio, si registra un programma di avvio come gestore di estensione. Il programma di avvio esamina il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] file e decide quale versione di e il pacchetto VSPackage in grado di gestire quel particolare file. Ad esempio, se un utente apre un file salvato per ultimo da una particolare versione del pacchetto [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage, il programma di avvio può avviare tale VSPackage nella versione corrispondente di . Inoltre, un utente potrebbe configurare il programma di avvio per avviare sempre la versione più recente. Un programma di avvio potrebbe anche richiedere all'utente di aggiornare il formato del file. Se il formato del file include un numero di versione, il programma di avvio potrebbe informare un utente se il formato di file è da una versione successiva a uno o più dei package VS installati.

   Il programma di avvio deve essere in un componente di Windows Installer condiviso con tutte le versioni del pacchetto VSPackage.The launcher should be in a Windows Installer component that is shared with all versions of your VSPackage. Questo processo assicura che la versione più recente viene sempre installata e non viene rimosso fino a quando non vengono disinstallate tutte le versioni del pacchetto VSPackage.This process makes sure that the latest version is always installed and is not removed until all versions of your VSPackage are uninstalled. In questo modo, le associazioni di file e altre voci del Registro di sistema del componente di avvio vengono mantenute anche se viene disinstallata una versione del pacchetto VSPackage.

## <a name="uninstall-and-file-associations"></a>Disinstallazione e associazioni di file

Disinstallazione di un pacchetto VSPackage che scrive le voci del Registro di sistema per le associazioni di file rimuove le associazioni di file. Pertanto, l'estensione non ha programmi associati. Windows Installer non "recupera" le voci del Registro di sistema che sono state aggiunte quando è stato installato il pacchetto VSPackage. Ecco alcuni modi per correggere le associazioni di file di un utente:

- Utilizzare un componente di avvio condiviso come descritto in precedenza.

- Indicare all'utente di eseguire un ripristino della versione del pacchetto VSPackage che l'utente desidera essere proprietario dell'associazione di file.

- Fornire un programma eseguibile separato che riscriva le voci del Registro di sistema appropriate.

- Fornire una pagina o una finestra di dialogo delle opzioni di configurazione che consenta agli utenti di scegliere le associazioni di file e recuperare le associazioni perse. Indicare agli utenti di eseguirlo dopo la disinstallazione.

## <a name="see-also"></a>Vedere anche

- [Registrare le estensioni dei nomi di file per le distribuzioni side-by-sideRegister file name extensions for side-by-side deployments](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrare i verbi per le estensioni di fileRegister verbs for file name extensions](../extensibility/registering-verbs-for-file-name-extensions.md)
