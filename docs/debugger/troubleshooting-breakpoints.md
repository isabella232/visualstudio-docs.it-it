---
title: Risolvere i problemi relativi ai punti di interruzione nel debugger | Microsoft Docs
description: Se un punto di interruzione è disabilitato o non può essere impostato, viene visualizzato come cerchio vuoto. Di seguito sono riportate informazioni sui problemi che possono verificarsi durante l'impostazione dei punti di interruzione.
ms.custom: SEO-VS-2020
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0801a687529b5e0f8cdf34030460f0b5fe45bc91
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112386384"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Risolvere i problemi relativi ai punti di interruzione nel debugger Visual Studio

## <a name="breakpoint-warnings"></a>Avvisi dei punti di interruzione

Durante il debug, un punto di interruzione ha due possibili stati di visualizzazione: un cerchio rosso a tinta unita e un cerchio vuoto (con riempimento bianco). Se il debugger è in grado di impostare correttamente un punto di interruzione nel processo di destinazione, rimarrà un cerchio rosso pieno. Se il punto di interruzione è un cerchio vuoto, il punto di interruzione è disabilitato o si è verificato un avviso durante il tentativo di impostare il punto di interruzione. Per determinare la differenza, passare il puntatore del mouse sul punto di interruzione e verificare se è presente un avviso.

Le due sezioni seguenti descrivono gli avvisi principali e come risolverli.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nessun simbolo è stato caricato per questo documento"

Passare alla finestra **Moduli** **(Debug**  >  **moduli Windows)** e verificare se il modulo è  >  caricato.
* Se il modulo è caricato, controllare la colonna **Stato** simbolo per verificare se i simboli sono stati caricati.
  * Se i simboli non vengono caricati, controllare lo stato dei simboli per diagnosticare il problema. Nel menu di scelta rapida  di un modulo nella finestra Moduli fare clic su Informazioni di caricamento simboli **per** vedere dove il debugger cercava di provare a caricare i simboli. Per altre informazioni sul caricamento dei simboli, vedere [Specify Symbol (.pdb) and Source Files](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Se vengono caricati simboli, il PDB non contiene informazioni sui file di origine. Ecco alcune possibili cause:
    * Se i file di origine sono stati aggiunti di recente, verificare che sia in corso il caricamento di una versione aggiornata del modulo.
    * È possibile creare file PDB con striped usando l'opzione del linker **/PDBSTRIPPED.** I file PDB con striped non contengono informazioni sul file di origine. Verificare che si sta lavorando con un PDB completo e non con un PDB con striped.
    * Il file PDB è parzialmente danneggiato. Eliminare il file ed eseguire una compilazione pulita del modulo per provare a risolvere il problema.

* Se il modulo non è caricato, verificare quanto segue per individuare la causa:
  * Verificare di eseguire il debug del processo giusto.
  * Verificare che sia in esecuzione il debug del tipo di codice giusto. È possibile individuare il tipo di codice per cui il debugger è configurato per il debug nella **finestra** Processi (**Debug**  >  **di processi**  >  **Windows**). Ad esempio, se si sta tentando di eseguire il debug del codice C#, verificare che il debugger sia configurato per il tipo e la versione appropriati di .NET (ad esempio, Gestito (v4 ) e Gestito (v2 /v3 ) rispetto a Gestito \* \* \* (CoreCLR)).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… il codice sorgente corrente è diverso dalla versione incorporata in..."

Se un file di origine è stato modificato e l'origine non corrisponde più al codice di cui si esegue il debug, per impostazione predefinita il debugger non imposta punti di interruzione nel codice. In genere, questo problema si verifica quando viene modificato un file di origine, ma il codice sorgente non è stato ricompilato. Per risolvere questo problema, ricompilare il progetto. Se il sistema di compilazione pensa che il progetto sia già aggiornato anche se non lo è, è possibile forzare la ricompilazione del sistema del progetto salvando nuovamente il file di origine o pulendo l'output di compilazione del progetto prima della compilazione.

In rari scenari può essere necessario eseguire il debug senza codice sorgente corrispondente. Il debug senza codice sorgente corrispondente può generare un'esperienza di debug confusa, quindi assicurarsi che questa sia la modalità di procedere.

Per disabilitare questi controlli di sicurezza, eseguire una delle operazioni seguenti:
* Per modificare un singolo punto di interruzione, passare il mouse sull'icona del punto di interruzione nell'editor e fare clic sull'icona delle impostazioni (a forma di ingranaggio). All'editor viene aggiunta una finestra di anteprima. Nella parte superiore della finestra di anteprima è presente un collegamento ipertestuale che indica la posizione del punto di interruzione. Fare clic sul collegamento ipertestuale per consentire la modifica della posizione del punto di interruzione e selezionare Consenti che il codice sorgente **sia diverso da quello originale.**
* Per modificare questa impostazione per tutti i punti di interruzione, passare a **Opzioni**  >  **e impostazioni di debug.** Nella pagina **Debug/Generale** deselezionare l'opzione **Richiedi corrispondenza esatta dei file di origine con la versione originale** . Assicurarsi di riabilitare questa opzione al termine del debug.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Il punto di interruzione è stato impostato correttamente (nessun avviso), ma non è stato raggiunto

Questa sezione fornisce informazioni per risolvere i problemi quando il debugger non visualizza avvisi. Il punto di interruzione è un cerchio rosso pieno durante il debug attivo, ma il punto di interruzione non viene raggiunto.

Ecco alcuni aspetti da controllare:
1. Se il codice viene eseguito in più processi o più computer, assicurarsi di eseguire il debug del processo o del computer giusto.
2. Verificare che il codice sia in esecuzione. Per verificare che il codice sia in esecuzione, aggiungere una chiamata a `System.Diagnostics.Debugger.Break` (C#/VB) o (C++) alla riga di codice in cui si sta tentando di impostare il punto di interruzione e quindi ricompilare `__debugbreak` il progetto.
3. Se si esegue il debug di codice ottimizzato, assicurarsi che la funzione in cui è impostato il punto di interruzione non venga inline in un'altra funzione. Il `Debugger.Break` test descritto nel controllo precedente può funzionare anche per testare questo problema.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Un punto di interruzione è stato eliminato ma si continua a raggiungerlo quando si avvia nuovamente il debug

Se è stato eliminato un punto di interruzione durante il debug, è possibile che il punto di interruzione venga raggiunto nuovamente al successivo avvio del debug. Per evitare di raggiungere il punto di interruzione, accertarsi che tutte le istanze del punto di interruzione vengano rimosse dalla finestra **Punti di interruzione** .
