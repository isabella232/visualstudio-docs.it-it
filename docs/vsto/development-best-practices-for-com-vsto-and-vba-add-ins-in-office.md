---
title: 'Procedure consigliate di sviluppo: COM, VSTO, & componenti aggiuntivi VBA in Office'
description: Informazioni sulle procedure consigliate per lo sviluppo di componenti aggiuntivi COM, VSTO e VBA per Microsoft Office.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 07/25/2017
ms.topic: conceptual
dev_langs:
- ''
helpviewer_keywords:
- ''
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e7387b58bae486588687fe018453fafb5d6571f7
ms.sourcegitcommit: ce85cff795df29e2bd773b4346cd718dccda5337
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/08/2020
ms.locfileid: "96846896"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Procedure consigliate per lo sviluppo di componenti aggiuntivi COM, VSTO e VBA in Office
  Se si sviluppano componenti aggiuntivi COM, VSTO o VBA per Office, seguire le procedure consigliate per lo sviluppo descritte in questo articolo.   In modo da garantire:

- Compatibilità dei componenti aggiuntivi in versioni e distribuzioni diverse di Office.
- Riduzione della complessità della distribuzione dei componenti aggiuntivi per gli utenti e gli amministratori IT.
- Non si verificano errori di installazione o Runtime non intenzionali del componente aggiuntivo.

>Nota: l'uso di [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) per preparare il componente aggiuntivo com, VSTO o VBA per Windows Store non è supportato. I componenti aggiuntivi COM, VSTO e VBA non possono essere distribuiti in Windows Store o in Office Store.

## <a name="do-not-check-for-office-during-installation"></a>Non controllare Office durante l'installazione
 Non è consigliabile che il componente aggiuntivo rilevi se Office è installato durante il processo di installazione del componente aggiuntivo. Se Office non è installato, è possibile installare il componente aggiuntivo e l'utente sarà in grado di accedervi dopo l'installazione di Office.

## <a name="use-embedded-interop-types-nopia"></a>Usare i tipi di interoperabilità incorporati (NoPIA)
Se la soluzione USA .NET 4,0 o versione successiva, usare i tipi di interoperabilità incorporati (NoPIA) anziché a seconda degli assembly di interoperabilità primari di Office (PIA) ridistribuibili. L'uso dell'incorporamento dei tipi riduce le dimensioni di installazione della soluzione e garantisce la compatibilità futura. Office 2010 è stata l'ultima versione di Office che ha fornito l'assembly di interoperabilità primario ridistribuibile. Per altre informazioni, vedere [procedura dettagliata: incorporamento delle informazioni sui tipi da assembly Microsoft Office](/previous-versions/ee317478(v=vs.140)) e [equivalenza del tipo e tipi di interoperabilità incorporati](/windows/uwp/porting/desktop-to-uwp-root).

Se la soluzione USA una versione precedente di .NET, è consigliabile aggiornare la soluzione per l'uso di .NET 4,0 o versione successiva. L'uso di .NET 4,0 o versione successiva riduce i prerequisiti di runtime nelle versioni più recenti di Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Evitare la dipendenza da versioni di Office specifiche
Se la soluzione USA funzionalità disponibili solo nelle versioni più recenti di Office, verificare che la funzionalità esista (se possibile, a livello di funzionalità) in fase di esecuzione, ad esempio usando la gestione delle eccezioni o controllando la versione. Convalidare le versioni minime, anziché versioni specifiche, usando le API supportate nel modello a oggetti, ad esempio la [Proprietà Application. Version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Non è consigliabile fare affidamento su metadati binari Office, percorsi di installazione o chiavi del registro di sistema, in quanto questi possono cambiare tra installazioni, ambienti e versioni.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Abilita l'utilizzo di Office sia a 32 bit che a 64 bit
La destinazione di compilazione predefinita deve supportare sia 32 bit (x86) che 64 bit (x64), a meno che la soluzione non dipenda da librerie disponibili solo per un bit specifico. La versione a 64 bit di Office sta aumentando l'adozione, soprattutto in ambienti Big Data. Il supporto di sia a 32 bit che a 64 bit rende più semplice per gli utenti la transizione tra le versioni di Office a 32 bit e a 64 bit.

Quando si scrive codice VBA, usare le istruzioni Declare sicure a 64 bit e convertire le variabili in base alle esigenze. Assicurarsi inoltre che i documenti possano essere condivisi tra gli utenti che eseguono versioni di Office a 32 bit o a 64 bit fornendo codice per ogni bit. Per ulteriori informazioni, vedere [Panoramica di Visual Basic a 64 bit per le applicazioni](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Supportare ambienti con restrizioni
La soluzione non deve richiedere privilegi di privilegi di amministratore o di elevazione degli account utente. Inoltre, la soluzione non deve dipendere dall'impostazione o dalla modifica:

- Directory di lavoro corrente
- Directory di caricamento della DLL.
- Variabile di percorso.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modificare il percorso di salvataggio dei dati e delle impostazioni condivisi
Se la soluzione è costituita da un componente aggiuntivo e da un processo esterno a Office, non usare la cartella di dati dell'applicazione dell'utente o il registro di sistema per scambiare dati o impostazioni tra il componente aggiuntivo e il processo esterno. È invece consigliabile usare la cartella temporanea dell'utente, la cartella documenti o la directory di installazione della soluzione.

## <a name="increment-the-version-number-with-each-update"></a>Incrementa il numero di versione con ogni aggiornamento
Impostare il numero di versione dei file binari nella soluzione e incrementarlo a ogni aggiornamento. In questo modo sarà più semplice per gli utenti identificare le modifiche tra le versioni e valutare la compatibilità.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fornire le istruzioni di supporto per le versioni più recenti di Office
I clienti chiedono agli ISV di fornire istruzioni di supporto per i relativi componenti aggiuntivi COM, VSTO e VBA eseguiti in Office. Elencando le istruzioni di supporto esplicito è possibile aiutare i clienti che usano Microsoft 365 app per gli strumenti di conformità aziendale a comprendere il supporto.

Per fornire le istruzioni di supporto per le applicazioni client di Office, ad esempio Word o Excel, verificare innanzitutto che i componenti aggiuntivi vengano eseguiti nella versione corrente di Office e quindi eseguire il commit per fornire gli aggiornamenti se il componente aggiuntivo si interrompe in una versione futura. Non è necessario testare i componenti aggiuntivi quando Microsoft rilascia una nuova compilazione o un aggiornamento a Office. Microsoft raramente modifica la piattaforma di estensibilità COM, VSTO e VBA in Office e queste modifiche saranno ben documentate.

>Importante: Microsoft gestisce un elenco dei componenti aggiuntivi supportati per i report di conformità e le informazioni di contatto ISV. Per ottenere l'elenco dei componenti aggiuntivi, vedere [/ConfigMgr/desktop-Analytics/Ready-for-Windows](/configmgr/desktop-analytics/ready-for-windows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Usare Process Monitor per facilitare il debug di problemi di installazione o caricamento
Se il componente aggiuntivo presenta problemi di compatibilità durante l'installazione o il caricamento, potrebbero essere correlati a problemi di accesso al file o al registro di sistema. Usare [Process Monitor](/sysinternals/downloads/procmon) o uno strumento di debug simile per registrare e confrontare il comportamento con un ambiente funzionante per identificare il problema.