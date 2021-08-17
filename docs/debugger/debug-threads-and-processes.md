---
title: Strumenti per eseguire il debug di thread e processi | Microsoft Docs
description: Esaminare gli strumenti per eseguire il debug di thread e processi in Visual Studio. I thread e i processi rappresentano sequenze di istruzioni che devono essere eseguite in un ordine specifico.
ms.custom: SEO-VS-2020
ms.date: 04/21/2018
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- multiprocess debugging
- threading [Visual Studio], debugging
- processes, debugging
- debugging threads
- debugging [Visual Studio], threads
ms.assetid: 9f0c8505-b6b2-452b-adfd-076db14d8115
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: e1a377550b43d6f746e609586561a3dfb5046089
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122105414"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Strumenti per il debug di thread e processi in Visual Studio
I termini *thread* e *processi* costituiscono concetti correlati in ambito informatico. Entrambi rappresentano infatti sequenze di istruzioni che devono essere eseguite in un ordine specifico. Le istruzioni incluse in thread o processi distinti possono tuttavia essere eseguite in parallelo.

 I processi sono disponibili nel sistema operativo e corrispondono a ciò che gli utenti visualizzano sotto forma di programmi o applicazioni. I thread sono invece disponibili nei processi. Per questo motivo vengono talvolta definiti *processi leggeri*. Ciascun processo è costituito da uno o più thread.

 La presenza di più processi consente a un computer di eseguire più attività contemporaneamente. La presenza di più thread consente invece a un processo di suddividere le operazioni da eseguire in parallelo. In un computer con più processori, i processi o i thread possono essere eseguiti in processori diversi consentendo l'effettiva elaborazione in parallelo.

 Una perfetta elaborazione in parallelo non è sempre possibile. È talvolta necessario sincronizzare i thread. È inoltre possibile che un thread debba attendere un risultato di un altro thread o disporre di accesso esclusivo a una risorsa utilizzata da un altro thread. I problemi di sincronizzazione costituiscono una causa comune di bug in applicazioni con multithreading. È talvolta possibile che i thread rimangano in attesa di una risorsa che non diviene mai disponibile, causando una condizione denominata *deadlock*.

 Nel debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sono disponibili strumenti efficaci e di facile utilizzo per il debug di thread e processi.

## <a name="tools-and-features"></a>Strumenti e funzionalità
Gli strumenti che è necessario usare in dipendono dal tipo di codice di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] cui si sta tentando di eseguire il debug:

- Per i processi, gli strumenti principali sono la **finestra** di dialogo Collega a processo, la **finestra** Processi e la barra degli **strumenti Percorso di** debug.

- Per i thread, gli strumenti  principali per il debug dei thread sono la finestra Thread, i marcatori di thread nelle finestre di origine, la finestra **Stack** in **parallelo,** la finestra Controllo parallelo e la barra degli strumenti **Posizione di** debug.

- Per il codice che usa <xref:System.Threading.Tasks.Task> in [Task Parallel Library (TPL),](/dotnet/standard/parallel-programming/task-parallel-library-tpl)il [runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/) (codice nativo),    gli strumenti principali per il debug di  applicazioni multithreading sono la finestra Stack paralleli, la finestra Espressioni di controllo in parallelo e la finestra Attività (la finestra Attività supporta anche l'oggetto promessa JavaScript).

- Per il debug dei thread nella GPU, lo strumento principale è la **finestra Thread GPU.**

  Nella tabella riportata di seguito sono illustrate le informazioni disponibili e le operazioni che è possibile eseguire con ciascuno strumento:

|Interfaccia utente|Informazioni disponibili|Operazioni eseguibili|
|--------------------|---------------------------|-----------------------------|
|Finestra di dialogo **Connetti a processo**|Processi disponibili cui è possibile eseguire la connessione:<br /><br /> -   Nome di processo (estensione exe)<br />-   Numero di ID di processo<br />-   Titolo della barra dei menu<br />-   Tipo (Managed v4.0; Managed v2.0, v1.1, v1.0; x86; x64; IA64)<br />-   Nome utente (nome account)<br />-   Numero di sessione|Selezione di un processo a cui connettersi<br /><br /> Selezione di un computer remoto<br /><br /> Modifica del tipo di trasporto per la connessione a computer remoti|
|Finestra **Processi**|Processi collegati:<br /><br /> -   Nome processo<br />-   Numero di ID di processo<br />-   Percorso dell'eseguibile (file con estensione exe) di processo<br />-   Titolo della barra dei menu<br />-   Stato (Interrompi. In esecuzione)<br />-   Debug (nativo, gestito e così via)<br />-   Tipo di trasporto (predefinito, nativo senza autenticazione)<br />-   Qualificatore di trasporto (computer remoto)|Strumenti:<br /><br /> -   Attach<br />-   Detach<br />-   Terminate<br /><br /> Menu di scelta rapida:<br /><br /> -   Attach<br />-   Detach<br />-   Disconnetti al termine del debug<br />-   Terminate|
|**Finestra** Thread|Thread nel processo corrente:<br /><br /> -   ID thread<br />-   ID gestito<br />-   Categoria (thread principale, thread dell'interfaccia, gestore delle chiamate a una procedura remota o thread di lavoro)<br />-   Nome thread<br />-   Percorso in cui viene creato il thread<br />-   Priorità<br />-   Maschera di affinità<br />-   Numero sospesi<br />-   Nome processo<br />-   Indicatore flag<br />-   Indicatore di sospensione|Strumenti:<br /><br /> -   Cerca<br />-   Cerca nello stack di chiamate<br />-   Contrassegna Just My Code<br />-   Contrassegna selezione moduli personalizzata<br />-   Raggruppa per<br />-   Colonne<br />-   Espandi/Comprimi stack di chiamate<br />-   Espandi/Comprimi gruppi<br />-   Blocca/Sblocca thread<br /><br /> Menu di scelta rapida:<br /><br /> -   Mostra thread nell'origine<br />-   Passa al thread<br />-   Blocca un thread in esecuzione<br />-   Sblocca un thread bloccato<br />-   Imposta flag del thread per studio aggiuntivo<br />-   Rimuovi flag del thread<br />-   Rinomina thread<br />-   Mostra/Nascondi thread<br /><br /> Altre azioni:<br /><br /> -   Visualizzare lo stack di chiamate per un thread in un suggerimento dati|
|Finestra di origine|Gli indicatori dei thread all'estrema sinistra indicano thread singoli o più thread (disattivati per impostazione predefinita, si attivano tramite il menu di scelta rapida nella finestra **Thread**)|Menu di scelta rapida:<br /><br /> -   Passa al thread<br />-   Imposta flag del thread per studio aggiuntivo<br />-   Rimuovi flag del thread|
|Barra degli strumenti **Posizione di debug**|-   Processo corrente<br />-   Sospendi l'applicazione<br />-   Riprendi l'applicazione<br />-   Sospendi e arresta l'applicazione<br />-   Thread corrente<br />-   Attiva/Disattiva lo stato di flag del thread corrente<br />-   Mostra solo thread con flag<br />-   Mostra solo processo corrente<br />-   Stack frame corrente|-   Passa a un altro processo<br />-   Sospendi, riprendi o arresta l'applicazione<br />-   Passa a un altro thread del processo corrente<br />-   Passa a un altro stack frame del thread corrente<br />-   Contrassegna o rimuovi i contrassegni dei thread correnti<br />-   Mostra solo thread con flag<br />-   Mostra solo processo corrente|
|Finestra **Stack in parallelo**|-   Stack di chiamate per più thread in una finestra.<br />-   Stack frame Attivo per ogni thread.<br />-   Chiamanti e chiamati per ogni metodo.|-   Filtraggio di thread specificati<br />- Passare alla visualizzazione Attività<br />-   Contrassegno o rimozione del contrassegno di un thread<br />-   Zoom|
|Finestra **Espressione di controllo in parallelo**|-   Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.<br />-   Colonna frame, in cui una freccia indica il frame selezionato.<br />-   Colonna configurabile che consente di visualizzare il computer, il processo, la sezione, l'attività e il thread.|-   Contrassegno o rimozione del contrassegno di un thread<br />-   Visualizza solo thread con flag<br />-   Passa da un frame all'altro<br />-   Ordina una colonna<br />-   Raggruppa i thread<br />-   Blocca o sblocca i thread<br />-   Esporta i dati nella finestra Espressioni di controllo in parallelo|
|**Finestra** Attività|-   Visualizzare informazioni sugli oggetti <xref:System.Threading.Tasks.Task> inclusi ID attività, stato dell'attività (programmato, in esecuzione, in attesa, in deadlock) e il thread assegnato all'attività.<br />-   Percorso corrente nello stack di chiamate.<br />-   Delegato passato all'attività in fase di creazione|-   Passare all'attività corrente<br />-   Contrassegnare o rimuovere il contrassegno di un'attività<br />-   Bloccare o sbloccare un'attività|
|Finestra **Thread GPU**|-   Colonna flag, nella quale è possibile contrassegnare un thread al quale si desidera prestare particolare attenzione.<br />- Colonna thread corrente, in cui una freccia gialla indica il thread corrente.<br />-   Colonna **Conteggio thread**, che visualizza il numero di thread nella stessa posizione.<br />-   Colonna **Riga** che visualizza la riga di codice in cui si trova ciascun gruppo di thread.<br />-   Colonna **Indirizzo** che visualizza l'indirizzo dell'istruzione in cui si trova ciascun gruppo di thread.<br />-   Colonna **Posizione** che indica la posizione nel codice dell'indirizzo.<br />-   Colonna **Stato**, che indica se il thread è attivo o bloccato.<br />-   Colonna **Sezione**, che indica l'indice della sezione per i thread nella riga.|- Passare a un thread diverso<br />-   Visualizza una sezione e un thread specifici<br />-   Mostra o nasconde una colonna<br />-   Ordina per colonna<br />-   Raggruppa i thread<br />-   Blocca o sblocca i thread<br />-   Contrassegno o rimozione del contrassegno di un thread<br />-   Visualizza solo thread con flag|

## <a name="see-also"></a>Vedi anche

- [Connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)
- [Eseguire il debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)
- [Debug del codice GPU](../debugger/debugging-gpu-code.md)