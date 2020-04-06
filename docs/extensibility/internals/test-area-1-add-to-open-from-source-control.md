---
title: "Area di test 1: Aggiungere da un controllo del codice sorgente per l'apertura dal controllo del codice sorgente Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6ac7b8e5a60fe25ac22272cc28fc3ed6f903b058
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704674"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Area di test 1: Aggiungi a/Apri dal controllo del codice sorgente
Questa area di test del plug-in del controllo del codice sorgente riguarda l'inserimento di soluzioni o progetti nel controllo del codice sorgente e il loro recupero dal controllo del codice sorgente.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case vengono utilizzati i percorsi dei menu dell'ambiente di sviluppo integrato seguenti:The following integrated development environment menu paths are used in the test cases:

- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], open dal controllo del codice sorgente: **File**, **Open**,**Soluzione** **progetto**/; guardare nella [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] posizione.

- Per altri plug-in del controllo del codice sorgente, aprire dal controllo del codice sorgente: **File**, **Controllo del codice sorgente**, Apri dal controllo del codice **sorgente**.

- Aggiungi al controllo del codice sorgente: **File**, **Controllo del codice sorgente**, Aggiungi soluzione al file del controllo del codice **sorgente**, Controllo del **codice sorgente**, Aggiungi progetti selezionati al controllo del **codice sorgente**.

- Menu di scelta rapida (Progetto/Soluzione), **Aggiungi soluzione al controllo del codice sorgente**.

- Aggiungi dal controllo del codice sorgente: **File**, **Controllo del codice sorgente**, Aggiungi progetto dal controllo del codice **sorgente**.

- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], l'opzione Aggiungi dal controllo del codice sorgente è disponibile anche in **File**, **Aggiungi**, **Progetto esistente**; guardare nella [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] posizione.

  > [!NOTE]
  > In questo test è possibile utilizzare un percorso di un file locale o di un IIS locale (server Web).

## <a name="expected-behavior"></a>Comportamento previsto

- Per ogni tipo di progetto supportato, un utente deve essere in grado di "Aggiungere a" e "Apri da" controllo del codice sorgente.

- Quando un progetto viene aggiunto al \<controllo del codice sorgente, viene creato un file *ProjectName*>.vspscc corrispondente (file dei suggerimenti del progetto). Contiene l'elenco dei file di esclusione e le informazioni di connessione. Non eliminare questo file perché contiene informazioni specifiche per il progetto.

- Quando una soluzione viene aggiunta al \<controllo del codice sorgente, viene creato un file *SolutionName*>.vssscc (tripla S) corrispondente. Il file di testo contiene informazioni di connessione e un elenco di file di esclusione, simile al file dei suggerimenti del progetto. Questo file è temporaneo ed esiste solo nel database del controllo del codice sorgente.

- Quando una soluzione viene aperta \<dal controllo del codice sorgente, un file *SolutionName*>.vsscc (doppio S) che esiste solo nel database del controllo del codice sorgente, viene creato localmente in un file temporaneo. Questo file contiene il percorso dalla cartella di connessione della soluzione al file della soluzione. Questo file è temporaneo e la copia locale viene eliminata al termine dell'operazione "Apri dal controllo del codice sorgente".

- Dopo aver aggiunto un progetto al controllo del codice sorgente, è possibile eseguire qualsiasi azione del controllo del codice sorgente su di esso (Estrai, Ottieni e così via).

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test Aggiungi a/Apri dal controllo del codice sorgente.

### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: aggiungere una soluzione al controllo del codice sorgenteCase 1a: Add Solution to Source Control
 Questo test case è incentrato sull'aggiunta di soluzioni al controllo del codice sorgente.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere una soluzione contenente un progetto client al controllo del codice sorgenteAdd solution containing a client project to source control|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Aggiungi soluzione al controllo del codice **sorgente**).|Soluzione/Progetto è stato aggiunto al controllo del codice sorgente.|
|Aggiungere una soluzione contenente un file system o un progetto Web IIS locale al controllo del codice sorgenteAdd solution containing a File System or local IIS Web project to source control|1. Creare un file system o un progetto Web IIS locale (utilizzare il pulsante Sfoglia per puntare al percorso del progetto; il percorso determina il tipo di progetto Web creato).<br />2. Aggiungere la soluzione al controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Aggiungi soluzione al controllo del codice **sorgente**).|Soluzione/Progetto è stato aggiunto al controllo del codice sorgente.|
|Aggiungere una soluzione contenente un progetto Web di sito remoto al controllo del codice sorgenteAdd solution containing a Remote Site Web project to source control|1. Creare un progetto Web di sito remoto.<br />2. Aggiungere la soluzione al controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Aggiungi soluzione al controllo del codice **sorgente**).<br />3. Fare clic **su OK** nella finestra di dialogo Avviso di accesso a FrontPage.|La soluzione è stata aggiunta al controllo del codice sorgente.<br /><br /> Il progetto di sito remoto NON è nel controllo del codice sorgente. I progetti di sito remoto devono essere controllati dal proprio server IIS.|
|Aggiungere una singola soluzione di progetto al controllo del codice sorgente utilizzando **Aggiungi progetti selezionati al controllo del codice sorgente**.|1. Creare una singola soluzione di progetto.<br />2. Aggiungere solo la soluzione al controllo del codice sorgente come selezione (**File**, **Controllo del codice sorgente**, Aggiunta di progetti selezionati al controllo del codice **sorgente**). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Aggiungere progetto al controllo del codice sorgente come selezione (**File**, **Controllo del codice sorgente**, Aggiunta di progetti selezionati al controllo del codice **sorgente**).<br />4. Fare clic su **Sì** per aggiungere il progetto nella stessa posizione.<br />5. Fare clic su **Estrai** nella finestra di dialogo **Estrai per la modifica.**|`Result from Step 2:`<br /><br /> Il progetto e tutti i file all'interno del progetto hanno un indicatore di controllo del codice sorgente estratto e una descrizione comando visualizza "Non nel controllo del codice sorgente".<br /><br /> `Result from Step 5:`<br /><br /> Il file di progetto e di soluzione si trovano nella stessa cartella nel controllo del codice sorgente.|
|Annullare l'aggiunta di una soluzione al controllo del codice sorgenteCancel adding a solution to source control|1. Creare una singola soluzione di progetto.<br />2. Tentare di aggiungere progetto e soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Annullare dopo essere nel sistema di controllo del codice sorgente.|`Result from Step 2:`<br /><br /> La finestra di dialogo Imposta controllo del codice sorgente del progetto viene visualizzata una sola volta.<br /><br /> `Result from Step 3:`<br /><br /> Aggiunta progetto annullato, progetto/soluzione NON è sotto controllo del codice sorgente e tutti i menu Aggiungi al controllo del codice sorgente ancora disponibili.|

### <a name="case-1b-open-solution-from-source-control"></a>Caso 1b. Apri soluzione dal controllo del codice sorgenteOpen Solution from Source Control
 Questo test case si concentra sull'apertura di soluzioni dal controllo del codice sorgente.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aprire una soluzione contenente un progetto client dal controllo del codice sorgenteOpen a solution containing a client project from source control|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|Soluzione/Progetto aperto dal controllo del codice sorgente.|
|Aprire una soluzione contenente un progetto Web IIS o locale dal controllo del codice sorgente|1. Creare un progetto Web IIS o locale.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|Soluzione/Progetto aperto dal controllo del codice sorgente.|
|Aprire una soluzione contenente un progetto Web di sito remoto dal controllo del codice sorgenteOpen a solution containing a Remote Site Web project from source control|1. Creare un progetto Web di sito remoto.<br />2. Aggiungere la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|`Result from Step 2:`<br /><br /> Web del sito remoto NON è sotto il controllo del codice sorgente.<br /><br /> `Result from Step 4:`<br /><br /> Soluzione aperta dal controllo del codice sorgente.<br /><br /> Il progetto di sito remoto viene caricato, ma NON è nel controllo del codice sorgente.|

### <a name="case-1c-add-solution-from-source-control"></a>Caso 1c: aggiungere una soluzione dal controllo del codice sorgenteCase 1c: Add Solution from Source Control
 Questo test case è incentrato sull'aggiunta di soluzioni dal controllo del codice sorgente.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungi alla soluzione vuota: una singola soluzione di progettoAdd to Empty solution - a single project solution|1. Creare una singola soluzione di progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare una seconda soluzione vuota.<br />5. Aggiungere la soluzione controllata in precedenza dal controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Aggiungi progetto dal controllo del codice **sorgente**).|Il progetto aggiunto viene visualizzato in **Esplora soluzioni** ed è archiviato.|
|Aggiungi alla soluzione con un singolo progetto: singolo progetto|1. Creare una soluzione con un singolo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare una seconda soluzione vuota.<br />5. Aggiungere la soluzione controllata in precedenza dal controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Aggiungi progetto dal controllo del codice **sorgente**).|Il progetto aggiunto viene visualizzato in **Esplora soluzioni** ed è archiviato.|
|Aggiungi alla soluzione: soluzione aggiunta al controllo del codice sorgente tramite selezione|1. Creare una soluzione con un progetto.<br />2. Aggiungere solo la soluzione al controllo del codice sorgente come selezione. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Chiudere la soluzione.<br />4. Creare una nuova soluzione.<br />5. Aggiungere la soluzione controllata in precedenza dal controllo del codice sorgente (**File**, **Controllo del codice sorgente**, Aggiungi progetto dal controllo del codice **sorgente**).|`Result from Step 2:`<br /><br /> Il progetto non è nel controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> Se la prima soluzione dispone di elementi di soluzione, non è possibile aggiungerli dal controllo del codice sorgente, pertanto non vengono visualizzati.<br /><br /> Il progetto della prima soluzione viene visualizzato come non disponibile.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
