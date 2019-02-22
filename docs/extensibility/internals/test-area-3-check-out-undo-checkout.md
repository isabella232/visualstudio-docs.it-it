---
title: "Area di test 3: Estrarre o annullare l'estrazione | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, checkout
- source control plug-ins, undo checkout
- source control [Visual Studio SDK], checking out
- source control [Visual Studio SDK], undo checkout
ms.assetid: ce00c5a5-d472-4f45-8776-d77a1fbe9d37
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 772e238367f16d95fa47d661f8a4bd24091524d1
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/21/2019
ms.locfileid: "56605653"
---
# <a name="test-area-3-check-outundo-checkout"></a>Area di test 3: Check-Out / Annulla estrazione
Quest'area del plug-in test di controllo del codice sorgente illustra gli elementi di modifica e di ripristino dall'archivio delle versioni tramite il **Estrai** e **Annulla estrazione** comandi.

**Scopri**: Contrassegni estratto un elemento nell'archivio delle versioni come, modifica la copia locale su lettura/scrittura.

**Annulla estrazione**: Segni di un elemento nell'archivio delle versioni come Check-in, viene ripristinato la copia locale allo stato di check-out (a seconda delle opzioni).

## <a name="command-menu-access"></a>Accesso a comandi di Menu

Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nei test case vengono usati percorsi di menu ambiente di sviluppo integrato.

##### <a name="check-out"></a>Vedere:

-   **File**, **controllo del codice sorgente**, **Scopri**.

-   **File**, **consultare**.

-   Menu di scelta rapida **Estrai**.

-   Annulla estrazione: **File**, **controllo del codice sorgente**, **Annulla estrazione**.

## <a name="common-expected-behavior"></a>Comportamento previsto comune

-   Dopo l'operazione di estrazione, il file di destinazione e/o le cartelle sono contrassegnate come estratti nell'archivio delle versioni.

-   L'archivio delle versioni l'estrazione di attributi per l'utente corretto.

-   La data dell'estrazione e l'ora siano corretti (per le impostazioni dell'utente).

## <a name="test-cases"></a>Test case

Di seguito sono specifici test case per l'area di test di estrazione/annullamento dell'estrazione.

### <a name="case-3a-check-out"></a>Case 3a: Estrai

Questa sezione è incentrata sull'operazione del comando estrazione.

|Operazione|Passi del test|Per verificare i risultati previsti|
|------------|----------------|--------------------------------|
|Controllare Out esclusivo (COE) un progetto client|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrae l'intero progetto in modo esclusivo (**File**, **Estrai**).|Si verifica l'estrazione.|
|Estrazione esclusiva (COE) un File System o un progetto Web IIS locale|1.  Impostazione connessione di Server Web di condivisione nel File **degli strumenti**, **opzioni**, **progetti**, **impostazioni Web**.<br />2.  Creare un progetto Web.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrae l'intero progetto in modo esclusivo (**File**, **controllo del codice sorgente**, **Check Out**).|Si verifica l'estrazione.|
|Estrae gli elementi della soluzione in una soluzione (nuovo metodo per la gestione di altri file)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre la soluzione.<br />4.  Aggiungere alcuni elementi di soluzione.<br />5.  Archiviare tutti gli elementi appena aggiunti.<br />6.  Selezionare più elementi di soluzione.<br />7.  Estrae gli elementi selezionati (Menu di scelta rapida **Estrai**).|I file selezionati sono stati estratti.|
|Estrai versione locale (se questa funzionalità supporta i plug-in sottoposta a test)|1.  1 utente: Creare un progetto client.<br />2.  1 utente: Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Utente 2: Aprire la soluzione dal controllo del codice sorgente in un altro percorso.<br />4.  Utente 2: Estrarre un file.<br />5.  Utente 2: Modificare il file.<br />6.  Utente 2: Archiviare il file.<br />7.  1 utente: Estrai versione locale del file (verificare i **Estrai versione locale** nell'opzione avanzata **Check Out** nella finestra di dialogo).|Versione locale del file è estratto.<br /><br /> Le modifiche apportate dall'utente 2 non vengono applicate ai file di 1 utente.|

### <a name="case-3b-disconnected-check-out"></a>Case 3b: Estrazione disconnesso

Funziona in modalità disconnessa consente agli utenti un certo livello di supporto per il controllo origine continua se non è collegato direttamente a un archivio delle versioni. Ciò avviene memorizzando localmente nella cache tutte le informazioni rilevanti sui progetti e soluzioni integrate.

Operazioni di estrazione esclusiva può verificarsi solo durante la connessione all'archivio di controllo di origine. Operazioni di estrazione condivisa può verificarsi in qualsiasi momento, se connesso o disconnesso. Pertanto, quando si è disconnessi dall'archivio versioni, solo il **controllare e condiviso** (CO) command è abilitato. Durante la disconnessione, **Annulla estrazione** è disabilitata perché la versione precedente non può essere recuperata per sostituire le modifiche apportate dall'utente.

Quando l'utente si riconnette alla versione archiviare, gli stati di estrazione di tutte le soluzioni integrate e progetti sono stati sincronizzati. Le estrazioni in modo che l'utente ha eseguito questa operazione gli aggiornamenti necessari all'archivio. Dopo la sincronizzazione è stato eseguito, l'utente è in grado di continuare a lavorare come di consueto (connesso).

#### <a name="expected-behavior"></a>Comportamento previsto

-   Non è possibile usare **Out esclusivamente** comando durante la disconnessione dall'archivio versioni.

-   Non è possibile usare **Annulla estrazione** comando durante la disconnessione dall'archivio versioni.

-   **Condiviso Check Out** comando funziona.

|Operazione|Passi del test|Per verificare i risultati previsti|
|------------|----------------|--------------------------------|
|Durante la disconnessione, estrarre un file e quindi connettersi per la sincronizzazione|1.  Disconnettere un progetto controllato presente nella finestra di dialogo Modifica controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Modifica controllo del codice sorgente**).<br />2.  Estrarre un file.<br />3.  Fare clic su Estrai (disconnesso) nella finestra di dialogo di avviso.<br />4.  Modificare il file.<br />5.  Connettersi tramite la finestra di dialogo Modifica controllo del codice sorgente.<br />6.  Ottenere la versione più recente del file modificato.|Comportamento previsto comune|

### <a name="case-3c-query-editquery-save-qeqs"></a>Caso 3C: Query Edit/Query Save (QEQS)
 Gli elementi nel controllo del codice sorgente vengono tenuta traccia per le modifiche, le modifiche, e consente di risparmiare per consentire agli utenti con facilità gestiscono i file. Quando viene modificato un elemento controllato che è "archiviato", QEQS intercetta la modifica effettuata è fallita e chiede all'utente se desidera estrarre il file per modificarlo. A seconda **degli strumenti**, **opzioni** impostazioni, l'utente è costretto a controllare estrarre il file per modificare o possono essere autorizzati a modificare una copia in memoria ed estrarre in un secondo momento. Se l'utente **degli strumenti**, **opzioni** impostazione non è impostata per visualizzare la finestra di dialogo di estrazione e di appena estrarlo, quindi come l'utente apporta la modifica, il file estrae automaticamente, laddove possibile.

#### <a name="expected-behavior"></a>Comportamento previsto

-   Dopo l'operazione di estrazione, il file di destinazione e/o le cartelle sono contrassegnate come estratti nell'archivio delle versioni.

-   L'archivio delle versioni di attributi di check-out per l'utente corretto.

-   La data e ora del check-out sono corretti (per le impostazioni dell'utente).

-   La copia locale della cartella o file di destinazione è scrivibile.

|Operazione|Passi del test|Per verificare i risultati previsti|
|------------|----------------|--------------------------------|
|Modificare i file di testo che viene verificato|1.  Creare un nuovo progetto che contiene un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Impostare **degli strumenti**, **opzioni**, **controllo del codice sorgente**, **consentono la modifica di sola lettura su disco dei file** a deselezionata.<br />4.  Impostare **Tools**, **opzioni**, **controllo del codice sorgente**, **Richiedi estrazione** nel **quando archiviato file sonomodificato** casella combinata.<br />5.  Impostare **degli strumenti**, **opzioni**, **controllo del codice sorgente**, **Richiedi estrazione** nel **quando archiviare i file vengono salvati** casella combinata.<br />6.  Aprire il file di testo nell'editor, provare a digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7.  Fare clic su **annullare** nel **Estrai per la modifica** nella finestra di dialogo. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />8.  Impostare **degli strumenti**, **opzioni**, **controllo del codice sorgente**, **consentono la modifica di sola lettura su disco dei file** a selezionato.<br />9. Aprire il file di progetto nell'editor, provare a digitare il nuovo testo nel file. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />10. Fare clic su **Edit** nel **Estrai per la modifica** nella finestra di dialogo. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />11. Modificare il file di testo e si tenterà di salvarlo.|`Result of step 6:`<br /><br /> Controllare se viene visualizzata la finestra di dialogo di modifica.<br /><br /> `Result of step 7:`<br /><br /> Il file rimane invariato.<br /><br /> `Result of step 9:`<br /><br /> Controllare se viene visualizzata la finestra di dialogo di modifica.<br /><br /> `Result of step 10:`<br /><br /> È possibile modificare il file di progetto in memoria.<br /><br /> `Result of step 11:`<br /><br /> Salva il Check-out nel salvataggio nella finestra di dialogo viene visualizzato.|
|Modificare un file di soluzione che viene archiviato|Ripetere i passaggi come descritto nella precedente di test, ma anziché modificare un file di testo, modificare soluzione modificando le proprietà della soluzione.|Uguale a test precedente|
|Modificare un file di progetto che viene verificato|Ripetere i passaggi come descritto nella precedente di test, ma anziché modificare un file di testo, modificare progetto modificando le proprietà del progetto.|Uguale a test precedente.|

### <a name="case-3d-silent-check-out"></a>Caso 3d: Estrazione automatica
 Questo controllo include sottoarea gli scenari in cui il **Check-Out** finestra di dialogo non vengono visualizzati per ogni utente **Tools**, **opzioni**, **le impostazioni di controllo del codice sorgente** .

#### <a name="expected-behavior"></a>Comportamento previsto

-   Dopo l'operazione di estrazione, il file di destinazione e/o le cartelle sono contrassegnate come estratti nell'archivio delle versioni.

-   L'archivio delle versioni di attributi di check-out per l'utente corretto.

-   La data e ora del check-out è corretto (per le impostazioni dell'utente).

-   La copia locale della cartella o file di destinazione è scrivibile.

|Operazione|Passi del test|Per verificare i risultati previsti|
|------------|----------------|--------------------------------|
|Estrazione invisibile all'utente per un file|1.  Impostare **Tools**, **opzioni**, **controllo del codice sorgente** al **Esegui checkout dei file automaticamente dal menu Modifica**.<br />2.  Creare un nuovo progetto con un file.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrarre il file.|File estratto automaticamente (senza interfaccia utente).|
|Estrazione invisibile all'utente per un progetto|1.  Impostare **Tools**, **opzioni**, **controllo del codice sorgente** al **Esegui checkout dei file automaticamente dal menu Modifica**.<br />2.  Creare un nuovo progetto.<br />3.  Aggiungere la soluzione al controllo del codice sorgente.<br />4.  Estrarre il progetto.|File estratto automaticamente (senza interfaccia utente).|

### <a name="case-3e-undo-check-out"></a>Case 3e: Annulla estrazione
 **Annulla estrazione** viene usato per annullare un file estratto lo stato e di evitare di archiviare le modifiche apportate al file.

#### <a name="expected-behavior"></a>Comportamento previsto

-   Il valore predefinito si basa il suo **Estrai versione locale** impostazione. Se l'utente ha scelto di estrarre la versione locale, il valore predefinito per l'operazione di annullamento estrazione consiste nel ripristinare in qualsiasi momento la versione estratta.

-   Dopo l'accettazione dell'operazione di annullamento, le icone nel **Esplora soluzioni** vengono aggiornati per interessati i file e l'elemento viene rimosso dal **archiviazioni in sospeso** finestra.

|Operazione|Passi del test|Per verificare i risultati previsti|
|------------|----------------|--------------------------------|
|Annullare l'estrazione di un singolo file che è stato estratto in modo esclusivo|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrae un file in modo esclusivo.<br />4.  Modificare il file.<br />5.  Annullare l'estrazione di (**File**, **controllo del codice sorgente**, **Annulla estrazione**).|Comportamento previsto comune.|
|Annullare l'estrazione di un singolo file che è stato estratto condiviso|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre un file condiviso.<br />4.  Modificare il file.<br />5.  Annullare l'estrazione di (**File**, **controllo del codice sorgente**, **Annulla estrazione**).|Comportamento previsto comune.|
|Annullare l'estrazione di un progetto dopo l'aggiunta di più file al progetto|1.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2.  Estrarre il progetto.<br />3.  Aggiungere un file al progetto.<br />4.  Annullare l'estrazione del progetto.|File aggiunto viene rimosso dal progetto in Esplora soluzioni.<br /><br /> Progetto non è stato estratto.|
|Annullare l'estrazione di un progetto dopo l'eliminazione di file dal progetto|1.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />2.  Estrarre il progetto.<br />3.  Eliminare un file dal progetto.<br />4.  Annullare l'estrazione del progetto.|File eliminato viene visualizzato sotto il progetto in Esplora soluzioni.<br /><br /> Progetto non è stato estratto.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
