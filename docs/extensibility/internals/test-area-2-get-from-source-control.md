---
title: 'Area di test 2: Ottenere dal controllo del codice sorgente | Microsoft Docs'
description: Questa area di test illustra i test case per il recupero di elementi dall'archivio versioni con Get. Questi test case possono essere applicati sia a progetti locali che a progetti Web.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: b7feb73cddacc15eeba1bd617f8beaa28a7e068d481290852c2d4e6c2b67801b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121336824"
---
# <a name="test-area-2-get-from-source-control"></a>Area di test 2: Caricare dal controllo del codice sorgente
Questa area di test illustra i test case per il recupero di elementi dall'archivio versioni tramite il comando Get. Questi test case possono essere applicati sia a progetti locali che a progetti Web.

## <a name="command-menu-access"></a>Accesso al menu di comando
 Nei test case vengono usati i percorsi di menu dell'ambiente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato seguenti.

##### <a name="get-latest-version"></a>Ottenere la versione più recente:

- **File**, **Controllo del codice sorgente**, **Ottenere la versione più recente**.

- **File**, **Ottenere la versione più recente**.

- Menu di scelta rapida, **Ottieni versione più recente.**

- Get: **File**, **Source Control**, **Get**.

## <a name="expected-behavior"></a>Comportamento previsto

##### <a name="get-latest-version"></a>Ottenere la versione più recente:
 Esegue un recupero automatico (senza interfaccia utente) dell'ultima versione dell'elemento dall'archivio versioni.

##### <a name="get"></a>Recupero:
 Visualizza la **finestra di** dialogo Recupera e consente all'utente di apportare modifiche al set di file che verrà recuperato, nonché di modificare le opzioni che influiscono sulla modalità di recupero dei file.

## <a name="test-cases"></a>Test case

|Azione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Ottenere la versione più recente di un file che NON esiste in locale|1. Creare un progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Eliminare la copia locale dell'elemento.<br />5. Ottenere la versione più recente dell'elemento (menu di scelta rapida, **Ottieni versione più recente).**|Il file dell'elemento viene recuperato in locale.|
|Ottenere un file che NON esiste in locale|1. Creare un progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Eliminare la copia locale dell'elemento.<br />5. Ottenere l'elemento (**File**, **Controllo del codice sorgente**, **Get** \<item> ).|Il file dell'elemento viene recuperato in locale.|
|Ottenere un file estratto esclusivamente e modificato in locale|1. Creare un progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Estrarre esclusivamente l'elemento di progetto.<br />5. Modificare la copia locale.<br />6. Ottenere la versione più recente dell'elemento (**File**, **Get Latest Version of** \<item> ). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. Fare clic **sul pulsante** Sostituisci nella finestra di dialogo di avviso.|**ReResult del passaggio 6**`:`<br /><br /> La finestra di dialogo Avviso indica che il file è estratto.<br /><br /> **ReResult del passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dell'archivio versioni.<br /><br /> Il file è di lettura/scrittura.|
|Ottenere e sostituire il file estratto, condiviso e modificato in locale|1. Creare un nuovo progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Estrarre l'elemento di progetto come condiviso.<br />5. Modificare la copia locale.<br />6. Ottenere la versione più recente dell'elemento (**File**, **Get Latest Version of** \<item> ). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. Fare clic **su Sostituisci** nella finestra di dialogo di avviso.|**Risultato del passaggio 6:**<br /><br /> La finestra di dialogo Avviso indica che il file è estratto.<br /><br /> **Risultato del passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dell'archivio versioni.<br /><br /> Il file è di lettura/scrittura.|
|Ottenere un file che esiste in locale, come la versione più recente nell'archivio versioni|1. Creare un nuovo progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Ottenere l'elemento (**File**, **Controllo del codice sorgente**, **Get** \<item> ).|Il file locale rimane invariato.|
|Ottenere una soluzione con un progetto|1. Creare una soluzione con un progetto.<br />2. Inserire la soluzione nel controllo del codice sorgente.<br />3. Eliminare tutti i file di progetto in locale.<br />4. Ottenere la soluzione (**File**, **Controllo del codice sorgente**, **Ottieni**).|Tutti i file eliminati vengono ripristinati in locale.|

## <a name="see-also"></a>Vedi anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
