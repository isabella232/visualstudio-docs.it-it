---
title: Visualizzare le dipendenze tra i file di origine e di intestazione C++
description: Fornisce informazioni sulle mappe del codice per i progetti C++.
ms.date: 05/16/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
ms.custom: SEO-VS-2020
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9c2aa1e49c0465fcf75917f0d9bd134962794c74
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99861751"
---
# <a name="code-maps-for-c-projects"></a>Mappe codice per progetti C++

Per creare mappe più complete per i progetti C++, impostare l'opzione del compilatore di informazioni di visualizzazione (**/FR**) su tali progetti. In caso contrario, viene visualizzato un messaggio con la richiesta di impostare l'opzione. Se si seleziona **OK**, l'opzione viene impostata solo per la mappa corrente. È possibile scegliere di nascondere il messaggio per tutte le mappe successive.

Quando si apre una soluzione che contiene progetti Visual C++, l'aggiornamento del database di IntelliSense potrebbe richiedere del tempo. Durante questo periodo, potrebbe non essere possibile creare mappe codice per file di intestazione (*. h* o `#include` ) fino al termine dell'aggiornamento del database IntelliSense. È possibile monitorare lo stato di avanzamento dell'aggiornamento nella barra di stato di Visual Studio.

- Per visualizzare le dipendenze tra tutti i file di origine e i file di intestazione nella soluzione, selezionare **architettura**  >  **Genera grafico dei file di inclusione**.

   ![Grafico delle dipendenze per il codice nativo](../modeling/media/dependencygraphgeneral_nativecode.png)

- Per visualizzare le dipendenze tra i file attualmente aperti e i file di origine e i file di intestazione correlati, aprire il file di origine o il file di intestazione. Aprire il menu di scelta rapida del file in un punto qualsiasi del file. Scegliere **Genera grafico dei file di inclusione**.

   ![Grafico delle dipendenze di primo livello per il file con estensione h](../modeling/media/dependencygraph_native_firstlevel.png)

## <a name="troubleshoot-code-maps-for-c-and-c-code"></a>Risolvere i problemi relativi alle mappe codici per il codice C e C++

Gli elementi seguenti non sono supportati nel codice C e C++:

- I tipi di base non vengono visualizzati nelle mappe che includono la gerarchia padre.

- La maggior parte delle voci di menu **Mostra** non è disponibile per il codice C e C++.

Questi problemi possono verificarsi quando si creano mappe del codice per il codice C e C++:

|**Problema**|**Possibile causa**|**Risoluzione**|
|-|-|-|
|Non è stato possibile generare la mappa codice.|Nessun progetto nella soluzione è stato compilato correttamente.|Correggere gli errori di compilazione che si sono verificati, quindi rigenerare la mappa.|
|Quando si prova a generare una mappa codice dal menu **architettura** , Visual Studio smette di rispondere.|Il file di database del programma (con estensione pdb) potrebbe essere danneggiato.<br /><br /> Nel file pdb sono memorizzate informazioni di debug, ad esempio informazioni sui tipi, sui metodi e sui file di origine.|Ricompilare la soluzione e riprovare.|
|Alcune impostazioni per il database di esplorazione IntelliSense sono disabilitate.|Alcune impostazioni di IntelliSense potrebbero essere disabilitate nella finestra di dialogo **Opzioni** di Visual Studio.|Attivare le impostazioni per abilitarle.<br /><br /> Vedere [Opzioni, editor di testo, C/C++, avanzate](../ide/reference/options-text-editor-c-cpp-advanced.md).|
|Il messaggio **Metodi sconosciuti** viene visualizzato su un nodo di metodo.<br /><br /> Questo problema si verifica perché non è possibile risolvere il nome del metodo.|Il file binario potrebbe non disporre di una tabella di rilocazione di base.|Attivare l'opzione **/FIXED:NO** nel linker.|
||Il file di database del programma (con estensione pdb) potrebbe non essere compilato.<br /><br /> Nel file pdb sono memorizzate informazioni di debug, ad esempio informazioni sui tipi, sui metodi e sui file di origine.|Attivare l'opzione **/DEBUG** nel linker.|
||Non è possibile aprire o trovare il file pdb nei percorsi previsti.|Verificare che il file pdb esista nei percorsi previsti.|
||Le informazioni di debug sono state rimosse dal file pdb.|Se nel linker è stata usata l'opzione **/PDBSTRIPPED** , includere il file pdb completo.|
||Il chiamante non è una funzione e non è un thunk nel file binario o un puntatore nella sezione di dati.|Quando il chiamante è un thunk, provare a usare `_declspec(dllimport)` per evitare il thunk.|

## <a name="see-also"></a>Vedi anche

- [Eseguire il mapping delle dipendenze con le mappe codice](../modeling/map-dependencies-across-your-solutions.md)
