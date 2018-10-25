---
title: Strumenti per eseguire il debug di thread e processi | Microsoft Docs
ms.custom: ''
ms.date: 04/21/2017
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: cb8c8abab1dc4b8f5778ed4b76688f8a3946e461
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49888829"
---
# <a name="tools-to-debug-threads-and-processes-in-visual-studio"></a>Strumenti per eseguire il debug di thread e processi in Visual Studio
*Thread* e *processi* sono concetti correlati in scienze informatiche. Entrambi rappresentano infatti sequenze di istruzioni che devono essere eseguite in un ordine specifico. Le istruzioni incluse in thread o processi distinti possono tuttavia essere eseguite in parallelo.  
  
 I processi sono disponibili nel sistema operativo e corrispondono a ciò che gli utenti visualizzano sotto forma di programmi o applicazioni. I thread sono invece disponibili nei processi. Per questo motivo, i thread sono talvolta detti *processi leggeri*. Ciascun processo è costituito da uno o più thread.  
  
 La presenza di più processi consente a un computer di eseguire più attività contemporaneamente. La presenza di più thread consente invece a un processo di suddividere le operazioni da eseguire in parallelo. In un computer con più processori, i processi o i thread possono essere eseguiti in processori diversi consentendo l'effettiva elaborazione in parallelo.  
  
 Una perfetta elaborazione in parallelo non è sempre possibile. È talvolta necessario sincronizzare i thread. È inoltre possibile che un thread debba attendere un risultato di un altro thread o disporre di accesso esclusivo a una risorsa utilizzata da un altro thread. I problemi di sincronizzazione costituiscono una causa comune di bug in applicazioni con multithreading. È talvolta possibile che i thread rimangano in attesa di una risorsa che non diviene mai disponibile, Ciò comporta una condizione denominata *deadlock*.  
  
 Nel debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sono disponibili strumenti efficaci e di facile utilizzo per il debug di thread e processi.  
  
## <a name="tools-and-features"></a>Strumenti e funzionalità
Gli strumenti necessari per usare in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dipendono dal tipo di codice si sta tentando di eseguire il debug:

- Per i processi, sono i principali strumenti di **Connetti a processo** nella finestra di dialogo il **processi** finestra e il **posizione di Debug** sulla barra degli strumenti.

- Per i thread sono i principali strumenti per il debug dei thread di **thread** (finestra), i marcatori dei thread nelle finestre di origine **stack in parallelo** finestra **espressioni di controllo parallela** finestra e il **posizione di Debug** sulla barra degli strumenti.  
  
- Per il codice che usa il <xref:System.Threading.Tasks.Task> nella [Task Parallel Library (TPL)](/dotnet/standard/parallel-programming/task-parallel-library-tpl), il [Runtime di concorrenza](/cpp/parallel/concrt/concurrency-runtime/) (codice nativo), i principali strumenti per il debug di applicazioni multithreading sono le **Stack in parallelo** finestra, il **espressioni di controllo parallelo** finestra e il **attività** finestra (il **attività** finestra supporta anche il Oggetto di promessa JavaScript).

- Per il debug dei thread nella GPU, lo strumento principale è il **thread GPU** windows.  
  
  Nella tabella riportata di seguito sono illustrate le informazioni disponibili e le operazioni che è possibile eseguire con ciascuno strumento:  
  
|Interfaccia utente|Informazioni disponibili|Operazioni eseguibili|  
|--------------------|---------------------------|-----------------------------|  
|**Connetti a processo** nella finestra di dialogo|Processi disponibili cui è possibile eseguire la connessione:<br /><br /> -Nome processo (.exe)<br />-Numero di ID processi<br />: Titolo sulla barra dei menu<br />-Tipo (Managed v4.0; Managed v2.0, v1.1, v1.0; x86; x64; IA64)<br />-Nome utente (nome account)<br />: Numero di sessione|Selezione di un processo a cui connettersi<br /><br /> Selezione di un computer remoto<br /><br /> Modifica del tipo di trasporto per la connessione a computer remoti|  
|**Processi** finestra|Processi collegati:<br /><br /> : Nome processo<br />-Numero di ID processi<br />-Path per l'elaborazione .exe<br />: Titolo sulla barra dei menu<br />-Stato (Interrompi. In esecuzione)<br />-Debug (nativi e gestiti e così via.)<br />-Tipo di trasporto (predefinito, nativo senza autenticazione)<br />-Qualificatore di trasporto (computer remoto)|Strumenti:<br /><br /> -Attach<br />-Scollegamento<br />-Termina<br /><br /> Menu di scelta rapida:<br /><br /> -Attach<br />-Scollegamento<br />-Disconnetti al termine del debug arrestato<br />-Termina|  
|**Thread** finestra|Thread nel processo corrente:<br /><br /> -ID thread<br />-ID gestiti<br />-Categoria (thread principale, thread dell'interfaccia, gestore delle chiamate a procedura remota o thread di lavoro)<br />-Nome thread<br />-Ubicazione in cui viene creato thread<br />-Priorità<br />: Maschera di affinità<br />-Numero sospesi<br />: Nome processo<br />-Indicatore flag<br />-Indicatore di sospensione|Strumenti:<br /><br /> -Ricerca<br />-Stack di chiamate Cerca<br />-Contrassegna Just My Code<br />-Contrassegna selezione moduli personalizzata<br />-Raggruppa per<br />-Le colonne<br />-Espandi/Comprimi stack di chiamate<br />-Espandere/comprimere gruppi<br />-Blocca/Sblocca thread<br /><br /> Menu di scelta rapida:<br /><br /> -Mostra thread nell'origine<br />-Passare a un thread<br />-Bloccare un thread in esecuzione<br />-Sblocca un thread bloccato<br />-Contrassegnare un thread per Studio aggiuntivo<br />-Rimuovi flag del thread<br />-Rinomina thread<br />-Mostra / Nascondi thread<br /><br /> Altre azioni:<br /><br /> -Visualizzare lo stack di chiamate per un thread in un suggerimento dati|  
|Finestra di origine|Gli indicatori dei thread all'estrema sinistra indicano thread singoli o più thread (disattivato per impostazione predefinita, attivata tramite il menu di scelta rapida **thread** finestra)|Menu di scelta rapida:<br /><br /> -Passare a un thread<br />-Contrassegnare un thread per Studio aggiuntivo<br />-Rimuovi flag del thread|  
|**Posizione di debug** sulla barra degli strumenti|-Processo corrente<br />-Sospende l'applicazione<br />-Riprendere l'applicazione<br />-Sospendi e arresta l'applicazione<br />-Current thread<br />-Attiva/Disattiva corrente dello stato del flag thread<br />-Mostra solo thread con flag<br />-Mostra solo processo corrente<br />-Corrente dello stack frame|-Passare a un altro processo<br />-Sospendere, riprendere o arrestare l'applicazione<br />-Passare a un altro thread nel processo corrente<br />-Passare a un altro stack frame nel thread corrente<br />-Contrassegnare o rimuovere i flag dei thread correnti<br />-Mostra solo thread con flag<br />-Mostra solo processo corrente|  
|**Stack in parallelo** finestra|-Stack di chiamate per più thread in una finestra.<br />-Stack frame attivo per ogni thread.<br />-I chiamanti e chiamati per ogni metodo.|-Filtrare i thread specificati<br />-Passare alla visualizzazione attività<br />-Contrassegnare o rimuovere un thread<br />-Eseguire lo zoom avanti|   
|**Espressioni di controllo in parallelo** finestra|-La colonna flag, in cui è possibile contrassegnare un thread che si desidera prestare particolare attenzione.<br />-La colonna frame, in cui una freccia indica il frame selezionato.<br />-Colonna configurabile che consente di visualizzare la macchina, processo, tile, attività e thread.|-Contrassegnare o rimuovere un thread<br />-Visualizza solo thread con flag<br />-Passare da un frame<br />-Ordinare una colonna<br />-Thread gruppo<br />-Blocca o Sblocca thread<br />-esportare i dati nella finestra Espressioni di controllo parallela| 
|**Attività** finestra|-Visualizzare le informazioni relative <xref:System.Threading.Tasks.Task> oggetti inclusi ID attività, lo stato dell'attività (programmato, in esecuzione, in attesa, in deadlock) e il thread assegnato all'attività.<br />-Percorso corrente nello stack di chiamate.<br />-Delegato passato all'attività al momento della creazione|-Passare all'attività corrente<br />-Contrassegnare o rimuovere un'attività<br />-Bloccare o sbloccare un'attività|  
|**Thread GPU** finestra|-La colonna flag, in cui è possibile contrassegnare un thread che si desidera prestare particolare attenzione.<br />-Thread colonna corrente, in cui una freccia gialla indica che il thread corrente.<br />-il **conteggio dei Thread** colonna, che visualizza il numero di thread nella stessa posizione.<br />-il **riga** colonna, che consente di visualizzare la riga di codice in cui si trova ciascun gruppo di thread.<br />-il **indirizzo** colonna, che consente di visualizzare l'indirizzo dell'istruzione in cui si trova ciascun gruppo di thread.<br />-il **posizione** colonna, ovvero la posizione nel codice dell'indirizzo.<br />-il **stato** colonna che indica se il thread è attivo o bloccato.<br />-il **riquadro** colonna che mostra l'indice della sezione per i thread nella riga.|-Modifica a un altro thread<br />: Consente di visualizzare un riquadro specifico e thread<br />-Visualizza o nasconde una colonna<br />-Ordina per colonna<br />-Thread gruppo<br />-Blocca o Sblocca thread<br />-Contrassegnare o rimuovere un thread<br />-Visualizza solo thread con flag|  
  
## <a name="see-also"></a>Vedere anche  
 [Collegamento a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Debug di applicazioni multithreading](../debugger/debug-multithreaded-applications-in-visual-studio.md)   
 [Debug del codice GPU](../debugger/debugging-gpu-code.md)