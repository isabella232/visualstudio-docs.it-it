---
title: 'Procedure consigliate per lo sviluppo: componenti VSTO COM, & componenti aggiuntivi VBA in Office'
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 523f339fb26ea12e8e737772a59002001d6302bb
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122106471"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Procedure consigliate per lo sviluppo di componenti aggiuntivi COM, VSTO e VBA in Office
  Se si sviluppano componenti aggiuntivi COM, VSTO o VBA per Office, seguire le procedure consigliate per lo sviluppo descritte in questo articolo.   In modo da garantire:

- Compatibilità dei componenti aggiuntivi tra versioni e distribuzioni diverse di Office.
- Riduzione della complessità della distribuzione dei componenti aggiuntivi per gli utenti e gli amministratori IT.
- Non si verificano errori imprevisti di installazione o di runtime del componente aggiuntivo.

>Nota: l'uso [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) per preparare il componente aggiuntivo COM, VSTO o VBA per Windows Store non è supportato. I componenti VSTO COM e VBA non possono essere distribuiti in Windows Store o Office Store.

## <a name="do-not-check-for-office-during-installation"></a>Non verificare la presenza di Office durante l'installazione
 Non è consigliabile fare in modo che il componente aggiuntivo rilevi se Office viene installato durante il processo di installazione del componente aggiuntivo. Se Office non è installato, è possibile installare il componente aggiuntivo e l'utente sarà in grado di accedervi dopo Office installato.

## <a name="use-embedded-interop-types-nopia"></a>Usare tipi di interoperabilità incorporati (NoPIA)
Se la soluzione usa .NET 4.0 o versione successiva, usare i tipi di interoperabilità incorporati (NoPIA) invece di dipendere dall'assembly di interoperabilità primario (PIA) di Office ridistribuibile. L'uso dell'incorporamento dei tipi riduce le dimensioni di installazione della soluzione e garantisce la compatibilità futura. Office 2010 è stata l'ultima versione Office che ha fornito l'applicazione ridistribuibile PIA. Per altre informazioni, vedere [Procedura dettagliata: Incorporamento](/previous-versions/ee317478(v=vs.140)) di informazioni sui tipi Microsoft Office assembly e Equivalenza del tipo e tipi [di interoperabilità incorporati.](/windows/uwp/porting/desktop-to-uwp-root)

Se la soluzione usa una versione precedente di .NET, è consigliabile aggiornare la soluzione per l'uso di .NET 4.0 o versione successiva. L'uso di .NET 4.0 o versioni successive riduce i prerequisiti di runtime nelle versioni più recenti di Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Evitare di dipendere da versioni Office specifiche
Se la soluzione usa funzionalità disponibili solo nelle versioni più recenti di Office, verificare che la funzionalità esista (se possibile, a livello di funzionalità) in fase di esecuzione(ad esempio, usando la gestione delle eccezioni o controllando la versione). Convalidare le versioni minime, anziché versioni specifiche, usando le API supportate nel modello a oggetti, ad esempio la [proprietà Application.Version](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Non è consigliabile basarsi su Office binari, percorsi di installazione o chiavi del Registro di sistema, perché possono cambiare tra installazioni, ambienti e versioni.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Abilitare l'utilizzo delle chiavi sia a 32 bit che a 64 bit Office
La destinazione di compilazione predefinita deve supportare sia a 32 bit (x86) che a 64 bit (x64), a meno che la soluzione non dipenda da librerie disponibili solo per un numero di bit specifico. La versione a 64 bit di Office è in aumento nell'adozione, soprattutto negli ambienti Big Data. Il supporto sia a 32 bit che a 64 bit rende più semplice per gli utenti la transizione tra le versioni a 32 bit e a 64 bit di Office.

Quando si scrive codice VBA, usare istruzioni declare sicure a 64 bit e convertire le variabili in base alle esigenze. Assicurarsi inoltre che i documenti possano essere condivisi tra gli utenti che eseguono versioni a 32 bit o a 64 bit di Office fornendo il codice per ogni numero di bit. Per altre informazioni, vedere [64-bit Visual Basic for applications overview](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Supportare ambienti con restrizioni
La soluzione non deve richiedere privilegi di elevazione degli account utente o di amministratore. Inoltre, la soluzione non deve dipendere dall'impostazione o dalla modifica:

- Directory di lavoro corrente
- Directory di caricamento DLL.
- Variabile PATH.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modificare il percorso di salvataggio dei dati condivisi e delle impostazioni
Se la soluzione è costituita da un componente aggiuntivo e da un processo esterno a Office, non usare la cartella dei dati dell'applicazione dell'utente o il Registro di sistema per scambiare dati o impostazioni tra il componente aggiuntivo e il processo esterno. È invece consigliabile usare la cartella temporanea dell'utente, la cartella documenti o la directory di installazione della soluzione.

## <a name="increment-the-version-number-with-each-update"></a>Incrementare il numero di versione con ogni aggiornamento
Impostare il numero di versione dei file binari nella soluzione e incrementarlo a ogni aggiornamento. In questo modo sarà più semplice per gli utenti identificare le modifiche tra le versioni e valutare la compatibilità.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fornire istruzioni di supporto per le versioni più recenti di Office
I clienti chiedono agli ISV di fornire istruzioni di supporto per i componenti aggiuntivi COM, VSTO e VBA eseguiti in Office. L'elenco delle istruzioni di supporto esplicite consente ai clienti di usare Microsoft 365 app per gli strumenti di idoneità aziendale per comprendere il supporto.

Per fornire istruzioni di supporto per le applicazioni client di Office (ad esempio, Word o Excel), verificare innanzitutto che i componenti aggiuntivi siano eseguiti nella versione corrente di Office e quindi eseguire il commit per fornire gli aggiornamenti se il componente aggiuntivo si interrompe in una versione futura. Non è necessario testare i componenti aggiuntivi quando Microsoft rilascia una nuova build o un aggiornamento per Office. Microsoft raramente modifica la piattaforma di estendibilità COM, VSTO e VBA in Office e queste modifiche saranno ben documentate.

>Importante: Microsoft gestisce un elenco dei componenti aggiuntivi supportati per i report di conformità e le informazioni di contatto dell'ISV. Per ottenere il componente aggiuntivo elencato, vedere [/configmgr/desktop-analytics/ready-for-windows.](/configmgr/desktop-analytics/ready-for-windows)

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Usare Monitoraggio processo per eseguire il debug dei problemi di installazione o caricamento
Se il componente aggiuntivo presenta problemi di compatibilità durante l'installazione o il caricamento, potrebbe essere correlato a problemi di accesso al file o al Registro di sistema. Usare [Monitoraggio processo o](/sysinternals/downloads/procmon) uno strumento di debug simile per registrare e confrontare il comportamento con un ambiente di lavoro per identificare il problema.