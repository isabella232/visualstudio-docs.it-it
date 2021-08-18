---
title: 'Area di test 4: Archiviare | Microsoft Docs'
description: Questa area di test del plug-in del controllo del codice sorgente illustra l'invio di elementi aggiornati all'archivio versioni usando il comando Archivia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 8f3a90d2329b9b2c4beed6c5fee3b9284b655a1fd14d78e1b15ca988a617af6e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121336876"
---
# <a name="test-area-4-check-in"></a>Area di test 4: Archiviare
Questa area di test del plug-in di controllo del codice sorgente illustra l'invio di elementi aggiornati all'archivio versioni tramite **il comando Archivia.**

## <a name="command-menu-access"></a>Accesso al menu di comando
 Nei test case vengono usati i percorsi di menu dell'ambiente di sviluppo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrato seguenti.

##### <a name="check-in"></a>Archivia:
 **File**, **Controllo del codice sorgente**, **Archivia**.

 **File**, **Archivia**.

 Menu di scelta **rapida, Archivia**.

## <a name="common-expected-behavior"></a>Comportamento previsto comune

- I progetti e i file aggiunti a una  soluzione o a un progetto nel controllo del codice sorgente vengono visualizzati nella finestra di dialogo Archivia e nella **finestra Archivia in** sospeso.

- Dopo l'archiviazione, gli elementi aggiunti vengono visualizzati nel controllo del codice sorgente.

- Dopo l'archiviazione, gli elementi aggiornati vengono aggiornati correttamente nell'archivio.

## <a name="test-cases"></a>Test case
 Di seguito sono riportati test case specifici per l'area di test Checkin.

### <a name="case-4a-modified-items"></a>Caso 4a: Elementi modificati
 Descrive l'uso dell'azione di archiviazione per aggiornare un file nel controllo del codice sorgente modificato.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Modificare un file di testo estratto, archiviare solo il file **(finestra di dialogo** Archivia)|1. Creare un nuovo progetto con un file di testo.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre e modificare il file di testo.<br />4. Archiviare tramite la finestra di dialogo Archivia (**File**, **Controllo del codice sorgente**, **Archivia**).|Comportamento previsto comune.|
|Modificare un file di testo estratto, archiviare solo il file (finestra **Archivia in** sospeso)|1. Creare un nuovo progetto con un file di testo.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Estrarre e modificare il file di testo.<br />4. Eseguire l'archiviazione tramite la **finestra Checkins in** sospeso.|Comportamento previsto comune.|

### <a name="case-4b-adding-files"></a>Caso 4b: Aggiunta di file
 Quando si aggiunge un file a un progetto o a un elemento a una soluzione, è necessario modificare anche il progetto o la soluzione. Viene quindi estratto anche il file padre e deve essere archiviato per completare l'aggiunta.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere un file di testo e archiviare tutto **(finestra di dialogo** Archivia)|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un file di testo al progetto.<br />4. Accettare l'estrazione del progetto, se richiesto.<br />5. Selezionare la soluzione in **Esplora soluzioni**.<br />6. Archiviare nella finestra **di dialogo** Archivia.|Comportamento previsto comune.|
|Aggiungere un file di testo e archiviare tutti gli elementi **(finestra Archiviazioni in** sospeso)|1. Creare un nuovo progetto.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un file di testo al progetto.<br />4. Accettare l'estrazione del progetto, se richiesto.<br />5. Archiviare la soluzione **dalla finestra Archiviazioni in** sospeso.|Comportamento previsto comune|

### <a name="case-4c-adding-projects"></a>Caso 4c: Aggiunta di progetti
 Quando si aggiunge un progetto a una soluzione, anche la soluzione deve cambiare. Anche il file di soluzione viene estratto e deve essere archiviato per completare l'aggiunta.

|Azione|Passaggi di test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente **(finestra di dialogo** Archivia)|1. Creare una soluzione vuota.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un nuovo progetto.<br />4. Accettare l'estrazione della soluzione, se richiesto.<br />5. Archiviare nella **finestra di dialogo** Archivia.|Comportamento previsto comune.|
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente **(finestra Archiviazioni in** sospeso)|1. Creare una soluzione vuota.<br />2. Aggiungere la soluzione al controllo del codice sorgente.<br />3. Aggiungere un nuovo progetto.<br />4. Accettare l'estrazione della soluzione, se richiesto.<br />5. Archiviare la soluzione **dalla finestra Archiviazioni in** sospeso.|Comportamento previsto comune.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
