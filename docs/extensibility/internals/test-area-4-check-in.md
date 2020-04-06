---
title: 'Area di prova 4: Effettuare il check-in Documenti Microsoft'
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704579"
---
# <a name="test-area-4-check-in"></a>Area di test 4: Archiviare
Questa area di test del plug-in del controllo del codice sorgente riguarda l'invio di elementi aggiornati all'archivio versioni tramite il comando **Archivia.**

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case vengono utilizzati i percorsi di menu dell'ambiente di sviluppo integrato seguenti.

##### <a name="check-in"></a>Archivia:
 **File**, **Controllo del codice sorgente**, **Archivia**.

 **File**, **Archivia**.

 Menu di scelta rapida, **Archivia**.

## <a name="common-expected-behavior"></a>Comportamento previsto comuneCommon Expected Behavior

- I progetti e i file aggiunti a una soluzione o a un progetto nel controllo del codice sorgente vengono visualizzati nella finestra di dialogo **Archivia** e nella finestra **Archiviazioni in sospeso.**

- Dopo l'archiviazione, gli elementi aggiunti vengono visualizzati nel controllo del codice sorgente.

- Dopo l'archiviazione, gli elementi aggiornati vengono sottoposti a controllo delle versioni nell'archivio.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati i test case specifici per l'area di test Checkin.

### <a name="case-4a-modified-items"></a>Caso 4a: Elementi modificati
 Viene descritto l'utilizzo dell'azione di archiviazione per aggiornare un file nel controllo del codice sorgente che è stato modificato.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Modificare un file di testo che è stato estratto, archiviare solo il file (finestra di dialogo**Archivia)**|1. Creare un nuovo progetto con un file di testo.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre e modificare il file di testo.<br />4. Archiviare tramite la finestra di dialogo Archivia (**File**, **Controllo del codice sorgente**, **Archivia**).|Comportamento previsto comune.|
|Modificare un file di testo estratto, Archivia solo file (finestra**Archiviazioni in sospeso)**|1. Creare un nuovo progetto con un file di testo.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre e modificare il file di testo.<br />4. Effettuare il check-in tramite la finestra **Check-in in sospeso.**|Comportamento previsto comune.|

### <a name="case-4b-adding-files"></a>Caso 4b: Aggiunta di file
 Quando si aggiunge un file a un progetto o un elemento a una soluzione, è necessario modificare anche il progetto o la soluzione. Pertanto, il file padre viene estratto e deve essere archiviato per completare l'addizione.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere un file di testo e archiviare tutto (finestra di dialogo**Archivia)**|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un file di testo al progetto.<br />4. Se richiesto, accettare il check-out del progetto.<br />5. Selezionare la soluzione in **Esplora soluzioni**.<br />6. Effettuare il check-in dalla finestra di dialogo **Archivia.**|Comportamento previsto comune.|
|Aggiungere un file di testo e archiviare tutto (finestra**Archiviazioni in sospeso)**|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un file di testo al progetto.<br />4. Se richiesto, accettare il check-out del progetto.<br />5. Archiviare la soluzione dalla finestra **Archivia in sospeso.**|Comportamento previsto comuneCommon Expected Behavior|

### <a name="case-4c-adding-projects"></a>Caso 4c: Aggiunta di progetti
 Quando si aggiunge un progetto a una soluzione, è necessario modificare anche la soluzione. Pertanto, il file di soluzione viene estratto e deve essere archiviato per completare l'addizione.

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente (finestra di dialogo**Archivia)Add** a project to a blank solution under source control ( Check In dialog box)|1. Creare una soluzione vuota.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un nuovo progetto.<br />4. Se richiesto, accettare il check-out della soluzione.<br />5. Effettuare il check-in dalla finestra di dialogo **Archivia.**|Comportamento previsto comune.|
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente (finestra**Archiviini in sospeso)Add** a project to a blank solution under source control ( Pending Checkins window)|1. Creare una soluzione vuota.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un nuovo progetto.<br />4. Se richiesto, accettare il check-out della soluzione.<br />5. Archiviare la soluzione dalla finestra **Archivia in sospeso.**|Comportamento previsto comune.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
