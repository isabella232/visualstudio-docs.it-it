---
title: 'Area di test 3: controllare Out-Undo checkout | Microsoft Docs'
description: Questa area di test del plug-in di controllo del codice sorgente illustra la modifica e il ripristino degli elementi dall'archivio versioni usando i comandi Estrai e Annulla estrazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 96c5940a97fc799393d7830fa5589183afe33fb0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158788"
---
# <a name="test-area-3-check-outundo-checkout"></a>Area di test 3: estrarre o annullare l'estrazione
Questa area di test del plug-in di controllo del codice sorgente illustra la modifica e il ripristino degli elementi dall'archivio versioni tramite **i comandi Estrai** **e** Annulla estrazione.

**Check Out**: contrassegna un elemento nell'archivio versioni come estratto e modifica la copia locale in lettura/scrittura.

**Annulla estrazione:** contrassegna un elemento nell'archivio versioni come archiviato, ripristina lo stato della copia locale prima dell'estrazione (a seconda delle opzioni).

## <a name="command-menu-access"></a>Accesso al menu di comando

Nei test case vengono usati i percorsi di menu dell'ambiente di sviluppo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato seguenti.

##### <a name="check-out"></a>Estrai:

- **File**, **Controllo del codice sorgente**, **Estrai**.

- **File**, **Estrai**.

- Menu di scelta **rapida, Check-Out**.

- Annulla estrazione: **File**, **Controllo del codice sorgente**, **Annulla estrazione**.

## <a name="common-expected-behavior"></a>Comportamento previsto comune

- Dopo l'operazione di estrazione, i file e/o le cartelle di destinazione vengono contrassegnati come estratti nell'archivio versioni.

- L'archivio delle versioni attribta l'estrazione all'utente corretto.

- L'ora e la data del pagamento sono corrette (in base alle impostazioni dell'utente).

## <a name="test-cases"></a>Test case

Di seguito sono riportati test case specifici per l'area di test Checkout/Undo Checkout.

### <a name="case-3a-check-out"></a>Caso 3a: Check Out

Questa sezione è incentrata sul funzionamento del comando check-out.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Estrarre un progetto client esclusivo (COE)|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre l'intero progetto in modo esclusivo (**File**, **Check Out**).|Si verifica il check-out.|
|Estrarre un file system o un progetto Web IIS locale|1. Impostare Connessione server Web su Condivisione file in **Strumenti**, **Opzioni**, **Progetti**, Web **Impostazioni**.<br />2. Creare un progetto Web.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Estrarre l'intero progetto in modo esclusivo (**File**, **Controllo del codice sorgente**, **Check Out**).|Si verifica il check-out.|
|Estrarre gli elementi della soluzione in una soluzione (nuovo metodo per la gestione di altri file)|1. Creare una soluzione vuota.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Controllare la soluzione.<br />4. Aggiungere diversi elementi della soluzione.<br />5. Archiviare tutti gli elementi appena aggiunti.<br />6. Selezionare più elementi della soluzione.<br />7. Controllare gli elementi selezionati (menu di scelta rapida, **Check-Out).**|I file selezionati vengono estratti.|
|Check Out Local Version (se il plug-in sotto test supporta questa funzionalità)|1. Utente 1: creare un progetto client.<br />2. Utente 1: aggiungere la soluzione al controllo del codice sorgente.<br />3. Utente 2: aprire la soluzione dal controllo del codice sorgente a un'altra posizione.<br />4. Utente 2: Estrarre un file.<br />5. Utente 2: modificare il file.<br />6. Utente 2: archiviare il file.<br />7. Utente 1: Estrarre la versione locale del file (selezionare l'opzione Estrai versione locale **avanzata** nella finestra **di dialogo** Estrai).|La versione locale del file è stata es check-out.<br /><br /> Le modifiche apportate dall'utente 2 non vengono applicate al file dell'utente 1.|

### <a name="case-3b-disconnected-check-out"></a>Caso 3b: Disconnessione dell'estrazione

Il funzionamento in modalità disconnessa consente agli utenti un certo livello di supporto continuo del controllo del codice sorgente quando non sono collegati direttamente a un archivio versioni. Questa operazione viene eseguita memorizzando nella cache locale tutte le informazioni pertinenti sulla soluzione e sui progetti elencati.

Le operazioni di estrazione esclusive possono verificarsi solo durante la connessione all'archivio del controllo del codice sorgente. Le operazioni di estrazione condivise possono verificarsi in qualsiasi momento, indipendentemente dal fatto che siano connesse o disconnesse. Pertanto, quando si è disconnessi dall'archivio versioni, è abilitato solo il comando Check **Out Shared** (COS). In caso di disconnessione, **l'opzione Annulla** estrazione è disabilitata perché non è possibile recuperare la versione precedente per sostituire le modifiche apportate dall'utente.

Quando l'utente si riconnette all'archivio versioni, gli stati di estrazione di tutte le soluzioni e i progetti elencati vengono sincronizzati. In questo modo vengono eseguiti gli aggiornamenti necessari all'archivio per le estrazioni eseguite dall'utente. Al termine della sincronizzazione, l'utente può continuare a lavorare normalmente (connesso).

#### <a name="expected-behavior"></a>Comportamento previsto

- Impossibile usare **il comando Estrai in** modo esclusivo mentre è disconnesso dall'archivio versioni.

- Impossibile usare **il comando Annulla estrazione** mentre è disconnesso dall'archivio versioni.

- **Il comando Estrazione** condivisa funziona.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Durante la disconnessione, estrarre un file e quindi connettersi per la sincronizzazione|1. Disconnettere un progetto controllato usando la finestra di dialogo Modifica controllo del codice sorgente (**File**, **Controllo del codice** sorgente , Modifica controllo del codice **sorgente**).<br />2. Estrarre un file.<br />3. Fare clic su Estrai (disconnesso) nella finestra di dialogo di avviso.<br />4. Modificare il file.<br />5. Connessione la finestra di dialogo Modifica controllo del codice sorgente .<br />6. Ottenere la versione più recente del file modificato.|Comportamento previsto comune|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3c: Query Edit/Query Save (QEQS)
 Gli elementi nel controllo del codice sorgente vengono registrati per le modifiche, le modifiche e i salvamenti per consentire agli utenti di gestire facilmente i file. Quando viene modificato un elemento controllato archiviato, QEQS intercetta la modifica tentata e chiede all'utente se vuole estrarre il file per modificarlo. A seconda **delle impostazioni** di Strumenti **,** Opzioni, l'utente è obbligato a estrarre il file per modificarlo o può essere autorizzato a modificare una copia in memoria e a estrarlo in un secondo momento. Se l'impostazione Strumenti  **,** Opzioni dell'utente non è impostata per visualizzare la finestra di dialogo di estrazione e per estrarla, quando l'utente apporta la modifica, il file viene estratto automaticamente, quando possibile.

#### <a name="expected-behavior"></a>Comportamento previsto

- Dopo l'operazione di estrazione, i file e/o le cartelle di destinazione vengono contrassegnati come estratti nell'archivio versioni.

- L'archivio versioni attribta l'estrazione all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

- La copia locale del file o della cartella di destinazione è scrivibile.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Modificare il file di testo archiviato|1. Creare un nuovo progetto contenente un file di testo.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Impostare **Strumenti**, **Opzioni**, **Controllo del** codice sorgente , Consenti la modifica dei file in sola lettura su **disco** per deselezionarla.<br />4. Impostare **Strumenti**, **Opzioni**, **Controllo del** codice **sorgente** , Richiedi estrazione nella casella combinata quando i file archiviati **vengono modificati.**<br />5. Impostare **Strumenti**, **Opzioni**, **Controllo del** codice **sorgente** , Richiedi estrazione nella casella combinata quando i file archiviati **vengono** salvati.<br />6. Aprire il file di testo nell'editor, provare a digitare nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. Fare **clic su Annulla** nella finestra di dialogo **Estrai** per modifica . Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />8. Impostare **Strumenti**, **Opzioni**, **Controllo del** codice sorgente , Consenti la modifica dei file in sola lettura **su disco** da controllare.<br />9. Aprire il file di progetto nell'editor, provare a digitare nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />10. Fare **clic su Modifica** nella finestra di dialogo **Estrai** per modifica . Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />11. Modificare il file di testo e provare a salvarlo.|`Result of step 6:`<br /><br /> Verrà visualizzata la finestra di dialogo Modifica .<br /><br /> `Result of step 7:`<br /><br /> Il file rimane invariato.<br /><br /> `Result of step 9:`<br /><br /> Verrà visualizzata la finestra di dialogo Modifica .<br /><br /> `Result of step 10:`<br /><br /> È possibile modificare il file di progetto in memoria.<br /><br /> `Result of step 11:`<br /><br /> Al salvataggio viene visualizzata la finestra di dialogo Estrai al salvataggio.|
|Modificare un file di soluzione archiviato|Ripetere i passaggi come descritto nel test precedente, ma invece di modificare un file di testo, modificare la soluzione modificando le proprietà della soluzione.|Uguale al test precedente|
|Modificare un file di progetto archiviato|Ripetere i passaggi come descritto nel test precedente, ma invece di modificare un file di testo, modificare il progetto modificando le proprietà del progetto.|Uguale al test precedente.|

### <a name="case-3d-silent-check-out"></a>Caso 3d: estrazione invisibile all'utente
 Questa sottoarea illustra gli  scenari di estrazione in cui la finestra di dialogo Estrai non viene visualizzata per ogni utente Strumenti **,** **Opzioni**, Impostazioni controllo del **codice sorgente**.

#### <a name="expected-behavior"></a>Comportamento previsto

- Dopo l'operazione di estrazione, i file e/o le cartelle di destinazione vengono contrassegnati come estratti nell'archivio versioni.

- L'archivio versioni attribta l'estrazione all'utente corretto.

- L'ora e la data dell'estrazione sono corrette (in base alle impostazioni dell'utente).

- La copia locale del file o della cartella di destinazione è scrivibile.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Estrazione invisibile all'utente per un file|1. Impostare **Strumenti**, **Opzioni**, Controllo **del codice sorgente** per estrarre **automaticamente i file al momento della modifica.**<br />2. Creare un nuovo progetto con un file.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Estrarre il file.|Il file viene estratto automaticamente (nessuna interfaccia utente).|
|Estrazione invisibile all'utente per un progetto|1. Impostare **Strumenti**, **Opzioni**, Controllo **del codice sorgente** per estrarre **automaticamente i file al momento della modifica.**<br />2. Creare un nuovo progetto.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Estrarre il progetto.|Il file viene estratto automaticamente (nessuna interfaccia utente).|

### <a name="case-3e-undo-check-out"></a>Caso 3e: Annullare l'estrazione
 **Annulla estrazione** consente di annullare lo stato di estrazione di un file ed evitare di archiviare le modifiche apportate al file.

#### <a name="expected-behavior"></a>Comportamento previsto

- L'impostazione predefinita è basata sull'impostazione **Estrai versione locale** dell'utente. Se l'utente ha scelto di estrarre la versione locale, l'impostazione predefinita per l'annullamento dell'estrazione è ripristinare sempre la versione es check-out.

- Dopo l'accettazione dell'annullamento, le icone Esplora soluzioni vengono aggiornate per i file interessati e l'elemento viene rimosso dalla finestra **Archiviazioni in** sospeso. 

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Annullare l'estrazione di un singolo file estratto in modo esclusivo|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre un file in modo esclusivo.<br />4. Modificare il file.<br />5. Annullare **l'estrazione**( File , **Controllo del codice sorgente**, **Annulla estrazione**).|Comportamento previsto comune.|
|Annullare l'estrazione di un singolo file estratto Condiviso|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre un file condiviso.<br />4. Modificare il file.<br />5. Annullare **l'estrazione**( File , **Controllo del codice sorgente**, **Annulla estrazione**).|Comportamento previsto comune.|
|Annullare l'estrazione di un progetto dopo l'aggiunta di file al progetto|1. Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2. Estrarre il progetto.<br />3. Aggiungere un file al progetto.<br />4. Annullare l'estrazione del progetto.|Il file aggiunto viene rimosso dal progetto in Esplora soluzioni.<br /><br /> Project non è più estratto.|
|Annullare l'estrazione di un progetto dopo l'eliminazione di file dal progetto|1. Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2. Estrarre il progetto.<br />3. Eliminare un file dal progetto.<br />4. Annullare l'estrazione del progetto.|Il file eliminato viene visualizzato nel progetto in Esplora soluzioni.<br /><br /> Project non è più estratto.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
