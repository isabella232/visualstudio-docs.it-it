---
title: Gestione delle associazioni di file side-by-side | Microsoft Docs
description: Se il VSPackage fornisce associazioni di file, decidere come gestire le installazioni side-by-side in cui una particolare versione di Visual Studio apre un file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 306643116e295342bcfb602eef370af418c87733
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709461"
---
# <a name="manage-side-by-side-file-associations"></a>Gestire le associazioni di file side-by-side

Se il pacchetto VSPackage fornisce associazioni di file, è necessario decidere come gestire le installazioni side-by-side in cui una determinata versione di deve essere richiamata per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] aprire un file. Il problema è stato composto da formati di file incompatibili.

Gli utenti si aspettano che una nuova versione di un prodotto sia compatibile con le versioni precedenti, in modo che i file esistenti possano essere caricati in una nuova versione senza perdere dati. Idealmente, il pacchetto VSPackage può caricare e salvare i formati di file delle versioni precedenti. In caso contrario, è consigliabile scegliere di aggiornare il formato di file alla nuova versione del pacchetto VSPackage. Lo svantaggio di questo approccio è che il file aggiornato non può essere aperto nella versione precedente.

Per evitare questo problema, è possibile modificare le estensioni quando i formati di file diventano incompatibili. Ad esempio, la versione 1 del pacchetto VSPackage potrebbe usare l'estensione *mypkg10* e la versione 2 potrebbe usare l'estensione *mypkg20.* Questa differenza identifica il VSPackage che apre un file specifico. Se si aggiungono pacchetti VSPackage più nuovi all'elenco di programmi associati a un'estensione precedente, gli utenti possono fare clic con il pulsante destro del mouse sul file e scegliere di aprirlo in un VSPackage più recente. A questo punto, il pacchetto VSPackage può offrire l'aggiornamento del file al nuovo formato o aprire il file e mantenere la compatibilità con le versioni precedenti del pacchetto VSPackage.

> [!NOTE]
> È possibile combinare questi approcci. Ad esempio, è possibile offrire la compatibilità con le versioni precedenti caricando un file meno recente e offrire l'aggiornamento del formato di file quando l'utente lo salva.

## <a name="face-the-problem"></a>Affrontare il problema

Se si vuole che più VSPackage side-by-side usino la stessa estensione, è necessario scegliere la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associata all'estensione. Ecco due alternative:

- Aprire il file nella versione più recente [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] di installata nel computer di un utente.

   In questo approccio, il programma di installazione è responsabile di determinare la versione più recente di e include tale versione nella voce del Registro di sistema scritta per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] l'associazione di file. In un Windows Installer è possibile includere azioni personalizzate per impostare una proprietà che indica la versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > In questo contesto, "più recente" significa "versione supportata più recente". Queste voci del programma di installazione non rileveranno automaticamente una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Le voci in [Detecting System Requirements](../extensibility/internals/detecting-system-requirements.md) (Rilevamento dei requisiti di sistema) e in [Commands That Must Be Run After Installation](../extensibility/internals/commands-that-must-be-run-after-installation.md) (Comandi che devono essere eseguiti dopo l'installazione) sono simili a quelle presentate qui e sono necessarie per supportare versioni aggiuntive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   Le righe seguenti nella tabella CustomAction impostano la proprietà DEVENV_EXE_LATEST come proprietà impostata dalle tabelle AppSearch e RegLocator descritte in Comandi che devono essere eseguiti dopo [l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md)di . Le righe nella tabella InstallExecuteSequence pianificano le azioni personalizzate nelle prime fasi della sequenza di esecuzione. I valori nella colonna Condizione fanno funzionare la logica:

  - Visual Studio .NET 2002 è la versione più recente se è l'unica versione presente.

  - Visual Studio .NET 2003 è la versione più recente solo se è presente e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è presente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è la versione più recente se è l'unica versione presente.

    Il risultato finale è che DEVENV_EXE_LATEST contiene il percorso della versione più recente di devenv.exe.

  **Righe della tabella CustomAction che determinano la versione più recente di Visual Studio**

  |Azione|Tipo|Source (Sorgente)|Destinazione|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **Righe della tabella InstallExecuteSequence che determinano la versione più recente di Visual Studio**

  |Azione|Condizione|Sequenza|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 AND NOT (DEVENV_EXE_2003 OR DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 AND NOT DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   È possibile usare la proprietà DEVENV_EXE_LATEST nella tabella Registry del pacchetto del programma di installazione di Windows per scrivere il valore predefinito della chiave **HKEY_CLASSES_ROOT *ProgId* ShellOpenCommand,** [DEVENV_EXE_LATEST] "%1"

- Eseguire un programma di avvio condiviso che può essere la scelta migliore tra le versioni di VSPackage disponibili.

   Gli sviluppatori di hanno scelto questo approccio per gestire i requisiti complessi dei diversi formati di soluzioni e progetti risultati [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] da molte versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . In questo approccio si registra un programma di avvio come gestore dell'estensione. L'utilità di avvio esamina il file e decide quale versione di e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il VSPackage è in grado di gestire quel particolare file. Ad esempio, se un utente apre un file salvato per l'ultima volta da una versione specifica del pacchetto VSPackage, l'utilità di avvio può avviare il pacchetto VSPackage nella versione corrispondente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Inoltre, un utente può configurare l'utilità di avvio per avviare sempre la versione più recente. Un'utilità di avvio potrebbe anche richiedere all'utente di aggiornare il formato del file. Se il formato del file include un numero di versione, l'utilità di avvio potrebbe informare l'utente se il formato del file deriva da una versione successiva a uno o più pacchetti VSPackage installati.

   L'utilità di avvio deve essere in Windows del programma di installazione che viene condiviso con tutte le versioni del pacchetto VSPackage. Questo processo garantisce che la versione più recente sia sempre installata e non venga rimossa fino a quando non vengono disinstallate tutte le versioni del pacchetto VSPackage. In questo modo, le associazioni di file e altre voci del Registro di sistema del componente di avvio vengono mantenute anche se viene disinstallata una versione del pacchetto VSPackage.

## <a name="uninstall-and-file-associations"></a>Disinstallare e le associazioni di file

La disinstallazione di un VSPackage che scrive voci del Registro di sistema per le associazioni di file rimuove le associazioni di file. Pertanto, all'estensione non sono associati programmi. Windows Il programma di installazione non "ripristina" le voci del Registro di sistema aggiunte durante l'installazione del pacchetto VSPackage. Ecco alcuni modi per correggere le associazioni di file di un utente:

- Usare un componente di avvio condiviso come descritto in precedenza.

- Indicare all'utente di eseguire un ripristino della versione del PACCHETTO VSPackage di cui l'utente vuole essere proprietario dell'associazione di file.

- Fornire un programma eseguibile separato che riscrive le voci del Registro di sistema appropriate.

- Specificare una pagina o una finestra di dialogo di opzioni di configurazione che consente agli utenti di scegliere le associazioni di file e recuperare le associazioni perse. Indica agli utenti di eseguirlo dopo la disinstallazione.

## <a name="see-also"></a>Vedi anche

- [Registrare le estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrare i verbi per le estensioni di file](../extensibility/registering-verbs-for-file-name-extensions.md)
