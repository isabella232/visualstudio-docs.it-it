---
title: 'Area di prova 7: Condivisione Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd4c48e94015d95f5e56d465cdbf98562108d3b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704411"
---
# <a name="test-area-7-share"></a>Area di test 7: Condividere
Questa area di test riguarda la condivisione di elementi tra posizioni tramite il comando **Condividi.**

 Un'operazione hhare è l'apparente duplicazione di file ed elementi di cartella tra due o più posizioni all'interno di una gerarchia di file del controllo del codice sorgente. La duplicazione non si verifica realmente sul server, ma l'utente vede lo stesso file in due o più posizioni specificate. Ogni volta che vengono apportate modifiche a uno degli elementi condivisi, tali modifiche vengono visualizzate in tutte le altre posizioni condivise.

 La condivisione in cartelle funziona se si seleziona una cartella contenente almeno un file sotto il controllo del codice sorgente. Il comando share è disabilitato nelle seguenti condizioni:

- Se la cartella selezionata è una cartella vuota.

- Se è presente una cartella reale, ma non contiene file del controllo del codice sorgente.

- Se è presente una cartella virtuale, indipendentemente dal fatto che i file in controllo del codice sorgente sono in essa presenti o meno.

- Se è presente un progetto Web di sito remoto.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case vengono utilizzati i percorsi di menu dell'ambiente di sviluppo integrato seguenti.

 Condividi:**condivisione****del controllo del codice**->sorgente **file**->.

## <a name="expected-behavior"></a>Comportamento previsto

- Il file condiviso viene visualizzato nella posizione condivisa.

- La visualizzazione della cronologia dell'archivio versione del controllo del codice sorgente mostra che i file sono condivisi.

- La modifica di un file condiviso consente di modificare entrambe le posizioni del file.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test Condividi.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Condividere un file da un progetto caricato nel controllo del codice sorgente a un altro progetto caricato|1. Creare un nuovo progetto.<br />2. Aggiungere un secondo progetto alla soluzione.<br />3. Creare un file nel secondo progetto con un nome che non è nel primo progetto.<br />4. Aggiungere la soluzione al controllo del codice sorgente.<br />5. Selezionare il primo progetto.<br />6. Aprire la finestra di dialogo **Condividi** (**Condivisione****controllo** -> del codice sorgente**file** -> ).<br />7. Condividere il file dal secondo progetto al primo progetto.<br />8. Accettare **l'estrazione** se richiesto.|Comportamento previsto comune.|
|Condividere un file da un progetto a un altro|1. Creare un nuovo progetto.<br />2. Aggiungerlo al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare un secondo progetto (nuova soluzione).<br />5. Aggiungere la soluzione al controllo del codice sorgente.<br />6. Selezionare il progetto.<br />7. Aprire la finestra di dialogo **Condividi** (**Condivisione****controllo** -> del codice sorgente**file).** -> <br />8. Condividere un file dal progetto aggiunto in precedenza al progetto aperto.<br />9. Accettare **l'estrazione** se richiesto.|Comportamento previsto comune.|
|Condividere un file che non fa parte del progetto dal controllo del codice sorgente nel progetto attualmente caricato|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un file al controllo del codice sorgente che non fa parte del progetto o della soluzione.<br />4. Selezionare il progetto e aprire la finestra di dialogo **Condividi** **(Condivisione****del controllo del codice** -> sorgente**del file).** -> <br />5. Selezionare un file all'interno della finestra di dialogo **Condividi** che non esiste all'interno del progetto o della soluzione corrente e condividerlo.<br />6. Accettare **l'estrazione** se richiesto.|L'archivio del controllo del codice sorgente ha eseguito un Get, quindi il file si trova ora nel percorso locale del progetto.|
|Condividere i file all'interno dello stesso progetto in una cartella diversa|1. Selezionare **Estrai automaticamente** in **Strumenti** -> **Opzioni** -> **Controllo del codice sorgente**.<br />2. Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />3. Aggiungere una cartella al progetto.<br />4. Aggiungere un file alla cartella e archiviare la cartella.<br />5. Selezionare la cartella.<br />6. Aprire la finestra di dialogo **Condividi** (**Condivisione****controllo** -> del codice sorgente**file** -> ).<br />7. Condividere il file nella cartella selezionata.|Comportamento previsto comune.<br /><br /> La cartella deve essere archiviata con un file al suo contenuto prima di poter essere utilizzata per la condivisione.|
|Condivisione di una cartella nel progetto caricato - Ricorsivo|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Selezionare il progetto.<br />4. Aprire la finestra di dialogo **Condividi** (**Condivisione****controllo** -> del codice sorgente**file).** -> <br />5. Selezionare una cartella.<br />6. Condividere la cartella in modo ricorsivo nel progetto.|Comportamento previsto comune.|
|Condividere più file da un progetto a un altro|1. Creare un nuovo progetto con diversi file in esso.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare un nuovo progetto in una nuova soluzione.<br />5. Aggiungere la soluzione al controllo del codice sorgente.<br />6. Selezionare il progetto.<br />7. Aprire la finestra di dialogo **Condividi** (**Condivisione****controllo** -> del codice sorgente**file).** -> <br />8. Condividere diversi file dal progetto creato in precedenza al progetto attualmente aperto.|Comportamento previsto comune.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
