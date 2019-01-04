---
title: Visualizzare le dipendenze tra file di intestazione e i file di origine C++
ms.date: 05/16/2018
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- multiple
ms.openlocfilehash: b5fc8e84100d8b7ceb2b529e7b1630e644ebc9f7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53968657"
---
# <a name="code-maps-for-c-projects"></a>Le mappe codice per i progetti C++

Per creare mappe più complete per i progetti C++, impostare l'opzione del compilatore di informazioni di visualizzazione (**/FR**) su tali progetti. In caso contrario, viene visualizzato un messaggio con la richiesta di impostare l'opzione. Se si seleziona **OK**, l'opzione viene impostata solo per la mappa corrente. È possibile scegliere di nascondere il messaggio per tutte le mappe successive.

Quando si apre una soluzione che contiene progetti Visual C++, l'aggiornamento del database di IntelliSense potrebbe richiedere del tempo. Durante questo periodo, non è in grado di creare mappe codice per l'intestazione (*h* o `#include`) i file fino a quando il database di IntelliSense ha completato l'aggiornamento. È possibile monitorare lo stato di avanzamento dell'aggiornamento nella barra di stato di Visual Studio.

- Per visualizzare le dipendenze tra tutti i file di origine e i file di intestazione nella soluzione, selezionare **Architecture** > **Genera grafico dei file di inclusione**.

   ![Grafico delle dipendenze per il codice nativo](../modeling/media/dependencygraphgeneral_nativecode.png)

- Per visualizzare le dipendenze tra i file attualmente aperti e i file di origine e i file di intestazione correlati, aprire il file di origine o il file di intestazione. Aprire il menu di scelta rapida del file in un punto qualsiasi del file. Scegliere **Genera grafico dei file di inclusione**.

   ![Grafico delle dipendenze di primo livello per il file con estensione h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Risolvere i problemi delle mappe codici per codice C e C++

Gli elementi seguenti non sono supportati nel codice C e C++:

- I tipi di base non vengono visualizzati nelle mappe che includono la gerarchia padre.

- La maggior parte delle voci di menu **Mostra** non è disponibile per il codice C e C++.

Questi problemi potrebbero verificarsi quando si creano mappe codici per codice C e C++:

|**Problema**|**Possibile causa**|**Risoluzione**|
|-|-|-|
|Non è stato possibile generare la mappa codice.|Nessun progetto nella soluzione è stato compilato correttamente.|Correggere gli errori di compilazione che si sono verificati, quindi rigenerare la mappa.|
|Visual Studio si blocca quando si prova a generare una mappa codice dal **architettura** menu.|Il file di database del programma (con estensione pdb) potrebbe essere danneggiato.<br /><br /> Nel file pdb sono memorizzate informazioni di debug, ad esempio informazioni sui tipi, sui metodi e sui file di origine.|Ricompilare la soluzione e riprovare.|
|Alcune impostazioni per il database di esplorazione IntelliSense sono disabilitate.|Alcune impostazioni di IntelliSense potrebbero essere disabilitate in Visual Studio **opzioni** nella finestra di dialogo.|Attivare le impostazioni per abilitarle.<br /><br /> Visualizzare [opzioni, Editor di testo, C/C++, avanzate](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Il messaggio **Metodi sconosciuti** viene visualizzato su un nodo di metodo.<br /><br /> Questo problema si verifica perché non è possibile risolvere il nome del metodo.|Il file binario potrebbe non disporre di una tabella di rilocazione di base.|Attivare l'opzione **/FIXED:NO** nel linker.|
||Il file di database del programma (con estensione pdb) potrebbe non essere compilato.<br /><br /> Nel file pdb sono memorizzate informazioni di debug, ad esempio informazioni sui tipi, sui metodi e sui file di origine.|Attivare l'opzione **/DEBUG** nel linker.|
||Non è possibile aprire o trovare il file pdb nei percorsi previsti.|Verificare che il file pdb esista nei percorsi previsti.|
||Le informazioni di debug sono state rimosse dal file pdb.|Se nel linker è stata usata l'opzione **/PDBSTRIPPED** , includere il file pdb completo.|
||Il chiamante non è una funzione e non è un thunk nel file binario o un puntatore nella sezione di dati.|Quando il chiamante è un thunk, provare a usare `_declspec(dllimport)` per evitare il thunk.|

## <a name="see-also"></a>Vedere anche

- [Mappare le dipendenze con le mappe codici](../modeling/map-dependencies-across-your-solutions.md)