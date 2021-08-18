---
title: 'Area di test 1: Aggiungere To-Open dal controllo del codice sorgente | Microsoft Docs'
description: Questa area di test del plug-in del controllo del codice sorgente illustra l'inserimento di soluzioni o progetti nel controllo del codice sorgente e il loro recupero dal controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 1f404b2d4ff41482fa492eedb17261618366934c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137613"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Area di test 1: aggiungere o aprire elementi dal controllo del codice sorgente
Questa area di test del plug-in del controllo del codice sorgente illustra l'inserimento di soluzioni o progetti nel controllo del codice sorgente e il loro recupero dal controllo del codice sorgente.

## <a name="command-menu-access"></a>Accesso al menu di comando
 Nei test case vengono usati i percorsi di menu dell'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato seguenti:

- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , aprire dal controllo del codice **sorgente: File**, Apri , **Project** / **soluzione**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] percorso .

- Per altri plug-in del controllo del codice sorgente, aprire dal controllo del codice sorgente: **File**, **Controllo del codice sorgente**, Apri dal controllo del codice **sorgente**.

- Aggiungi al controllo del codice sorgente: **File**, Controllo **del codice sorgente**, Aggiungi soluzione al **file** di controllo del codice **sorgente**, Controllo del codice sorgente , **Aggiungi progetti selezionati al controllo del codice sorgente**.

- Menu di scelta rapida (Project/Soluzione), **Aggiungi soluzione al controllo del codice sorgente.**

- Aggiungere dal controllo del codice sorgente: **File**, **Controllo del codice sorgente**, Project dal controllo del codice **sorgente**.

- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] , l'aggiunta dal controllo del codice sorgente è disponibile anche da **File**, **Aggiungi**, Project esistente . Cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] percorso .

  > [!NOTE]
  > In questo test è possibile usare un percorso di un file locale o di un IIS locale (server Web).

## <a name="expected-behavior"></a>Comportamento previsto

- Per ogni tipo di progetto supportato, un utente deve essere in grado di "Aggiungere a" e "Apri da" controllo del codice sorgente.

- Quando un progetto viene aggiunto al controllo del codice sorgente, viene creato un \<*ProjectName*> file con estensione vspscc (Project hint) corrispondente. Contiene l'elenco di file di esclusione e le informazioni di connessione. Non eliminare questo file perché contiene informazioni specifiche del progetto.

- Quando una soluzione viene aggiunta al controllo del codice sorgente, viene creato un file con estensione \<*SolutionName*> vssscc (triple S) corrispondente. Il file di testo contiene informazioni di connessione e un elenco di file di esclusione, simile al file dei suggerimenti per il progetto. Questo file è temporaneo ed esiste solo nel database del controllo del codice sorgente.

- Quando una soluzione viene aperta dal controllo del codice sorgente, un file con estensione vsscc (S doppio) esistente solo nel database del controllo del codice sorgente viene creato \<*SolutionName*> localmente in un file temporaneo. Questo file contiene il percorso dalla cartella di connessione della soluzione al file della soluzione. Questo file è temporaneo e la copia locale viene eliminata al termine dell'operazione "Apri dal controllo del codice sorgente".

- Dopo aver aggiunto un progetto al controllo del codice sorgente, è possibile eseguire qualsiasi azione di controllo del codice sorgente su di esso (Estrai, Ottieni e così via).

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test Aggiungi a/Apri dal controllo del codice sorgente.

### <a name="case-1a-add-solution-to-source-control"></a>Caso 1a: Aggiungere una soluzione al controllo del codice sorgente
 Questa test case incentrata sull'aggiunta di soluzioni al controllo del codice sorgente.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere una soluzione contenente un progetto client al controllo del codice sorgente|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente (**File**, **Controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|Soluzione/Project è stata aggiunta al controllo del codice sorgente.|
|Aggiungere una soluzione contenente un file system o un progetto Web IIS locale al controllo del codice sorgente|1. Creare un file system o un progetto Web IIS locale (usare il pulsante Sfoglia per puntare al percorso del progetto. Il percorso determina il tipo di progetto Web creato).<br />2. Aggiungere la soluzione al controllo del codice sorgente (**File**, **Controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|Soluzione/Project è stata aggiunta al controllo del codice sorgente.|
|Aggiungere una soluzione contenente un progetto Web del sito remoto al controllo del codice sorgente|1. Creare un progetto Web del sito remoto.<br />2. Aggiungere la soluzione al controllo del codice sorgente (**File**, **Controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).<br />3. Fare clic **su OK** nella finestra di dialogo di avviso Accesso a FrontPage.|La soluzione è stata aggiunta al controllo del codice sorgente.<br /><br /> Il progetto del sito remoto NON è sotto il controllo del codice sorgente. I progetti di sito remoto devono essere controllati dal proprio server IIS.|
|Aggiungere una singola soluzione di progetto al controllo del codice sorgente usando **Aggiungi progetti selezionati al controllo del codice sorgente.**|1. Creare una singola soluzione di progetto.<br />2. Aggiungere come selezione solo la soluzione al controllo del codice sorgente (**File**, **Controllo del** codice sorgente , Aggiungi progetti selezionati al controllo del **codice sorgente**). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Aggiungere un progetto al controllo del codice sorgente come selezione (**File**, **Controllo del** codice sorgente , Aggiungi progetti selezionati al controllo del **codice sorgente**).<br />4. **Fare clic su** Sì per aggiungere il progetto allo stesso percorso.<br />5. Fare clic su **Estrai nella finestra di dialogo Estrai** per modifica. |`Result from Step 2:`<br /><br /> Il progetto e tutti i file all'interno del progetto hanno un indicatore del controllo del codice sorgente estratto e una descrizione comando visualizza "Non in controllo del codice sorgente".<br /><br /> `Result from Step 5:`<br /><br /> Project file di soluzione e sono nella stessa cartella nel controllo del codice sorgente.|
|Annullare l'aggiunta di una soluzione al controllo del codice sorgente|1. Creare una singola soluzione di progetto.<br />2. Provare ad aggiungere il progetto e la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Annullare dopo aver fatto parte del sistema di controllo del codice sorgente.|`Result from Step 2:`<br /><br /> La finestra di dialogo Imposta controllo del codice sorgente percorso progetto viene visualizzata una sola volta.<br /><br /> `Result from Step 3:`<br /><br /> Project aggiunta annullata, progetto/soluzione NON è in controllo del codice sorgente e tutti i menu Aggiungi al controllo del codice sorgente sono ancora disponibili.|

### <a name="case-1b-open-solution-from-source-control"></a>Caso 1b. Aprire la soluzione dal controllo del codice sorgente
 Questa test case incentrata sull'apertura di soluzioni dal controllo del codice sorgente.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aprire una soluzione contenente un progetto client dal controllo del codice sorgente|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|Soluzione/Project aperta dal controllo del codice sorgente.|
|Aprire una soluzione contenente un progetto Web IIS o locale dal controllo del codice sorgente|1. Creare un progetto Web IIS o locale.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|Soluzione/Project aperta dal controllo del codice sorgente.|
|Aprire una soluzione contenente un progetto Web del sito remoto dal controllo del codice sorgente|1. Creare un progetto Web del sito remoto.<br />2. Aggiungere la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Chiudere la soluzione.<br />4. Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|`Result from Step 2:`<br /><br /> Il sito Web remoto NON è sotto il controllo del codice sorgente.<br /><br /> `Result from Step 4:`<br /><br /> Soluzione aperta dal controllo del codice sorgente.<br /><br /> Il progetto del sito remoto viene caricato, ma NON è sotto il controllo del codice sorgente.|

### <a name="case-1c-add-solution-from-source-control"></a>Caso 1c: Aggiungere una soluzione dal controllo del codice sorgente
 Questa test case incentrata sull'aggiunta di soluzioni dal controllo del codice sorgente.

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere alla soluzione vuota : una singola soluzione di progetto|1. Creare una singola soluzione di progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare una seconda soluzione vuota.<br />5. Aggiungere la soluzione controllata in precedenza dal controllo del codice sorgente (**File**, **Controllo** del codice sorgente , **Project controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato **Esplora soluzioni** ed è archiviato.|
|Aggiungere alla soluzione con un singolo progetto : singolo progetto|1. Creare una soluzione con un singolo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare una seconda soluzione vuota.<br />5. Aggiungere la soluzione controllata in precedenza dal controllo del codice sorgente (**File**, **Controllo** del codice sorgente , **Project controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato **Esplora soluzioni** ed è archiviato.|
|Aggiungi alla soluzione: soluzione aggiunta al controllo del codice sorgente in base alla selezione|1. Creare una soluzione con un progetto.<br />2. Aggiungere come selezione solo la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3. Chiudere la soluzione.<br />4. Creare una nuova soluzione.<br />5. Aggiungere la soluzione controllata in precedenza dal controllo del codice sorgente (**File**, **Controllo** del codice sorgente , **Project controllo del codice sorgente**).|`Result from Step 2:`<br /><br /> Project non è sotto il controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> Se la prima soluzione aveva elementi di soluzione, non possono essere aggiunti dal controllo del codice sorgente, quindi non vengono visualizzati.<br /><br /> Project dalla prima soluzione viene visualizzato come non disponibile.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
