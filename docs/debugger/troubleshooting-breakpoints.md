---
title: Risolvere i problemi relativi ai punti di interruzione nel debugger | Microsoft Docs
description: Se un punto di interruzione è disabilitato o non può essere impostato, viene visualizzato come cerchio vuoto. Esaminare qui le informazioni sui problemi che possono verificarsi durante l'impostazione dei punti di interruzione.
ms.custom: SEO-VS-2020, seodec18
ms.date: 01/23/2018
ms.topic: troubleshooting
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a07f92eccd7884ea3cc3871d04285a82cb5cb62e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148052"
---
# <a name="troubleshoot-breakpoints-in-the-visual-studio-debugger"></a>Risolvere i problemi relativi ai punti di interruzione nel debugger di Visual Studio

## <a name="breakpoint-warnings"></a>Avvisi del punto di interruzione

Quando si esegue il debug, un punto di interruzione ha due possibili stati di visualizzazione: un cerchio rosso continuo e un cerchio vuoto (riempimento bianco). Se il debugger è in grado di impostare correttamente un punto di interruzione nel processo di destinazione, resterà in un cerchio rosso a tinta unita. Se il punto di interruzione è un cerchio vuoto, il punto di interruzione è disabilitato o si è verificato un avviso durante il tentativo di impostare il punto di interruzione. Per determinare la differenza, passare il puntatore del mouse sul punto di interruzione e verificare se è presente un avviso.

Nelle due sezioni seguenti vengono descritti gli avvisi principali e come risolverli.

### <a name="no-symbols-have-been-loaded-for-this-document"></a>"Nessun simbolo è stato caricato per questo documento"

Passare alla finestra **moduli** (**eseguire il debug** dei  >    >  **moduli** di Windows) e verificare se il modulo è stato caricato.
* Se il modulo è caricato, controllare la colonna **stato simboli** per verificare se i simboli sono stati caricati.
  * Se i simboli non vengono caricati, controllare lo stato del simbolo per diagnosticare il problema. Dal menu di scelta rapida di un modulo nella finestra **moduli** fare clic su informazioni sul caricamento dei simboli **...** per vedere il punto in cui il debugger ha cercato di provare a caricare i simboli. Per ulteriori informazioni sul caricamento dei simboli, vedere [specificare i file di simboli (con estensione pdb) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).
  * Se i simboli vengono caricati, il PDB non contiene informazioni sui file di origine. Di seguito sono riportate alcune possibili cause:
    * Se i file di origine sono stati aggiunti di recente, verificare che sia in corso il caricamento di una versione aggiornata del modulo.
    * È possibile creare PDB rimossi usando l'opzione del linker **/PDBSTRIPPED** . I PDB rimossi non contengono informazioni sul file di origine. Verificare di usare un PDB completo e non un PDB rimosso.
    * Il file PDB è parzialmente danneggiato. Eliminare il file ed eseguire una compilazione pulita del modulo per tentare di risolvere il problema.

* Se il modulo non è caricato, controllare quanto segue per individuare la ragione:
  * Confermare che si sta eseguendo il debug del processo corretto.
  * Verificare di eseguire il debug del tipo di codice corretto. È possibile individuare il tipo di codice per il quale il debugger è configurato per eseguire il debug nella finestra **processi** (**debug** dei processi di  >  **Windows**  >  ). Se, ad esempio, si sta provando a eseguire il debug del codice C#, verificare che il debugger sia configurato per il tipo e la versione appropriati di .NET (ad esempio, Managed (v4 \* ) e Managed (v2 \* /v3 \* ) rispetto a Managed (CoreCLR).

### <a name="-the-current-source-code-is-different-from-the-version-built-into"></a>"… il codice sorgente corrente è diverso dalla versione compilata in... "

Se un file di origine è stato modificato e l'origine non corrisponde più al codice di cui si sta eseguendo il debug, per impostazione predefinita i punti di interruzione nel codice non verranno impostati dal debugger. In genere, questo problema si verifica quando viene modificato un file di origine, ma il codice sorgente non è stato ricompilato. Per risolvere il problema, ricompilare il progetto. Se il sistema di compilazione ritiene che il progetto sia già aggiornato anche se non lo è, è possibile forzare la ricompilazione del sistema del progetto salvando di nuovo il file di origine o pulendo l'output di compilazione del progetto prima della compilazione.

In rari scenari, è consigliabile eseguire il debug senza avere un codice sorgente corrispondente. Il debug senza il codice sorgente corrispondente può causare un'esperienza di debug confusionaria, quindi assicurarsi che questo sia il modo in cui si vuole continuare.

Per disabilitare i controlli di sicurezza, eseguire una delle operazioni seguenti:
* Per modificare un singolo punto di interruzione, passare il puntatore del mouse sull'icona del punto di interruzione nell'editor e fare clic sull'icona Impostazioni (ingranaggio). Viene aggiunta una finestra di anteprima all'editor. Nella parte superiore della finestra di anteprima è disponibile un collegamento ipertestuale che indica la posizione del punto di interruzione. Fare clic sul collegamento ipertestuale per consentire la modifica della posizione del punto di interruzione e selezionare **Consenti che il codice sorgente sia diverso dall'originale**.
* Per modificare questa impostazione per tutti i punti di interruzione, passare a  >  **Opzioni e impostazioni** di debug. Nella pagina **Debug/Generale** deselezionare l'opzione **Richiedi corrispondenza esatta dei file di origine con la versione originale** . Assicurarsi di riabilitare questa opzione al termine del debug.

## <a name="the-breakpoint-was-successfully-set-no-warning-but-didnt-hit"></a>Il punto di interruzione è stato impostato (nessun avviso) ma non è stato raggiunto

In questa sezione vengono fornite informazioni per la risoluzione dei problemi quando il debugger non visualizza alcun avviso: il punto di interruzione è un cerchio rosso a tinta unita durante il debug attivo, ma non viene raggiunto il punto di interruzione.

Ecco alcuni aspetti da controllare:
1. Se il codice viene eseguito in più processi o più di un computer, assicurarsi di eseguire il debug del processo o del computer corretto.
2. Verificare che il codice sia in esecuzione. Per verificare che il codice sia in esecuzione, aggiungere una chiamata a `System.Diagnostics.Debugger.Break` (C#/VB) o `__debugbreak` (C++) alla riga di codice in cui si sta provando a impostare il punto di interruzione e quindi ricompilare il progetto.
3. Se si esegue il debug di codice ottimizzato, assicurarsi che la funzione in cui è impostato il punto di interruzione non venga inline in un'altra funzione. Il `Debugger.Break` test descritto nella verifica precedente può funzionare anche per testare questo problema.

## <a name="i-deleted-a-breakpoint-but-i-continue-to-hit-it-when-i-start-debugging-again"></a>Un punto di interruzione è stato eliminato ma si continua a raggiungerlo quando si avvia nuovamente il debug

Se il punto di interruzione è stato eliminato durante il debug, è possibile raggiungere nuovamente il punto di interruzione al successivo avvio del debug. Per evitare di raggiungere il punto di interruzione, accertarsi che tutte le istanze del punto di interruzione vengano rimosse dalla finestra **Punti di interruzione** .
