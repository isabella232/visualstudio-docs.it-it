---
title: 'Area di test 7: Condivisione | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca148ccf4c3ca296fd03e9c3c25e2eacc9b6cf93
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941992"
---
# <a name="test-area-7-share"></a>Area di test 7: Condividi
Questa area di test illustra gli elementi di condivisione tra località, tramite il **condivisione** comando.  
  
 È un'operazione di hhare la duplicazione apparente di file e cartella elementi tra due o più posizioni all'interno di una gerarchia di file di controllo di origine. Nel server non è realmente verificarsi la duplicazione, ma l'utente di visualizzare lo stesso file in due o più percorsi specificati. Ogni volta che vengono apportate modifiche per gli elementi condivisi, tali modifiche vengono visualizzati in tutti gli altri percorsi condivisi.  
  
 Condivisione in cartelle funziona se si seleziona una cartella con almeno un file sotto controllo del codice sorgente in esso. Il comando di condivisione è disabilitato nelle condizioni seguenti:  
  
-   Se la cartella selezionata è una cartella vuota.  
  
-   Se è presente una cartella reale, ma non contiene alcun file di controllo di origine.  
  
-   Se è presente una cartella virtuale, se i file nel controllo del codice sorgente sono in esso o non.  
  
-   Se è presente un progetti Web sito remoto.  
  
## <a name="command-menu-access"></a>Accesso a comandi di Menu  
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nei test case vengono usati percorsi di menu ambiente di sviluppo integrato.  
  
 Condividere: **File**->**controllo del codice sorgente**->**condivisione**.  
  
## <a name="expected-behavior"></a>Comportamento previsto  
  
-   File condivisi viene visualizzato in percorso condiviso.  
  
-   Visualizzazione origine controllo versione archivio della cronologia mostra che i file sono condivisi.  
  
-   Modifica di un file condiviso consente di modificare entrambe le posizioni del file.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'area di test di condivisione.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Condividere un file da un progetto caricato nel controllo del codice sorgente in un altro progetto caricato|1.  Creare un nuovo progetto.<br />2.  Aggiungere un secondo progetto alla soluzione.<br />3.  Creare un file nel progetto secondo con un nome che non è presente nel primo progetto.<br />4.  Aggiungere la soluzione al controllo del codice sorgente.<br />5.  Selezionare il primo progetto.<br />6.  Aprire **Share** finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />7.  Condividere il file dal progetto secondo al primo progetto.<br />8.  Accettare **Estrai** se richiesto.|Comportamento previsto comune.|  
|Condividere un file da un progetto a un altro|1.  Creare un nuovo progetto.<br />2.  Aggiungerlo al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare un secondo progetto (nuova soluzione).<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Selezionare il progetto.<br />7.  Aprire il **Share** finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />8.  Condividere un file dal progetto precedentemente aggiunto al progetto aperto.<br />9. Accettare **Estrai** se richiesto.|Comportamento previsto comune.|  
|Condividere un file non fa parte del progetto dal controllo del codice sorgente nel progetto attualmente caricato|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file al controllo del codice sorgente che non fa parte del progetto o della soluzione.<br />4.  Selezionare il progetto e aprire il **Share** finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />5.  Selezionare un file all'interno di **condividere** finestra di dialogo che non esiste all'interno del progetto corrente o una soluzione e condividerlo.<br />6.  Accettare **Estrai** se richiesto.|Archivio del controllo codice sorgente ha eseguito un'operazione Get, in modo che il file è ora in corrispondenza della posizione locale del progetto.|  
|Condivisione di file all'interno dello stesso progetto a un'altra cartella|1.  Selezionare **Estrai automaticamente** nelle **Tools** -> **opzioni** -> **controllo del codice sorgente**.<br />2.  Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />3.  Aggiungere una cartella al progetto.<br />4.  Aggiungere un file nella cartella e archiviare la cartella.<br />5.  Selezionare la cartella.<br />6.  Aprire **Share** finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />7.  Condividere il file nella cartella selezionata.|Comportamento previsto comune.<br /><br /> Prima che possa essere utilizzato per la condivisione della cartella deve essere selezionata con un file in essa contenuti.|  
|Condividere una cartella nel progetto caricato, ricorsivi|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Selezionare il progetto.<br />4.  Aprire il **Share** finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />5.  Selezionare una cartella.<br />6.  Condividere la cartella in modo ricorsivo nel progetto.|Comportamento previsto comune.|  
|Condivisione di file diversi da un progetto a un altro|1.  Creare un nuovo progetto con molti file.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Chiudere la soluzione.<br />4.  Creare un nuovo progetto in una nuova soluzione.<br />5.  Aggiungere la soluzione al controllo del codice sorgente.<br />6.  Selezionare il progetto.<br />7.  Aprire il **Share** finestra di dialogo (**File** -> **controllo del codice sorgente** -> **condivisione**).<br />8.  Condividere i file diversi dal progetto creato in precedenza al progetto attualmente aperto.|Comportamento previsto comune.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)