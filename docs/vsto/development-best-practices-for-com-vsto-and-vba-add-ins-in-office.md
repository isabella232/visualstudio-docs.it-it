---
title: Procedure guidate di sviluppo di componenti aggiuntivi COM, VSTO e VBA in Office
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
ms.openlocfilehash: 2fcc2fe575bd6b526f5f66d936625c87e91b0b39
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62999794"
---
# <a name="development-best-practices-for-com-vsto-and-vba-add-ins-in-office"></a>Procedure guidate di sviluppo di componenti aggiuntivi COM, VSTO e VBA in Office
  Se si sviluppano componenti aggiuntivi COM, VSTO o VBA per Office, seguire le procedure guidate di sviluppo descritte in questo articolo.   Questo contribuisce a garantire:

- Compatibilità dei componenti aggiuntivi in diverse versioni e distribuzioni di Office.
- Minore complessità di distribuzione componente aggiuntivo per gli utenti e amministratori IT.
- Non si verificano errori di installazione che di esecuzione imprevisti del componente aggiuntivo.

>Nota: Usando il [Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root) per preparare COM, VSTO o VBA componente aggiuntivo per il Windows Store non è supportato. Componenti aggiuntivi COM, VSTO e VBA non possono essere distribuiti il Windows Store o di Office Store.

## <a name="do-not-check-for-office-during-installation"></a>Non selezionare durante l'installazione per Office
 Non è consigliabile che il componente aggiuntivo rileva se Office viene installato durante il processo di installazione del componente aggiuntivo. Se non è installato Office, è possibile installare il componente aggiuntivo e l'utente sarà in grado di accedere, dopo l'installazione di Office.

## <a name="use-embedded-interop-types-nopia"></a>Usare tipi di interoperabilità incorporati (NoPIA)
Se la soluzione viene utilizzato .NET 4.0 o versione successiva, usare tipi di interoperabilità incorporati (NoPIA) invece che a seconda di Office primario Interop Assembly (PIA) redistributable. Tramite l'incorporamento dei tipi riduce le dimensioni dell'installazione della soluzione e assicura la compatibilità futura. Office 2010 è stata l'ultima versione di Office forniti assembly di interoperabilità primario ridistribuibile. Per altre informazioni, vedere [Procedura dettagliata: Incorporamento di informazioni sui tipi da assembly di Microsoft Office](https://msdn.microsoft.com/library/ee317478.aspx) e [equivalenza del tipo e tipi di interoperabilità incorporati](/windows/uwp/porting/desktop-to-uwp-root).

Se la soluzione Usa una versione precedente di .NET, è consigliabile aggiornare la soluzione per l'uso di .NET 4.0 o versione successiva. Uso di .NET 4.0 o versione successiva riduce i prerequisiti di runtime nelle versioni più recenti di Windows.

## <a name="avoid-depending-on-specific-office-versions"></a>Evitare a seconda delle specifiche versioni di Office
Se la soluzione Usa la funzionalità disponibile solo nelle versioni più recenti di Office, verificare che la funzionalità sia (se possibile, a livello di funzionalità) in fase di esecuzione (ad esempio, utilizzando l'eccezione gestione o dal controllo della versione). Convalidare le versioni minime, anziché a versioni specifiche, usando le API supportate nel modello a oggetti, ad esempio la [Application.Version proprietà](<xref:Microsoft.Office.Interop.Excel._Application.Version%2A>). Non è consigliabile si basano su Office binaria dei metadati, i percorsi di installazione o le chiavi del Registro di sistema poiché questi può cambiare tra versioni, ambienti e le installazioni.

## <a name="enable-both-32-bit-and-64-bit-office-usage"></a>Abilitazione dell'utilizzo di Office a 32 bit sia 64 bit
La destinazione predefinita build deve supportare sia (x86) 32 bit e a 64 bit (x64), a meno che la soluzione dipende dalle librerie che sono disponibili solo per un determinato numero di bit. La versione a 64 bit di Office è in aumento nell'adozione, soprattutto in ambienti big data. Supporting sia a 32 e 64 bit rende più semplice per gli utenti per la transizione tra le versioni a 32 e 64 bit di Office.

Quando si scrive codice VBA, safe a 64 bit usare istruzioni declare e convertire le variabili come appropriato. Inoltre, assicurarsi che i documenti possono essere condivisi tra gli utenti che eseguono versioni a 32 o 64 bit di Office fornisce il codice per ogni numero di bit. Per altre informazioni, vedere [a 64 bit di Visual Basic per la panoramica delle applicazioni](/office/vba/Language/Concepts/Getting-Started/64-bit-visual-basic-for-applications-overview).

## <a name="support-restricted-environments"></a>Supporto degli ambienti con restrizioni
La soluzione non dovrebbe richiedere privilegi di amministratore o l'elevazione dei privilegi di Account utente. Inoltre, la soluzione non deve dipendere l'impostazione o modifica:

- Directory di lavoro corrente.
- Directory di caricamento DLL.
- La variabile di percorso.

## <a name="change-the-save-location-of-shared-data-and-settings"></a>Modificare il salvataggio posizione dei dati condivisi e impostazioni
Se la soluzione è costituita da un componente aggiuntivo e un processo esterno a Office, non utilizzare cartella dati applicazioni dell'utente o il Registro di sistema per lo scambio di dati o delle impostazioni tra il componente aggiuntivo e il processo esterno. In alternativa, è consigliabile usare cartella temporanea dell'utente, documenti o directory di installazione della soluzione.

## <a name="increment-the-version-number-with-each-update"></a>Incrementare il numero di versione con ogni aggiornamento
Imposta il numero di versione dei file binari nella soluzione e incrementarlo con ogni aggiornamento. Ciò renderà più facile per gli utenti identificare le modifiche apportate tra le versioni e valutare la compatibilità.

## <a name="provide-support-statements-for-the-latest-versions-of-office"></a>Fornire istruzioni di supporto per le versioni più recenti di Office
I clienti chiedono agli ISV di fornire istruzioni di supporto per i loro COM, VSTO e VBA componenti aggiuntivi che vengono eseguiti in Office. Elenca i supporto esplicito istruzioni aiuta i clienti che usano Office 365 ProPlus strumenti per la conformità comprendere il supporto tecnico.

Per fornire istruzioni di supporto per le applicazioni client di Office (ad esempio, Word o Excel), verificare innanzitutto che Esegui nella versione Office corrente dei componenti aggiuntivi e quindi eseguire il commit che forniscono gli aggiornamenti se il componente aggiuntivo si interrompe in una versione futura. Non è necessario testare i componenti aggiuntivi quando Microsoft rilascia una nuova build o un aggiornamento a Office. Microsoft vengono modificati raramente la piattaforma di estendibilità COM, VSTO e VBA in Office e queste modifiche saranno ben documentate.

>Importante: Microsoft gestisce un elenco di componenti aggiuntivi supportati per i report di conformità e le informazioni di contatto ISV. Per ottenere il componente aggiuntivo elencato, vedere [ https://aka.ms/readyforwindows ](https://aka.ms/readyforwindows).

## <a name="use-process-monitor-to-help-debug-installation-or-loading-issues"></a>Usare monitoraggio di processo per eseguire il debug di installazione o il caricamento di problemi
Se il componente aggiuntivo ha problemi di compatibilità durante l'installazione o caricamento, possono essere correlate a problemi di accesso del Registro di sistema o file. Uso [Process Monitor](/sysinternals/downloads/procmon) o uno strumento di debug simile per registrare e confrontare il comportamento in un ambiente di lavoro per consentire di identificare il problema.
