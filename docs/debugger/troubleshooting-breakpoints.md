---
title: Risolvere i punti di interruzione nel debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: a2afbff14be944e17a26df09d041d9267ac5cb87
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53989909"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Risolvere i punti di interruzione nel Debugger di Visual Studio

## <a name="breakpoint-warnings"></a>Avvisi di punto di interruzione

Durante il debug, un punto di interruzione ha due possibili stati di visualizzazione: un cerchio rosso e un vuoti (white riempiti) cerchio. Se il debugger è in grado di impostare correttamente un punto di interruzione nel processo di destinazione, rimarranno in un cerchio rosso. Se il punto di interruzione è un cerchio vuoto, il punto di interruzione è disabilitato o avviso durante il tentativo di impostare il punto di interruzione. Per determinare la differenza, passare il puntatore sul punto di interruzione e verificare se è presente un avviso.

Le due sezioni seguenti descrivono gli avvisi principali e come risolverli. 

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nessun simbolo è stato caricato per questo documento" 

Andare alla **moduli** finestra (**Debug** > **Windows** > **moduli**) e controllare se il modulo è caricato.  
* Se il modulo viene caricato, controllare la **stato simboli** colonna per verificare se sono stati caricati i simboli. 
  * Se non vengono caricati i simboli, controllare lo stato di simboli per diagnosticare il problema. Dal menu di scelta rapida in un modulo nel **moduli** finestra, fare clic su **informazioni sul caricamento simboli...**  per vedere in cui il debugger valutato per tentare di caricare i simboli. Per altre informazioni sul caricamento dei simboli, vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  * Se i simboli sono caricati, il file PDB non contiene informazioni sui file di origine. Ecco alcune possibili cause: 
    * Se i file di origine aggiunti di recente, verificare che venga caricata una versione aggiornata del modulo.  
    * È possibile creare i PDB rimossi usando il **/PDBSTRIPPED** l'opzione del linker. I PDB rimossi non contengono informazioni sui file di origine. Confermare il che uso con una procedura completa di PDB e non un PDB rimosso.  
    * Il file PDB è parzialmente danneggiato. Eliminare il file ed eseguire una compilazione pulita del modulo per tentare di risolvere il problema. 

* Se non viene caricato un modulo, verificare quanto segue per individuare la causa: 
  * Confermare che si esegue il debug del processo appropriato. 
  * Verificare che si esegue il debug del tipo appropriato di codice. È possibile scoprire che tipo di debugger è configurato per eseguire il debug nel codice il **processi** finestra (**Debug** > **Windows**  >  **Processi**). Ad esempio, se si sta tentando di eseguire il debug C# del codice, verificare che il debugger sia configurato per il tipo appropriato di .NET Framework (ad esempio, gestito (v4\*) e gestito (v2\*/v3\*) e gestito (CoreCLR)) . 

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… il codice sorgente corrente è diverso da quello della versione compilata in..." 

Se è stato modificato un file di origine e l'origine non corrisponde più il codice che si esegue il debug, il debugger non imposterà i punti di interruzione nel codice per impostazione predefinita. Solitamente, questo problema si verifica quando viene modificato un file di origine, ma il codice sorgente non è stato ricompilato. Per risolvere questo problema, ricompilare il progetto. Se il sistema di compilazione considera che il progetto è già aggiornato anche se non lo è, è possibile forzare il sistema di progetto per rigenerare, salvare di nuovo il file di origine o mediante l'eliminazione del progetto di compilazione output prima della compilazione. 

In rari casi, è possibile eseguire il debug senza la necessità di codice sorgente corrispondente. Debug senza corrispondente codice sorgente può lead un confusi esecuzione del debug, pertanto assicurarsi che che si tratta di come si desidera procedere.  

Per disattivare questi controlli di sicurezza, effettuare una delle operazioni seguenti: 
* Per modificare un singolo punto di interruzione, passare il mouse sull'icona di punto di interruzione nell'editor e fare clic sull'icona delle impostazioni (ingranaggio). Una finestra di anteprima viene aggiunto all'editor. Nella parte superiore della finestra di anteprima, è presente un collegamento ipertestuale che indica la posizione del punto di interruzione. Fare clic sul collegamento ipertestuale per consentire la modifica della posizione punto di interruzione e controllare **il codice sorgente può essere diverso dall'originale**.
* Per modificare questa impostazione per tutti i punti di interruzione, passare alle **Debug** > **opzioni e impostazioni**. Nella pagina **Debug/Generale** deselezionare l'opzione **Richiedi corrispondenza esatta dei file di origine con la versione originale** . Assicurarsi che per abilitarla di nuovo questa opzione dopo aver terminato il debug. 

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Il punto di interruzione è stato impostato correttamente (nessun avviso), ma non è stato raggiunto 

In questa sezione fornisce informazioni per risolvere i problemi quando il debugger non è visualizzati gli avvisi: il punto di interruzione è un cerchio rosso durante il debug, ma non è in corso raggiunto il punto di interruzione. 

Ecco alcuni aspetti da controllare: 
1. Se il codice viene eseguito nel processo più di una o più computer, assicurarsi che il debug viene eseguito il giusto processo o computer.  
2. Verificare che il codice sia in esecuzione. Per verificare che il codice sia in esecuzione, aggiungere una chiamata a `System.Diagnostics.Debugger.Break` (C#/VB) o `__debugbreak` (C++) per la riga di codice in cui si sta tentando di impostare il punto di interruzione e quindi ricompilare il progetto. 
3. Se si esegue il debug del codice ottimizzato, assicurarsi che la funzione in cui è impostato il punto di interruzione non è in corso resa inline in un'altra funzione. Il `Debugger.Break` test descritto nel controllo di precedenti possono essere usati per testare anche il problema. 

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Un punto di interruzione è stato eliminato ma si continua a raggiungerlo quando si avvia nuovamente il debug 

Se si elimina un punto di interruzione durante il debug, è possibile raggiungere il punto di interruzione nuovamente al successivo che avvio del debug. Per evitare di raggiungere il punto di interruzione, accertarsi che tutte le istanze del punto di interruzione vengano rimosse dalla finestra **Punti di interruzione** .  
