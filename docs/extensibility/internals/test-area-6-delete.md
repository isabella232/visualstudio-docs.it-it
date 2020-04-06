---
title: 'Area di prova 6: Elimina Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], deleting items
- source control plug-ins, deleting items
ms.assetid: 6f2e872c-5ba2-4303-9f50-a90cef9a6225
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9902ab9d1cb9c28ddf67b83590a4cccd5f6562f2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704506"
---
# <a name="test-area-6-delete"></a>Area di test 6: Eliminare
Questa area di test del plug-in del controllo del codice sorgente riguarda le azioni di eliminazione.

 Il controllo del codice sorgente risponde alle azioni di eliminazione in **Esplora soluzioni**.

 Di seguito è riportato un elenco di elementi che possono essere eliminati:

- File

- Cartelle

- Project

  A seconda del tipo di progetto, è possibile scegliere **Rimuovi** il progetto (lascia i file su disco) o **Eliminare** il progetto (rimuove i file su disco). L'azione rimuove il progetto o l'elemento da **Esplora soluzioni**.

## <a name="expected-behavior"></a>Comportamento previsto
 Il comportamento previsto per i test case nell'area di test di eliminazione è:The expected behavior for the test case in the delete test area is:

- L'elemento eliminato non è più visibile in **Esplora soluzioni.**

- L'elemento padre del progetto o dell'elemento eliminato viene estratto in base alle esigenze (eventualmente con un prompt).

- Dopo aver eliminato un elemento estratto o aggiunto, NON viene visualizzato nella finestra **Archiviazioni in sospeso.**

- L'elemento esiste ancora all'interno dell'archivio del controllo del codice sorgente, anche dopo l'eliminazione, e deve essere eliminato manualmente.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Eliminare un progetto clientDelete a client project|1. Creare un progetto client.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Rimuovere l'intero progetto dalla soluzione|Comportamento previsto comune.|
|Eliminare un file vuoto|1. Creare un progetto client.<br />2. Aggiungere un file di zero byte al progetto.<br />3. Aggiungere la soluzione al controllo del codice sorgente.<br />4. Selezionare il file, eliminarlo.|Comportamento previsto comune.|
|Eliminare una cartella con un file|1. Creare una singola soluzione di progetto.<br />2. Aggiungere una cartella.<br />3. Aggiungere un file alla cartella.<br />4. Aggiungere la soluzione al controllo del codice sorgente.<br />5. Controllare il progetto per evitare richieste.<br />6. Eliminare la cartella.|Comportamento previsto comune.|
|Eliminare un progetto Web file system|1. Creare un progetto Web file system (utilizzare il pulsante Sfoglia per specificare un percorso UNC).<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Rimuovere l'intero progetto dalla soluzione.<br />4. Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercizi osseperi diversi attraverso il codice ma ha la stessa interfaccia esterna e lo stesso comportamento).|Comportamento previsto comune.|
|Eliminare un file da un progetto Web file system|1. Creare un progetto Web file system.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Eliminare un file dal progetto.<br />4. Ripetere i passaggi da 1 a 3 per un progetto Web locale (esercizi osseperi diversi attraverso il codice ma ha la stessa interfaccia esterna e lo stesso comportamento).|Comportamento previsto comune.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
