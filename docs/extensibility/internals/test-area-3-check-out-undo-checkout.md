---
title: 'Area di test 3: Check Out-Undo Checkout Documenti Microsoft'
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
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5365da1e342df5aea9c1b1cd2ae5a446baea57f1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704614"
---
# <a name="test-area-3-check-outundo-checkout"></a>Area di test 3: Estrai/Annulla estrazione
Questa area di test del plug-in del controllo del codice sorgente illustra la modifica e il ripristino di elementi dall'archivio versioni tramite i comandi **Estrai** e **Annulla estrazione.**

**Estrai**: Contrassegna un elemento nell'archivio versioni come estratto, modifica la copia locale in lettura/scrittura.

**Annulla estrazione**: Contrassegna un elemento nell'archivio versioni come archiviato, ripristina lo stato della copia locale prima dell'estrazione (a seconda delle opzioni).

## <a name="command-menu-access"></a>Accesso al menu dei comandi

Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case vengono utilizzati i percorsi di menu dell'ambiente di sviluppo integrato seguenti.

##### <a name="check-out"></a>Estrai:

- **File**, **Controllo del codice sorgente**, **Estrai**.

- **File**, **Estrai**.

- Menu di scelta rapida, **Estrai**.

- Annulla estrazione: **File**, **Controllo del codice sorgente**, Annulla **estrazione**.

## <a name="common-expected-behavior"></a>Comportamento previsto comuneCommon Expected Behavior

- Dopo l'operazione di estrazione, i file e/o le cartelle di destinazione vengono contrassegnati come estratti nell'archivio versioni.

- L'archivio versione attribuisce l'estrazione all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

## <a name="test-cases"></a>Test case

Di seguito sono riportati i test case specifici per l'area di test Checkout/Undo Checkout.

### <a name="case-3a-check-out"></a>Caso 3a: Check-Out

Questa sezione è incentrata sul funzionamento del comando di estrazione.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Estrazione esclusiva (COE) di un progetto client|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre l'intero progetto in modo esclusivo (**File**, **Estrazione**).|Si verifica il check-out.|
|Estrazione esclusiva (COE) di un file system o di un progetto Web IIS locale|1. Impostare Connessione server Web su Condivisione file in **Strumenti**, **Opzioni**, **Progetti**, **Impostazioni Web**.<br />2. Creare un progetto Web.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Estrarre l'intero progetto in modo esclusivo (**File**, **Controllo del codice sorgente**, **Estrazione**).|Si verifica il check-out.|
|Estrarre gli elementi di soluzione in una soluzione (nuovo metodo per la gestione di altri file)Check out solution items in a solution (new method for handling other files)|1. Creare una soluzione vuota.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Controllare la soluzione.<br />4. Aggiungere diversi elementi della soluzione.<br />5. Archiviare tutti gli elementi appena aggiunti.<br />6. Selezionare più elementi della soluzione.<br />7. Estrarre gli elementi selezionati (Menu di scelta rapida, **Estrai**).|I file selezionati vengono estratti.|
|Estrai versione locale (se il plug-in sottoposto a test supporta questa funzionalità)|1. Utente 1: creare un progetto client.<br />2. Utente 1: aggiungere la soluzione al controllo del codice sorgente.<br />3. Utente 2: aprire la soluzione dal controllo del codice sorgente in un'altra posizione.<br />4. Utente 2: Estrarre un file.<br />5. Utente 2: Modificare il file.<br />6. Utente 2: archiviare il file.<br />7. Utente 1: Estrarre la versione locale del file (selezionare l'opzione **Estrai versione locale** avanzata nella finestra di dialogo **Estrai).**|La versione locale del file è estratta.<br /><br /> Le modifiche apportate dall'utente 2 non vengono applicate al file dell'utente 1.|

### <a name="case-3b-disconnected-check-out"></a>Caso 3b: Estrazione disconnessa

Il funzionamento in modalità disconnessa consente agli utenti un certo livello di supporto continuo del controllo del codice sorgente quando non sono collegati direttamente a un archivio versioni. Questa operazione viene eseguita memorizzando nella cache locale tutte le informazioni rilevanti sulla soluzione integrata e progetti.

Le operazioni di estrazione esclusive possono essere eseguite solo quando si è connessi all'archivio del controllo del codice sorgente. Le operazioni di estrazione condivise possono essere eseguite in qualsiasi momento, indipendentemente dal fatto che siano connesse o disconnesse. Pertanto, quando disconnesso dall'archivio versioni, è abilitato solo il comando **Estrai condiviso** (COS). Mentre è disconnesso, **Annulla estrazione** è disabilitato perché non è possibile recuperare la versione precedente per sostituire le modifiche apportate dall'utente.

Quando l'utente si riconnette all'archivio versioni, gli stati di estrazione di tutte le soluzioni e i progetti inclusi vengono sincronizzati. In questo modo gli aggiornamenti necessari per l'archivio per le estrazioni che l'utente ha eseguito. Una volta eseguita la sincronizzazione, l'utente è in grado di continuare a lavorare normalmente (connesso).

#### <a name="expected-behavior"></a>Comportamento previsto

- Impossibile utilizzare il comando **Estrai in modo esclusivo** quando è disconnesso dall'archivio versioni.

- Impossibile utilizzare il comando **Annulla estrazione** mentre è disconnesso dall'archivio versioni.

- **Il** comando Estrazione condivisa funziona.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Mentre sei disconnesso, estrai un file, quindi connettiti per la sincronizzazione|1. Disconnettere un progetto controllato utilizzando la finestra di dialogo Modifica controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Modifica controllo del codice **sorgente**).<br />2. Estrarre un file.<br />3. Fare clic su Estrai (disconnesso) nella finestra di dialogo di avviso.<br />4. Modificare il file.<br />5. Connettersi utilizzando la finestra di dialogo Modifica controllo del codice sorgente.<br />6. Ottenere l'ultima versione del file modificato.|Comportamento previsto comuneCommon Expected Behavior|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3c: Modifica query/Salvataggio query (QEQS)
 Gli elementi inclusi nel controllo del codice sorgente vengono rilevati per modifiche, modifiche e salvataggi per consentire agli utenti di gestire facilmente i propri file. Quando un elemento controllato che viene "archiviato" viene modificato, QEQS intercetta il tentativo di modifica e chiede all'utente se desidera estrarre il file per modificarlo. A seconda degli **strumenti**, **opzioni** impostazioni, l'utente è costretto a estrarre il file per modificare o può essere consentito di modificare una copia in memoria ed estrarre in un secondo momento. Se l'impostazione **Strumenti**dell'utente , **Opzioni** non è impostata per visualizzare la finestra di dialogo di estrazione e solo estrarla, quindi quando l'utente effettua la sua modifica, il file estrae automaticamente, quando possibile.

#### <a name="expected-behavior"></a>Comportamento previsto

- Dopo l'operazione di estrazione, i file e/o le cartelle di destinazione vengono contrassegnati come estratti nell'archivio versioni.

- L'archivio versione attribuisce l'estrazione all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

- La copia locale del file o della cartella di destinazione è scrivibile.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Modificare il file di testo archiviato|1. Creare un nuovo progetto contenente un file di testo.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Impostare **Strumenti**, **Opzioni**, **Controllo del codice sorgente**, Consentire la modifica dei file mentre è di sola lettura su **disco** per deselezionata.<br />4. Impostare **Strumenti**, **Opzioni**, **Controllo del codice sorgente**, Richiedi **estrazione** nella casella combinata Quando i **file archiviati vengono modificati.**<br />5. Impostare **Strumenti**, **Opzioni**, **Controllo del codice sorgente**, Richiedi **estrazione** nella casella combinata Quando i **file archiviati vengono salvati.**<br />6. Aprire il file di testo nell'editor, tentare di digitare nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. Fare clic su **Annulla** nella finestra di dialogo **Estrai per la modifica.** Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />8. Impostare **Strumenti**, **Opzioni**, **Controllo del codice sorgente**, Consentire la modifica dei file mentre è di sola lettura su **disco.**<br />9. Aprire il file di progetto nell'editor, tentare di digitare nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />10. Fare clic su **Modifica** nella finestra di dialogo **Estrai per la modifica.** Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />11. Modificare il file di testo e tentare di salvarlo.|`Result of step 6:`<br /><br /> Viene visualizzata la finestra di dialogo Estrai per modifica.<br /><br /> `Result of step 7:`<br /><br /> Il file è invariato.<br /><br /> `Result of step 9:`<br /><br /> Viene visualizzata la finestra di dialogo Estrai per modifica.<br /><br /> `Result of step 10:`<br /><br /> È possibile modificare il file di progetto in memoria.<br /><br /> `Result of step 11:`<br /><br /> Al salvataggio, viene visualizzata la finestra di dialogo Estrai al salvataggio.|
|Modificare un file di soluzione archiviato|Ripetere i passaggi come descritto nel test precedente, ma invece di modificare un file di testo, modificare la soluzione modificando le proprietà della soluzione.|Uguale al test precedente|
|Modificare un file di progetto archiviato|Ripetere i passaggi come descritto nel test precedente, ma invece di modificare un file di testo, modificare il progetto modificando le proprietà del progetto.|Come il test precedente.|

### <a name="case-3d-silent-check-out"></a>Caso 3d: Estrazione silenziosa
 In questa sottoarea vengono illustrati gli scenari di estrazione in cui la finestra di dialogo **Estrai** non viene visualizzata per **gli**strumenti , **Opzioni**, **le impostazioni del controllo del codice sorgente**.

#### <a name="expected-behavior"></a>Comportamento previsto

- Dopo l'operazione di estrazione, i file e/o le cartelle di destinazione vengono contrassegnati come estratti nell'archivio versioni.

- L'archivio versione attribuisce l'estrazione all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

- La copia locale del file o della cartella di destinazione è scrivibile.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Estrazione invisibile all'utente per un file|1. Impostare **Strumenti**, **Opzioni**, **Controllo del codice sorgente** per estrarre automaticamente i file in **edit**.<br />2. Creare un nuovo progetto con un file.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Estrarre il file.|Il file viene estratto automaticamente (nessuna interfaccia utente).|
|Estrazione invisibile all'utente per un progetto|1. Impostare **Strumenti**, **Opzioni**, **Controllo del codice sorgente** per estrarre automaticamente i file in **edit**.<br />2. Creare un nuovo progetto.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Controllare il progetto.|Il file viene estratto automaticamente (nessuna interfaccia utente).|

### <a name="case-3e-undo-check-out"></a>Caso 3e: Annulla estrazione
 **Annulla estrazione** viene utilizzato per annullare lo stato estratto di un file ed evitare di archiviare le modifiche apportate al file.

#### <a name="expected-behavior"></a>Comportamento previsto

- L'impostazione predefinita si basa sull'impostazione **Estrai versione locale** dell'utente. Se l'utente ha scelto di estrarre la versione locale, l'impostazione predefinita per l'annullamento dell'estrazione consiste nel ripristinare sempre la versione estratta.

- Dopo l'accettazione dell'annullamento, le icone in **Esplora soluzioni** vengono aggiornate per i file interessati e l'elemento viene rimosso dalla finestra **Archiviazioni in sospeso.**

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Annullare l'estrazione di un singolo file estratto in modo esclusivo|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre un file in modo esclusivo.<br />4. Modificare il file.<br />5. Annullare l'estrazione (**File**, **Controllo del codice sorgente**, Annulla **estrazione**).|Comportamento previsto comune.|
|Annullare l'estrazione di un singolo file estratto condiviso|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre un file condiviso.<br />4. Modificare il file.<br />5. Annullare l'estrazione (**File**, **Controllo del codice sorgente**, Annulla **estrazione**).|Comportamento previsto comune.|
|Annullare l'estrazione di un progetto dopo l'aggiunta di file al progetto|1. Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2. Controllare il progetto.<br />3. Aggiungere un file al progetto.<br />4. Annullare l'estrazione del progetto.|Il file aggiunto viene rimosso dal progetto in Esplora soluzioni.<br /><br /> Il progetto non è più estratto.|
|Annullare l'estrazione di un progetto dopo l'eliminazione di file dal progetto|1. Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2. Controllare il progetto.<br />3. Eliminare un file dal progetto.<br />4. Annullare l'estrazione del progetto.|Il file eliminato viene visualizzato sotto il progetto in Esplora soluzioni.<br /><br /> Il progetto non è più estratto.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
