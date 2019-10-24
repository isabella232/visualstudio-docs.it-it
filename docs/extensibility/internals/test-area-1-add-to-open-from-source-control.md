---
title: "Area di test 1: aggiungere all'apertura dal controllo del codice sorgente | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ea7cd49ee371ce78e71a311ed0184b8f7259365
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722711"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Area di test 1: aggiunta/apertura dal controllo del codice sorgente
Questa area di test del plug-in del controllo del codice sorgente copre la disposizione di soluzioni o progetti nel controllo del codice sorgente e il recupero dal controllo del codice sorgente.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei test case vengono utilizzati i percorsi dei menu Integrated Development Environment seguenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]:

- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], aprire dal controllo del codice sorgente: **file**, **apri**, **progetto** /**soluzione**; controllare la posizione del [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].

- Per altri plug-in del controllo del codice sorgente, aprire dal controllo del codice sorgente: **file**, **controllo del codice sorgente**, **aprire dal controllo del codice sorgente**.

- Aggiungi al controllo del codice sorgente: **file**, **controllo del codice sorgente**, **Aggiungi soluzione al file del controllo del codice**sorgente, controllo del **codice sorgente**, **Aggiungi progetti selezionati al controllo del codice sorgente**.

- Menu di scelta rapida (progetto/soluzione), **Aggiungi soluzione al controllo del codice sorgente**.

- Aggiungi dal controllo del codice sorgente: **file**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**.

- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], è disponibile anche l'aggiunta dal controllo del codice sorgente da **file**, **Aggiungi**, **progetto esistente**. controllare la posizione del [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)].

  > [!NOTE]
  > In questo test è possibile utilizzare un percorso di un file locale o di un IIS locale (server Web).

## <a name="expected-behavior"></a>Comportamento previsto

- Per ogni tipo di progetto supportato, un utente deve essere in grado di aggiungere il controllo del codice sorgente "Aggiungi a" e "Apri da".

- Quando un progetto viene aggiunto al controllo del codice sorgente, viene creato un corrispondente \<*nomeprogetto*> file vspscc (file di hint di progetto). Contiene l'elenco dei file di esclusione e le informazioni di connessione. Non eliminare questo file perché contiene informazioni specifiche per il progetto.

- Quando viene aggiunta una soluzione al controllo del codice sorgente, viene creato un file \<*solutionname*>. vssscc (Triple S) corrispondente. Il file di testo contiene le informazioni di connessione e un elenco di file di esclusione, analogamente al file di hint di progetto. Questo file è temporaneo ed esiste solo nel database del controllo del codice sorgente.

- Quando una soluzione viene aperta dal controllo del codice sorgente, un file \<*solutionname*>. vsscc (Double S) esistente solo nel database del controllo del codice sorgente viene creato localmente in un file temporaneo. Questo file contiene il percorso dalla cartella della connessione della soluzione al file di soluzione. Questo file è temporaneo e la copia locale viene eliminata al termine dell'operazione di apertura dal controllo del codice sorgente.

- Dopo l'aggiunta di un progetto al controllo del codice sorgente, è possibile eseguire qualsiasi azione di controllo del codice sorgente (Estrai, Ottieni e così via).

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test Aggiungi a/Apri dal controllo del codice sorgente.

### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: aggiungere una soluzione al controllo del codice sorgente
 Questa test case è incentrata sull'aggiunta di soluzioni al controllo del codice sorgente.

|Operazione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere una soluzione contenente un progetto client al controllo del codice sorgente|1. creare un progetto client.<br />2. aggiungere la soluzione al controllo del codice sorgente (**file**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|La soluzione o il progetto è stato aggiunto al controllo del codice sorgente.|
|Aggiungere una soluzione contenente un file System o un progetto Web IIS locale al controllo del codice sorgente|1. creare un file System o un progetto Web IIS locale (usare il pulsante Sfoglia per puntare al percorso del progetto; il percorso determina quale tipo di progetto Web viene creato).<br />2. aggiungere la soluzione al controllo del codice sorgente (**file**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|La soluzione o il progetto è stato aggiunto al controllo del codice sorgente.|
|Aggiungere una soluzione contenente un progetto Web del sito remoto al controllo del codice sorgente|1. creare un progetto Web del sito remoto.<br />2. aggiungere la soluzione al controllo del codice sorgente (**file**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).<br />3. fare clic su **OK** nella finestra di dialogo di avviso di accesso a FrontPage.|La soluzione è stata aggiunta al controllo del codice sorgente.<br /><br /> Il progetto di sito remoto non è sotto il controllo del codice sorgente. I progetti di siti remoti devono essere controllati dal proprio server IIS.|
|Aggiungere una singola soluzione di progetto al controllo del codice sorgente usando **Aggiungi progetti selezionati al controllo del codice sorgente**.|1. creare una soluzione di progetto singolo.<br />2. aggiungere solo la soluzione al controllo del codice sorgente come selezione (**file**, **controllo del codice sorgente**, **Aggiungi progetti selezionati al controllo del codice sorgente**). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. aggiungere il progetto al controllo del codice sorgente come selezione (**file**, **controllo del codice sorgente**, **Aggiungi progetti selezionati al controllo del codice sorgente**).<br />4. fare clic su **Sì** per aggiungere il progetto nello stesso percorso.<br />5. fare clic su **Estrai** nella finestra di dialogo **Estrai per la modifica** .|`Result from Step 2:`<br /><br /> Il progetto e tutti i file all'interno del progetto hanno un indicatore di controllo del codice sorgente estratto e una descrizione comando Visualizza "non incluso nel controllo del codice sorgente".<br /><br /> `Result from Step 5:`<br /><br /> Il progetto e il file di soluzione si trovano nella stessa cartella del controllo del codice sorgente.|
|Annulla l'aggiunta di una soluzione al controllo del codice sorgente|1. creare una soluzione di progetto singolo.<br />2. tentativo di aggiungere il progetto e la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Annulla dopo l'utente nel sistema di controllo del codice sorgente.|`Result from Step 2:`<br /><br /> La finestra di dialogo Imposta controllo del codice sorgente della posizione del progetto viene visualizzata una sola volta.<br /><br /> `Result from Step 3:`<br /><br /> Aggiunta progetto annullata, progetto/soluzione non è sotto il controllo del codice sorgente e tutti i menu Aggiungi a controllo del codice sorgente sono ancora disponibili.|

### <a name="case-1b-open-solution-from-source-control"></a>Caso 1B. Apri soluzione dal controllo del codice sorgente
 Questa test case è incentrata sull'apertura di soluzioni dal controllo del codice sorgente.

|Operazione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aprire una soluzione contenente un progetto client dal controllo del codice sorgente|1. creare un progetto client.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|Soluzione/progetto aperto dal controllo del codice sorgente.|
|Aprire una soluzione contenente un progetto Web locale o IIS dal controllo del codice sorgente|1. creare un progetto Web locale o IIS.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|Soluzione/progetto aperto dal controllo del codice sorgente.|
|Aprire una soluzione contenente un progetto Web di un sito remoto dal controllo del codice sorgente|1. creare un progetto Web del sito remoto.<br />2. aggiungere la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in una nuova posizione.|`Result from Step 2:`<br /><br /> Il Web del sito remoto non è sotto il controllo del codice sorgente.<br /><br /> `Result from Step 4:`<br /><br /> Soluzione aperta dal controllo del codice sorgente.<br /><br /> Il progetto di sito remoto viene caricato, ma non è sotto il controllo del codice sorgente.|

### <a name="case-1c-add-solution-from-source-control"></a>Caso 1C: aggiungere una soluzione dal controllo del codice sorgente
 Questa test case è incentrata sull'aggiunta di soluzioni dal controllo del codice sorgente.

|Operazione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungi a soluzione vuota-una soluzione di progetto singolo|1. creare una soluzione di progetto singolo.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. chiudere la soluzione.<br />4. creare una seconda soluzione vuota.<br />5. aggiungere la soluzione precedentemente controllata dal controllo del codice sorgente (**file**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato in **Esplora soluzioni** ed è archiviato.|
|Aggiungi a soluzione con singolo progetto-progetto singolo|1. creare una soluzione con un singolo progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. chiudere la soluzione.<br />4. creare una seconda soluzione vuota.<br />5. aggiungere la soluzione precedentemente controllata dal controllo del codice sorgente (**file**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato in **Esplora soluzioni** ed è archiviato.|
|Aggiungi alla soluzione: aggiunta della soluzione al controllo del codice sorgente tramite selezione|1. creare una soluzione con un progetto.<br />2. aggiungere solo la soluzione al controllo del codice sorgente come selezione. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. chiudere la soluzione.<br />4. creare una nuova soluzione.<br />5. aggiungere la soluzione precedentemente controllata dal controllo del codice sorgente (**file**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|`Result from Step 2:`<br /><br /> Il progetto non è sotto il controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> Se la prima soluzione aveva elementi di soluzione, non è possibile aggiungerli dal controllo del codice sorgente, in modo che non vengano visualizzati.<br /><br /> Il progetto dalla prima soluzione viene visualizzato come non disponibile.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)