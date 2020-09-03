---
title: 'Area di test 4: archivia | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2386a217de228c5c47b467e6e083d978702927f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704579"
---
# <a name="test-area-4-check-in"></a>Area di test 4: Archiviare
Questa area di test del plug-in del controllo del codice sorgente illustra l'invio di elementi aggiornati all'archivio delle versioni tramite il comando **Archivia** .

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Nei test case vengono utilizzati i percorsi dei menu Integrated Development Environment seguenti.

##### <a name="check-in"></a>Archivia:
 **File**, **controllo del codice sorgente**, **archiviazione**.

 **,** **Archiviare**.

 Menu di scelta rapida, **archiviare**.

## <a name="common-expected-behavior"></a>Comportamento previsto comune

- I progetti e i file aggiunti a una soluzione o a un progetto nel controllo del codice sorgente vengono visualizzati nella finestra di dialogo **Archivia** e nella finestra **archiviazioni in sospeso** .

- Dopo l'archiviazione, gli elementi aggiunti vengono visualizzati nel controllo del codice sorgente.

- Dopo l'archiviazione, gli elementi aggiornati vengono correttamente sottoposte a Versioning nell'archivio.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test di archiviazione.

### <a name="case-4a-modified-items"></a>Caso 4a: elementi modificati
 Viene descritto come usare l'azione Archivia per aggiornare un file nel controllo del codice sorgente che è stato modificato.

|Action|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Modificare un file di testo che è stato estratto, archiviare solo file (finestra**di dialogo Archivia** )|1. creare un nuovo progetto con un file di testo.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre e modificare il file di testo.<br />4. archiviare tramite la finestra di dialogo Archivia (**file**, **controllo del codice sorgente**, **Archivia**).|Comportamento previsto comune.|
|Modificare un file di testo che è stato estratto, archiviare solo file (finestra**archiviazioni in sospeso** )|1. creare un nuovo progetto con un file di testo.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre e modificare il file di testo.<br />4. archiviare tramite la finestra **archiviazioni in sospeso** .|Comportamento previsto comune.|

### <a name="case-4b-adding-files"></a>Caso 4B: aggiunta di file
 Quando si aggiunge un file a un progetto o a un elemento a una soluzione, il progetto o la soluzione deve essere modificata. Quindi, anche il file padre viene estratto e deve essere archiviato per completare l'aggiunta.

|Action|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere un file di testo e archiviare tutti gli elementi (finestra**di dialogo Archivia** )|1. creare un nuovo progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. aggiungere un file di testo al progetto.<br />4. se richiesto, accettare il controllo dal progetto.<br />5. Selezionare la soluzione in **Esplora soluzioni**.<br />6. archiviare nella finestra di dialogo **Archivia** .|Comportamento previsto comune.|
|Aggiungere un file di testo e archiviare tutti gli elementi (finestra**archiviazioni in sospeso** )|1. creare un nuovo progetto.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. aggiungere un file di testo al progetto.<br />4. se richiesto, accettare il controllo dal progetto.<br />5. archiviare la soluzione dalla finestra **archiviazioni in sospeso** .|Comportamento previsto comune|

### <a name="case-4c-adding-projects"></a>Caso 4C: aggiunta di progetti
 Quando si aggiunge un progetto a una soluzione, è necessario modificare anche la soluzione. Quindi, anche il file della soluzione viene estratto e deve essere archiviato per completare l'aggiunta.

|Action|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere un progetto a una soluzione vuota sotto controllo del codice sorgente (finestra**di dialogo Archivia** )|1. creare una soluzione vuota.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. aggiungere un nuovo progetto.<br />4. se richiesto, confermare l'estrazione della soluzione.<br />5. archiviare nella finestra di dialogo **Archivia** .|Comportamento previsto comune.|
|Aggiungere un progetto a una soluzione vuota sotto il controllo del codice sorgente (finestra**archiviazioni in sospeso** )|1. creare una soluzione vuota.<br />2. aggiungere la soluzione al controllo del codice sorgente.<br />3. aggiungere un nuovo progetto.<br />4. se richiesto, confermare l'estrazione della soluzione.<br />5. archiviare la soluzione dalla finestra **archiviazioni in sospeso** .|Comportamento previsto comune.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
