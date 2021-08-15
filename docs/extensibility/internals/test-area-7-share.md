---
title: 'Area di test 7: Condividere | Microsoft Docs'
description: Questa area di test del controllo del codice sorgente illustra la condivisione di elementi tra percorsi usando il comando Condividi per il plug-in Visual Studio di controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], sharing items
- source control plug-ins, sharing items
ms.assetid: 6ec4780a-bda4-4327-bb3e-c6c9e7eabf35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 23b5564470551b1732e57e4cf07cbd191c069d21afd6ac1f0b563f596c852fcd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431773"
---
# <a name="test-area-7-share"></a>Area di test 7: Condividi
Questa area di test illustra la condivisione di elementi tra percorsi tramite il **comando** Condividi.

 Un'operazione hhare è la duplicazione apparente di file ed elementi di cartelle tra due o più percorsi all'interno di una gerarchia di file del controllo del codice sorgente. La duplicazione non si verifica effettivamente nel server, ma l'utente visualizza lo stesso file in due o più percorsi specificati. Ogni volta che vengono apportate modifiche a uno degli elementi condivisi, tali modifiche vengono visualizzate in tutte le altre posizioni condivise.

 La condivisione in cartelle funziona se si seleziona una cartella in cui è presente almeno un file nel controllo del codice sorgente. Il comando di condivisione è disabilitato nelle condizioni seguenti:

- Se la cartella selezionata è una cartella vuota.

- Se è presente una cartella reale, ma non contiene file di controllo del codice sorgente.

- Se è presente una cartella virtuale, indipendentemente dal fatto che i file nel controllo del codice sorgente siano o meno presenti.

- Se è presente un progetto Web del sito remoto.

## <a name="command-menu-access"></a>Accesso al menu di comando
 Nei test case vengono usati i percorsi di menu dell'ambiente di sviluppo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato seguenti.

 Condivisione: **condivisione del** controllo del codice ->  -> **sorgente file.**

## <a name="expected-behavior"></a>Comportamento previsto

- Il file condiviso viene visualizzato nel percorso condiviso.

- La visualizzazione della cronologia dell'archivio versioni del controllo del codice sorgente mostra che i file sono condivisi.

- La modifica di un file condiviso modifica entrambi i percorsi del file.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test Condividi.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Condividere un file da un progetto caricato nel controllo del codice sorgente a un altro progetto caricato|1. Creare un nuovo progetto.<br />2. Aggiungere un secondo progetto alla soluzione.<br />3. Creare un file nel secondo progetto con un nome non presente nel primo progetto.<br />4. Aggiungere la soluzione al controllo del codice sorgente.<br />5. Selezionare il primo progetto.<br />6. Aprire **la finestra di dialogo** Condividi (**Condivisione** controllo del  ->  **codice**  ->  **sorgente file**).<br />7. Condividere il file dal secondo progetto al primo progetto.<br />8. Accettare **l'estrazione,** se richiesto.|Comportamento previsto comune.|
|Condividere un file da un progetto a un altro|1. Creare un nuovo progetto.<br />2. Aggiungerlo al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare un secondo progetto (nuova soluzione).<br />5. Aggiungere la soluzione al controllo del codice sorgente.<br />6. Selezionare il progetto.<br />7. Aprire la finestra **di dialogo** Condividi (**Condivisione** controllo  ->  **codice sorgente**  ->  **file**).<br />8. Condividere un file dal progetto aggiunto in precedenza al progetto aperto.<br />9. Accettare **l'estrazione,** se richiesto.|Comportamento previsto comune.|
|Condividere un file che non fa parte del progetto dal controllo del codice sorgente nel progetto attualmente caricato|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un file al controllo del codice sorgente che non fa parte del progetto o della soluzione.<br />4. Selezionare il progetto e aprire la **finestra di** dialogo Condividi (**Condivisione** controllo del  ->  **codice**  ->  **sorgente file**).<br />5. Selezionare un file nella finestra **di** dialogo Condividi che non esiste nel progetto o nella soluzione corrente e condividerlo.<br />6. Accettare **l'estrazione,** se richiesto.|L'archivio del controllo del codice sorgente ha eseguito un'operazione Get, quindi il file si trova ora nel percorso locale del progetto.|
|Condividere i file all'interno dello stesso progetto in una cartella diversa|1. Selezionare **Estrai automaticamente** in **Strumenti**  ->  **Opzioni Controllo del** codice  ->  **sorgente**.<br />2. Creare un nuovo progetto e aggiungerlo al controllo del codice sorgente.<br />3. Aggiungere una cartella al progetto.<br />4. Aggiungere un file alla cartella e archiviare la cartella.<br />5. Selezionare la cartella.<br />6. Aprire **la finestra di dialogo** Condividi (**Condivisione** controllo del  ->  **codice**  ->  **sorgente file**).<br />7. Condividere il file nella cartella selezionata.|Comportamento previsto comune.<br /><br /> La cartella deve essere archiviata con un file in essa contenuto prima di poter essere usata per la condivisione.|
|Condividere una cartella nella cartella caricata Project - Ricorsiva|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Selezionare il progetto.<br />4. Aprire la finestra **di dialogo** Condividi (**Condivisione** controllo  ->  **codice**  ->  **sorgente file**).<br />5. Selezionare una cartella.<br />6. Condividere la cartella in modo ricorsivo nel progetto.|Comportamento previsto comune.|
|Condividere più file da un progetto a un altro|1. Creare un nuovo progetto con diversi file.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Chiudere la soluzione.<br />4. Creare un nuovo progetto in una nuova soluzione.<br />5. Aggiungere la soluzione al controllo del codice sorgente.<br />6. Selezionare il progetto.<br />7. Aprire la finestra **di dialogo** Condividi (**Condivisione** controllo  ->  **codice sorgente**  ->  **file**).<br />8. Condividere diversi file dal progetto creato in precedenza al progetto attualmente aperto.|Comportamento previsto comune.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
