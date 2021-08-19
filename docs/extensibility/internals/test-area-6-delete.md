---
title: 'Area di test 6: Eliminare | Microsoft Docs'
description: Questa area di test del controllo del codice sorgente illustra le azioni di Esplora soluzioni per il plug-in Visual Studio controllo del codice sorgente.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: dd27a0ac99faf9ec2ab4b53fcbae31257e72202f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158749"
---
# <a name="test-area-6-delete"></a>Area di test 6: Eliminare
Questa area di test del plug-in del controllo del codice sorgente illustra le azioni di eliminazione.

 Il controllo del codice sorgente risponde alle azioni di eliminazione in **Esplora soluzioni**.

 Di seguito è riportato un elenco di elementi che è possibile eliminare:

- File

- Cartelle

- Project

  A seconda del tipo di progetto,  è possibile scegliere Rimuovi il  progetto (lascia i file su disco) o Elimina il progetto (rimuove i file su disco). L'azione rimuove il progetto o l'elemento **da Esplora soluzioni**.

## <a name="expected-behavior"></a>Comportamento previsto
 Il comportamento previsto per i test case nell'area di test di eliminazione è:

- L'elemento eliminato non è più visibile **all'interno Esplora soluzioni**.

- L'elemento padre del progetto o dell'elemento eliminato viene estratto in base alle esigenze (possibilmente con un prompt).

- Dopo aver eliminato un elemento estratto o aggiunto, NON viene visualizzato nella finestra **Archiviazioni in** sospeso.

- L'elemento esiste ancora nell'archivio del controllo del codice sorgente, anche dopo l'eliminazione, e deve essere eliminato manualmente.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Eliminare un progetto client|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Rimuovere l'intero progetto dalla soluzione|Comportamento previsto comune.|
|Eliminare un file vuoto|1. Creare un progetto client.<br />2. Aggiungere un file a zero byte al progetto.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare il file ed eliminarlo.|Comportamento previsto comune.|
|Eliminare una cartella con un file|1. Creare una singola soluzione di progetto.<br />2. Aggiungere una cartella.<br />3. Aggiungere un file alla cartella.<br />4. Aggiungere la soluzione al controllo del codice sorgente.<br />5. Estrarre il progetto per evitare richieste.<br />6. Eliminare la cartella.|Comportamento previsto comune.|
|Eliminare un progetto Web del file system|1. Creare un progetto Web del file system (usare il pulsante Sfoglia per specificare un percorso UNC).<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Rimuovere l'intero progetto dalla soluzione.<br />4. Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercita percorsi diversi tramite il codice, ma ha la stessa interfaccia esterna e lo stesso comportamento).|Comportamento previsto comune.|
|Eliminare un file da un progetto Web del file system|1. Creare un progetto Web del file system.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Eliminare un file dal progetto.<br />4. Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercita percorsi diversi tramite il codice, ma ha la stessa interfaccia esterna e lo stesso comportamento).|Comportamento previsto comune.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
