---
title: 'Area di test 1: Aggiungere o aprire dal controllo del codice sorgente | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], adding and opening solutions
- source control plug-ins, adding and opening solutions
ms.assetid: 5b3b5b08-5e9b-41be-ac72-c63957faed22
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3b50ff6c737b75fcdbd9a6fc265928301eeb4467
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842672"
---
# <a name="test-area-1-add-toopen-from-source-control"></a>Area di test 1: Aggiungere a / Apri dal controllo del codice sorgente
Questo controllo del codice sorgente del plug-in di test viene illustrata l'area immissione soluzioni o progetti di controllo del codice sorgente e il loro recupero dal controllo del codice sorgente.  
  
## <a name="command-menu-access"></a>Accesso a comandi di Menu  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] vengono usati percorsi di menu ambiente di sviluppo integrato nei test case:  
  
- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)]aprire dal controllo del codice sorgente: **File**, **aperta**, **Project**/**soluzione**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] posizione.  
  
- Per altre origine plug-in del controllo, aprire dal controllo del codice sorgente: **File**, **controllo del codice sorgente**, **Apri dal controllo del codice sorgente**.  
  
- Aggiungere al controllo del codice sorgente: **File**, **controllo del codice sorgente**, **Aggiungi soluzione al File di controllo di origine**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**.  
  
- Menu di scelta rapida (progetto/soluzione), **Aggiungi soluzione al controllo del codice sorgente**.  
  
- Aggiungere dal controllo del codice sorgente: **File**, **controllo del codice sorgente**, **aggiungere progetto dal controllo del codice sorgente**.  
  
- Per [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)], aggiungere dall'origine controllo è disponibile anche dal **File**, **Add**, **progetto esistente**; cercare nel [!INCLUDE[vsvss](../../extensibility/includes/vsvss_md.md)] posizione.  
  
  > [!NOTE]
  >  Un percorso di un file locale o un server IIS locale (server web) può essere utilizzato in questo test.  
  
## <a name="expected-behavior"></a>Comportamento previsto  
  
-   Per ogni tipo di progetto supportati, un utente deve essere in grado di "Add a" e "Aperto" dal controllo del codice sorgente.  
  
-   Quando viene aggiunto un progetto al controllo del codice sorgente, un oggetto corrispondente \< *NomeProgetto*> vspscc (file di progetto hint) viene creato. Contiene informazioni di connessione e l'elenco di file esclusione. Non eliminare questo file perché contiene informazioni specifiche per il progetto.  
  
-   Quando viene aggiunta una soluzione al controllo del codice sorgente, un oggetto corrispondente \< *SolutionName*> viene creato il file. vssscc (tripla S). Il file di testo contiene le informazioni di connessione e un elenco di file di esclusione, simile al file dei suggerimenti di progetto. Questo file è temporaneo ed esiste solo nel database del controllo del codice sorgente.  
  
-   Quando viene aperta una soluzione dal controllo del codice sorgente, un' \< *SolutionName*> file .vsscc (S double) che esiste solo nel database di controllo di origine, viene creato in locale in un file temporaneo. Questo file contiene il percorso dalla cartella di connessione della soluzione per il file della soluzione. Questo file è temporaneo e la copia locale viene eliminata quando l'operazione "Apri dal controllo del codice sorgente" è stata completata.  
  
-   Dopo l'aggiunta di un progetto di controllo del codice sorgente, è possibile eseguire le azioni di controllo sorgente su di esso (estrazione, Get e così via).  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'aggiunta a / Open dall'area di test di controllo del codice sorgente.  
  
### <a name="case-1a-add-solution-to-source-control"></a>Case 1a: Aggiungi soluzione al controllo del codice sorgente  
 Questo test case è incentrata sull'aggiunta di soluzioni di controllo del codice sorgente.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungi soluzione contenente un progetto di client di controllo del codice sorgente|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|Soluzione/progetto è stato aggiunto al controllo del codice sorgente.|  
|Aggiungi soluzione contenente un File System o un progetto Web IIS locale al controllo del codice sorgente|1.  Creare un File System o un progetto Web IIS locale (utilizzare sui puntini di sospensione per puntare al percorso del progetto; il percorso determina il tipo di progetto Web viene creato).<br />2.  Aggiungere la soluzione al controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).|Soluzione/progetto è stato aggiunto al controllo del codice sorgente.|  
|Aggiungi soluzione contenente un progetto Web sito remoto al controllo del codice sorgente|1.  Creare un progetto Web sito remoto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi soluzione al controllo del codice sorgente**).<br />3.  Fare clic su **OK** nella finestra di dialogo Avviso di accesso di FrontPage.|Soluzione è stata aggiunta al controllo del codice sorgente.<br /><br /> Progetto di sito remoto non è incluso nel controllo del codice sorgente. (I progetti di sito remoto devono essere controllati da un proprio server IIS).|  
|Aggiungi una soluzione di singolo progetto all'uso di controllo di origine **Aggiungi progetti selezionati a controllo del codice sorgente**.|1.  Creare una soluzione di singolo progetto.<br />2.  Aggiungere solo soluzioni al controllo del codice sorgente come selezione (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3.  Aggiungi progetto al controllo del codice sorgente come selezione (**File**, **controllo del codice sorgente**, **Aggiungi progetti selezionati a controllo del codice sorgente**).<br />4.  Fare clic su **Sì** per aggiungere il progetto nella stessa posizione.<br />5.  Fare clic su **Estrai** nelle **Estrai per la modifica** nella finestra di dialogo.|`Result from Step 2:`<br /><br /> Il progetto e tutti i file all'interno del progetto dispongono di una selezione out indicatore del controllo di origine e una descrizione comando Visualizza "non sotto controllo del codice sorgente".<br /><br /> `Result from Step 5:`<br /><br /> File di progetto e soluzione sono nella stessa cartella nel controllo del codice sorgente.|  
|Annullare l'aggiunta di una soluzione al controllo del codice sorgente|1.  Creare una soluzione di singolo progetto.<br />2.  Tentativo di aggiungere progetti e soluzioni al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3.  Annullare dopo essere entrati nel controllo del codice sorgente.|`Result from Step 2:`<br /><br /> La finestra di dialogo Set progetto percorso origine controllo viene visualizzata una sola volta.<br /><br /> `Result from Step 3:`<br /><br /> Progetto aggiunta annullata, progetto/soluzione non è incluso nel controllo del codice sorgente e aggiungere al menu di controllo di origine ancora disponibili.|  
  
### <a name="case-1b-open-solution-from-source-control"></a>1b case. Apri soluzione dal controllo del codice sorgente  
 Questo test case è incentrato sull'apertura di soluzioni dal controllo del codice sorgente.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aprire una soluzione contenente un progetto client dal controllo del codice sorgente|1.  Creare un progetto client.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|Soluzione/progetto aperto dal controllo del codice sorgente.|  
|Aprire una soluzione contenente un locale o un progetto Web di IIS dal controllo del codice sorgente|1.  Creare un progetto di Web IIS o locale.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|Soluzione/progetto aperto dal controllo del codice sorgente.|  
|Aprire una soluzione contenente un progetto Web sito remoto dal controllo del codice sorgente|1.  Creare un progetto Web sito remoto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3.  Chiudere la soluzione.<br />4.  Aprire la soluzione dal controllo del codice sorgente in un nuovo percorso.|`Result from Step 2:`<br /><br /> Web sito remoto non è incluso nel controllo del codice sorgente.<br /><br /> `Result from Step 4:`<br /><br /> Soluzione aperta dal controllo del codice sorgente.<br /><br /> Progetto di sito remoto viene caricato, ma non è incluso nel controllo del codice sorgente.|  
  
### <a name="case-1c-add-solution-from-source-control"></a>Caso 1c: Aggiungi soluzione dal controllo del codice sorgente  
 Questo test case è incentrata sull'aggiunta di soluzioni dal controllo del codice sorgente.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungi a soluzione vuota, ovvero una singolo progetto soluzione|1.  Creare una soluzione di singolo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare una seconda soluzione vuota.<br />5.  Aggiungere la soluzione in precedenza controllata dal controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato nella **Esplora soluzioni** e viene archiviato.|  
|Aggiungere alla soluzione con singolo progetto, ovvero singolo progetto|1.  Creare una soluzione con un singolo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare una seconda soluzione vuota.<br />5.  Aggiungere la soluzione in precedenza controllata dal controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|Il progetto aggiunto viene visualizzato nella **Esplora soluzioni** e viene archiviato.|  
|Aggiungere alla soluzione-soluzione aggiunto al controllo del codice sorgente in base a selezione|1.  Creare una soluzione con un progetto.<br />2.  Aggiungere solo soluzione al controllo del codice sorgente come selezione. Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />3.  Chiudere la soluzione.<br />4.  Creare una nuova soluzione.<br />5.  Aggiungere la soluzione in precedenza controllata dal controllo del codice sorgente (**File**, **controllo del codice sorgente**, **Aggiungi progetto dal controllo del codice sorgente**).|`Result from Step 2:`<br /><br /> Progetto non è incluso nel controllo del codice sorgente.<br /><br /> `Result from Step 5:`<br /><br /> Se la prima soluzione dispone di elementi di soluzione, non possono essere aggiunti dal controllo del codice sorgente, in modo che non sono visualizzate.<br /><br /> Progetto dalla soluzione prima viene visualizzato come non disponibile.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)