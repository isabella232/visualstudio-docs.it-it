---
title: 'Area di test 3: controllare Out-Undo estrazione | Microsoft Docs'
description: Questa area di test del plug-in del controllo del codice sorgente illustra la modifica e il ripristino degli elementi dall'archivio delle versioni usando i comandi Estrai e Annulla estrazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bb59b0342d67ab9118ffcdba74c177106fcceea0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99898116"
---
# <a name="test-area-3-check-outundo-checkout"></a>Area di test 3: estrarre o annullare l'estrazione
Questa area di test del plug-in del controllo del codice sorgente illustra la modifica e il ripristino degli elementi dall'archivio delle versioni **usando i comandi Estrai** e **Annulla estrazione** .

**Estrai**: contrassegna un elemento nell'archivio versioni come estratto, modifica la copia locale in lettura/scrittura.

**Annulla estrazione**: contrassegna un elemento nell'archivio versioni come archiviato, ripristina lo stato della copia locale prima dell'estrazione (a seconda delle opzioni).

## <a name="command-menu-access"></a>Accesso al menu dei comandi

[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nei test case vengono utilizzati i percorsi dei menu Integrated Development Environment seguenti.

##### <a name="check-out"></a>Estrai:

- **File**, **controllo del codice sorgente**, **Estrai**.

- **File**, **Estrai**.

- Menu di scelta rapida, **Estrai**.

- Annulla estrazione: **file**, **controllo del codice sorgente**, **Annulla estrazione**.

## <a name="common-expected-behavior"></a>Comportamento previsto comune

- Dopo l'operazione di estrazione, i file di destinazione e/o le cartelle vengono contrassegnati come estratti nell'archivio delle versioni.

- L'archivio versioni attribuisce il checkout all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

## <a name="test-cases"></a>Test case

Di seguito sono riportati i test case specifici per l'area di test Estrai/Annulla estrazione.

### <a name="case-3a-check-out"></a>Caso 3A: estrazione

Questa sezione è incentrata sull'operazione del comando di estrazione.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Estrai un progetto client esclusivo (COE)|1. creare un progetto client.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. esaminare l'intero progetto in modo esclusivo (**file**, **Estrai**).|Si verifica l'errore.|
|Estrai un file System o un progetto Web IIS locale esclusivo (COE)|1. impostare la connessione al server Web per la condivisione file in **strumenti**, **Opzioni**, **progetti** e **Impostazioni Web**.<br />2. creare un progetto Web.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. esaminare l'intero progetto in modo esclusivo (**file**, **controllo del codice sorgente**, **estrazione**).|Si verifica l'errore.|
|Estrarre gli elementi della soluzione in una soluzione (nuovo metodo per la gestione di altri file)|1. creare una soluzione vuota.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. consultare la soluzione.<br />4. aggiungere diversi elementi di soluzione.<br />5. archiviare tutti gli elementi appena aggiunti.<br />6. Selezionare più elementi della soluzione.<br />7. vedere gli elementi selezionati (menu di scelta rapida, **Estrai**).|I file selezionati vengono estratti.|
|Estrai versione locale (se il plug-in in test supporta questa funzionalità)|1. utente 1: creare un progetto client.<br />2. utente 1: aggiungere la soluzione al controllo del codice sorgente.<br />3. utente 2: aprire la soluzione dal controllo del codice sorgente in un'altra posizione.<br />4. utente 2: estrarre un file.<br />5. utente 2: modificare il file.<br />6. utente 2: archiviare il file.<br />7. utente 1: estrarre la versione locale del file (vedere l'opzione **Estrai versione locale** avanzata nella finestra di dialogo **Estrai** ).|La versione locale del file è stata estratta.<br /><br /> Le modifiche apportate dall'utente 2 non vengono applicate al file utente 1.|

### <a name="case-3b-disconnected-check-out"></a>Caso 3B: estrazione disconnessa

Il funzionamento in modalità disconnessa consente agli utenti di un certo livello di supporto del controllo del codice sorgente continuato quando non è collegato direttamente a un archivio versioni. Questa operazione viene eseguita memorizzando localmente nella cache tutte le informazioni rilevanti sulla soluzione e sui progetti integrata.

Le operazioni di estrazione esclusive possono verificarsi solo quando si è connessi all'archivio del controllo del codice sorgente. Le operazioni di estrazione condivise possono verificarsi in qualsiasi momento, sia connesse che disconnesse. Pertanto, quando si è disconnessi dall'archivio delle versioni, viene abilitato solo il comando **Estrai condivisi** (cos). Durante la disconnessione, l' **annullamento dell'estrazione** è disabilitato perché non è possibile recuperare la versione precedente per sostituire le modifiche apportate dall'utente.

Quando l'utente si riconnette all'archivio delle versioni, gli Stati di estrazione di tutti i progetti e le soluzioni integrate sono sincronizzati. Questa operazione esegue gli aggiornamenti necessari all'archivio per le estrazioni eseguite dall'utente. Una volta eseguita la sincronizzazione, l'utente può continuare a funzionare normalmente (connesso).

#### <a name="expected-behavior"></a>Comportamento previsto

- Non è possibile usare il comando **Estrai esclusivamente** durante la disconnessione dall'archivio delle versioni.

- Impossibile utilizzare il comando **Annulla estrazione** durante la disconnessione dall'archivio versioni.

- Il comando di **estrazione condivisa** funziona.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Durante la disconnessione, Estrai un file, quindi Connetti per la sincronizzazione|1. disconnettere un progetto controllato utilizzando la finestra di dialogo Modifica controllo del codice sorgente (**file**, **controllo del codice sorgente**, **modifica controllo del codice sorgente**).<br />2. controllare un file in uscita.<br />3. fare clic su Estrai (disconnesso) nella finestra di dialogo di avviso.<br />4. modificare il file.<br />5. connettersi tramite la finestra di dialogo Modifica controllo del codice sorgente.<br />6. ottenere la versione più recente del file modificato.|Comportamento previsto comune|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3C: modifica query/Salva query (QEQS)
 Gli elementi sottoposti al controllo del codice sorgente vengono rilevati per modifiche, modifiche e salvataggi per consentire agli utenti di gestire facilmente i propri file. Quando viene modificato un elemento controllato "archiviato", QEQS intercetta il tentativo di modifica e chiede all'utente se desidera estrarre il file per modificarlo. A seconda **degli strumenti**, impostazioni **Opzioni** , l'utente è obbligato a estrarre il file per modificare o potrebbe essere autorizzato a modificare una copia in memoria ed estrarlo in un secondo momento. Se gli **strumenti** dell'utente, l'impostazione delle **Opzioni** non è impostata per visualizzare la finestra di dialogo Estrai ed è sufficiente estrarlo, quando l'utente esegue la modifica, il file viene automaticamente verificato, quando possibile.

#### <a name="expected-behavior"></a>Comportamento previsto

- Dopo l'operazione di estrazione, i file di destinazione e/o le cartelle vengono contrassegnati come estratti nell'archivio delle versioni.

- L'archivio versioni attribuisce il controllo all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

- La copia locale del file o della cartella di destinazione è scrivibile.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Modificare il file di testo archiviato|1. creare un nuovo progetto contenente un file di testo.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. impostare **gli strumenti**, le **Opzioni**, il **controllo del codice sorgente**, **consentire la modifica dei file in sola lettura su disco** per deselezionarlo.<br />4. impostare **gli strumenti**, le **Opzioni**, il **controllo del codice sorgente**, la **richiesta di estrazione** nella casella combinata **modifica file archiviati in** .<br />5. impostare **gli strumenti**, le **Opzioni**, il **controllo del codice sorgente**, la **richiesta di estrazione** nella casella combinata **Salva file archiviati** .<br />6. Aprire il file di testo nell'editor, provare a digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. fare clic su **Annulla** nella finestra di dialogo **Estrai per la modifica** . Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />8. impostare **gli strumenti**, le **Opzioni**, il **controllo del codice sorgente**, **consentire la modifica dei file in sola lettura su disco** .<br />9. Aprire il file di progetto nell'editor, provare a digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />10. fare clic su **modifica** nella finestra di dialogo **Estrai per la modifica** . Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />11. modificare il file di testo e provare a salvarlo.|`Result of step 6:`<br /><br /> Viene visualizzata la finestra di dialogo Estrai per la modifica.<br /><br /> `Result of step 7:`<br /><br /> Il file non è stato modificato.<br /><br /> `Result of step 9:`<br /><br /> Viene visualizzata la finestra di dialogo Estrai per la modifica.<br /><br /> `Result of step 10:`<br /><br /> È possibile modificare il file di progetto in memoria.<br /><br /> `Result of step 11:`<br /><br /> In Salva viene visualizzata la finestra di dialogo Estrai al salvataggio.|
|Modificare un file di soluzione archiviato|Ripetere i passaggi come descritto nel test precedente, ma anziché modificare un file di testo, modificare la soluzione cambiando le proprietà della soluzione.|Uguale al test precedente|
|Modificare un file di progetto archiviato|Ripetere i passaggi come descritto nel test precedente, ma anziché modificare un file di testo, modificare il progetto modificando le proprietà del progetto.|Uguale al test precedente.|

### <a name="case-3d-silent-check-out"></a>Caso 3D: estrazione invisibile all'utente
 In questa area secondaria vengono descritti gli scenari in cui la finestra di dialogo **Estrai** non viene visualizzata per gli **strumenti**, le **Opzioni** e **le impostazioni di controllo del codice sorgente** dell'utente.

#### <a name="expected-behavior"></a>Comportamento previsto

- Dopo l'operazione di estrazione, i file di destinazione e/o le cartelle vengono contrassegnati come estratti nell'archivio delle versioni.

- L'archivio versioni attribuisce il controllo all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

- La copia locale del file o della cartella di destinazione è scrivibile.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Estrazione invisibile all'utente per un file|1. impostare **gli strumenti**, le **Opzioni**, il **controllo del codice sorgente** per l' **estrazione automatica dei file durante la modifica**.<br />2. creare un nuovo progetto con un file.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. Estrarre il file.|Il file viene estratto automaticamente (nessuna interfaccia utente).|
|Estrazione invisibile all'utente per un progetto|1. impostare **gli strumenti**, le **Opzioni**, il **controllo del codice sorgente** per l' **estrazione automatica dei file durante la modifica**.<br />2. creare un nuovo progetto.<br />3. aggiungere la soluzione al controllo del codice sorgente.<br />4. vedere il progetto.|Il file viene estratto automaticamente (nessuna interfaccia utente).|

### <a name="case-3e-undo-check-out"></a>Caso 3e: Annulla estrazione
 **Annulla estrazione** viene usato per annullare lo stato di estrazione di un file ed evitare di archiviare le modifiche apportate al file.

#### <a name="expected-behavior"></a>Comportamento previsto

- Il valore predefinito è basato sull'impostazione della **versione locale di estrazione** dell'utente. Se l'utente ha scelto di estrarre la versione locale, l'impostazione predefinita per Annulla estrazione consiste nel ripristinare sempre la versione estratto.

- Al momento dell'accettazione del rollback, le icone in **Esplora soluzioni** vengono aggiornate per i file interessati e l'elemento viene rimosso dalla finestra **archiviazioni in sospeso** .

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Annulla l'estrazione di un singolo file estratto in modo esclusivo|1. creare un progetto client.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre un file in modo esclusivo.<br />4. modificare il file.<br />5. annullare l'estrazione (**file**, **controllo del codice sorgente**, **annullamento estrazione**).|Comportamento previsto comune.|
|Annulla l'estrazione di un singolo file estratto condiviso|1. creare un progetto client.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre un file condiviso.<br />4. modificare il file.<br />5. annullare l'estrazione (**file**, **controllo del codice sorgente**, **annullamento estrazione**).|Comportamento previsto comune.|
|Annulla l'estrazione di un progetto dopo l'aggiunta di file al progetto|1. creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2. vedere il progetto.<br />3. aggiungere un file al progetto.<br />4. annullare l'estrazione del progetto.|Il file aggiunto è stato rimosso dal progetto in Esplora soluzioni.<br /><br /> Il progetto non è più estratto.|
|Annulla l'estrazione di un progetto dopo l'eliminazione dei file dal progetto|1. creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2. vedere il progetto.<br />3. eliminare un file dal progetto.<br />4. annullare l'estrazione del progetto.|Il file eliminato viene visualizzato sotto il progetto in Esplora soluzioni.<br /><br /> Il progetto non è più estratto.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
