---
title: Gestione di associazioni di file affiancati | Microsoft Docs
description: Se il pacchetto VSPackage fornisce associazioni di file, decidere come gestire le installazioni side-by-side in cui una determinata versione di Visual Studio apre un file.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, setting default
ms.assetid: 9b6df3bc-d15c-4a5d-9015-948a806193b7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 083eef2454a9e805b1cb8b3e85a6d7d81263a0dd
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105073053"
---
# <a name="manage-side-by-side-file-associations"></a>Gestire le associazioni di file affiancati

Se il pacchetto VSPackage fornisce associazioni di file, è necessario decidere come gestire le installazioni side-by-side in cui [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] deve essere richiamata una particolare versione di per aprire un file. I formati di file non compatibili compostano il problema.

Gli utenti prevedono la compatibilità di una nuova versione di un prodotto con le versioni precedenti, in modo che i file esistenti possano essere caricati in una nuova versione senza perdita di dati. Idealmente, il pacchetto VSPackage può caricare e salvare i formati di file delle versioni precedenti. In caso contrario, è consigliabile offrire per aggiornare il formato di file alla nuova versione del pacchetto VSPackage. Lo svantaggio di questo approccio è che il file aggiornato non può essere aperto nella versione precedente.

Per evitare questo problema, è possibile modificare le estensioni quando i formati di file diventano incompatibili. Ad esempio, la versione 1 del pacchetto VSPackage può usare l'estensione, *. mypkg10* e la versione 2 possono usare l'estensione *mypkg20*. Questa differenza identifica il VSPackage che apre un file specifico. Se si aggiungono pacchetti Vspackage più recenti all'elenco di programmi associati a un'estensione precedente, gli utenti possono fare clic con il pulsante destro del mouse sul file e scegliere di aprirlo in un pacchetto VSPackage più recente. A questo punto, il pacchetto VSPackage può offrire per aggiornare il file al nuovo formato o aprire il file e mantenere la compatibilità con le versioni precedenti del pacchetto VSPackage.

> [!NOTE]
> È possibile combinare questi approcci. Ad esempio, è possibile offrire compatibilità con le versioni precedenti caricando un file precedente e l'offerta per aggiornare il formato del file quando l'utente lo salva.

## <a name="face-the-problem"></a>Affrontare il problema

Se si desidera che più VSPackage affiancati usino la stessa estensione, è necessario scegliere la versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] associata all'estensione. Ecco due alternative:

- Aprire il file nella versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] installata nel computer di un utente.

   Con questo approccio, il programma di installazione è responsabile della determinazione della versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e dell'inclusione nella voce del registro di sistema scritta per l'associazione di file. In un pacchetto di Windows Installer, è possibile includere azioni personalizzate per impostare una proprietà che indichi la versione più recente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

  > [!NOTE]
  > In questo contesto, "più recente" significa "ultima versione supportata". Queste voci del programma di installazione non rileveranno automaticamente una versione successiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Le voci di [rilevamento dei requisiti di sistema](../extensibility/internals/detecting-system-requirements.md) e dei [comandi che devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md) sono simili a quelle presentate qui e sono necessarie per supportare versioni aggiuntive di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

   Le righe seguenti della tabella CustomAction impostano la proprietà DEVENV_EXE_LATEST come proprietà impostata dalle tabelle AppSearch e RegLocator illustrate in [comandi che devono essere eseguiti dopo l'installazione](../extensibility/internals/commands-that-must-be-run-after-installation.md). Le righe nella tabella InstallExecuteSequence pianificano le azioni personalizzate all'inizio della sequenza di esecuzione. I valori nella colonna Condition fanno funzionare la logica:

  - Visual Studio .NET 2002 è la versione più recente se è l'unica versione attuale.

  - Visual Studio .NET 2003 è la versione più recente solo se è presente e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non è presente.

  - [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] è la versione più recente se è l'unica versione presente.

    Il risultato finale è che DEVENV_EXE_LATEST contiene il percorso della versione più recente di devenv.exe.

  **CustomAction righe della tabella che determinano la versione più recente di Visual Studio**

  |Azione|Tipo|Source (Sorgente)|Destinazione|
  |------------|----------|------------|------------|
  |CA_SetDevenvLatest_2002|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2002]|
  |CA_SetDevenvLatest_2003|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2003]|
  |CA_SetDevenvLatest_2005|51|DEVENV_EXE_LATEST|[DEVENV_EXE_2005]|

  **InstallExecuteSequence righe della tabella che determinano la versione più recente di Visual Studio**

  |Azione|Condizione|Sequenza|
  |------------|---------------|--------------|
  |CA_SetDevenvLatest_2002|DEVENV_EXE_2002 E NON (DEVENV_EXE_2003 O DEVENV_EXE_2005)|410|
  |CA_SetDevenvLatest_2003|DEVENV_EXE_2003 E NON DEVENV_EXE_2005|420|
  |CA_SetDevenvLatest_2005|DEVENV_EXE_2005|430|

   È possibile utilizzare la proprietà DEVENV_EXE_LATEST nella tabella del registro di sistema del pacchetto Windows Installer per scrivere il valore predefinito della chiave **ShellOpenCommand del HKEY_CLASSES_ROOT *ProgID*** , [DEVENV_EXE_LATEST] "%1"

- Eseguire un programma di avvio condiviso che può essere la scelta migliore dalle versioni VSPackage disponibili.

   Gli sviluppatori di hanno [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] scelto questo approccio per gestire i requisiti complessi dei diversi formati di soluzioni e progetti derivanti da numerose versioni di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Con questo approccio, viene registrato un programma di avvio come gestore dell'estensione. L'utilità di avvio esamina il file e decide quale versione di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e il pacchetto VSPackage può gestire il file specifico. Ad esempio, se un utente apre un file che è stato salvato per l'ultima volta da una particolare versione del pacchetto VSPackage, l'utilità di avvio può avviare il pacchetto VSPackage nella versione corrispondente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Inoltre, un utente può configurare l'utilità di avvio per avviare sempre la versione più recente. Un utilità di avvio può inoltre richiedere a un utente di aggiornare il formato del file. Se il formato del file include un numero di versione, l'utilità di avvio potrebbe informare un utente se il formato del file è di una versione successiva a uno o più dei pacchetti VSPackage installati.

   L'utilità di avvio deve trovarsi in un componente Windows Installer condiviso con tutte le versioni del pacchetto VSPackage. Questo processo assicura che la versione più recente sia sempre installata e non venga rimossa fino a quando non vengono disinstallate tutte le versioni del pacchetto VSPackage. In questo modo, le associazioni di file e altre voci del registro di sistema del componente di avvio vengono mantenute anche se viene disinstallata una versione del pacchetto VSPackage.

## <a name="uninstall-and-file-associations"></a>Disinstallazione e associazioni di file

La disinstallazione di un pacchetto VSPackage che scrive le voci del registro di sistema per le associazioni di file rimuove le associazioni di file. Di conseguenza, all'estensione non è associato alcun programma. Windows Installer non consente di recuperare le voci del registro di sistema aggiunte al momento dell'installazione del pacchetto VSPackage. Ecco alcuni modi per correggere le associazioni di file di un utente:

- Usare un componente di avvio condiviso come descritto in precedenza.

- Indicare all'utente di eseguire un ripristino della versione del pacchetto VSPackage che l'utente vuole avere il proprietario dell'associazione di file.

- Fornire un programma eseguibile separato che riscriva le voci del registro di sistema appropriate.

- Specificare una pagina delle opzioni di configurazione o una finestra di dialogo che consente agli utenti di scegliere le associazioni di file e di recuperare le associazioni perse. Indicare agli utenti di eseguirlo dopo la disinstallazione.

## <a name="see-also"></a>Vedi anche

- [Registrare le estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)
- [Registrare i verbi per le estensioni dei nomi di file](../extensibility/registering-verbs-for-file-name-extensions.md)
