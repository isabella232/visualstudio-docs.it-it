---
title: 'Area di test 2: Ottenere dal controllo del codice sorgente Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c213e2774730596db8b8e4f2d0691472495222e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704595"
---
# <a name="test-area-2-get-from-source-control"></a>Area di test 2: Recuperare elementi dal controllo del codice sorgente
In questa area di test vengono illustrati i test case per il recupero di elementi dall'archivio versioni tramite il comando Get. Questi test case possono essere applicati sia ai progetti Web locali che a progetti Web.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] test case vengono utilizzati i percorsi di menu dell'ambiente di sviluppo integrato seguenti.

##### <a name="get-latest-version"></a>Scarica l'ultima versione:

- **File**, **Controllo del codice sorgente**, Leggi ultima **versione**.

- **File**, **Leggi ultima versione**.

- Menu di scelta rapida, **Leggi ultima versione**.

- Ottieni: **File**, **Controllo del codice sorgente**, **Ottieni**.

## <a name="expected-behavior"></a>Comportamento previsto

##### <a name="get-latest-version"></a>Scarica l'ultima versione:
 Esegue un recupero invisibile all'utente (nessuna interfaccia utente) dell'ultima versione dell'elemento dall'archivio versioni.

##### <a name="get"></a>Recupero:
 Visualizza la finestra di dialogo **Ottieni** e consente all'utente di apportare modifiche al set di file che verrà recuperato, nonché modificare le opzioni che influiscono sulla modalità di recupero dei file.

## <a name="test-cases"></a>Test case

|Azione|Passaggi del testTest Steps|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Ottenere l'ultima versione di un file che NON esiste localmente|1. Creare un progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Eliminare la copia locale dell'elemento.<br />5. Ottenere l'ultima versione dell'elemento (Menu di scelta rapida, **Leggi ultima versione**).|Il file dell'elemento viene recuperato localmente.|
|Ottenere un file che NON esiste localmenteGet a file that does NOT exist locally|1. Creare un progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Eliminare la copia locale dell'elemento.<br />5. Ottenere l'elemento (**File**, **Controllo del codice sorgente**, **Ottieni** \<elemento>).|Il file dell'elemento viene recuperato localmente.|
|Ottenere un file estratto in modo esclusivo e modificato localmenteGet a file that has been out exclusively and modified locally|1. Creare un progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Estrarre l'elemento di progetto in modo esclusivo.<br />5. Modificare la copia locale.<br />6. Ottenere l'ultima versione dell'elemento (**File**, **Leggi ultima versione dell'elemento** \<>). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. Clic **Sostituire** pulsante nella finestra di dialogo di avviso.|**ReRisultato dal passaggio 6ReResult from Step 6**`:`<br /><br /> La finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **ReRisultato dal passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dell'archivio versioni.<br /><br /> Il file è di lettura/scrittura.|
|Ottenere e sostituire un file estratto, condiviso e modificato localmente|1. Creare un nuovo progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Estrarre l'elemento di progetto come condiviso.<br />5. Modificare la copia locale.<br />6. Ottenere l'ultima versione dell'elemento (**File**, **Leggi ultima versione dell'elemento** \<>). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. Fare clic su **Sostituisci** nella finestra di dialogo di avviso.|**Risultato del passaggio 6:**<br /><br /> La finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **Risultato del passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dell'archivio versioni.<br /><br /> Il file è di lettura/scrittura.|
|Ottenere un file che esiste localmente, come la versione più recente nell'archivio versioniGet a file that DOES exist locally, same as latest version in the version store|1. Creare un nuovo progetto.<br />2. Aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Ottenere l'elemento (**File**, **Controllo del codice sorgente**, **Ottieni** \<elemento>).|Il file locale non è stato modificato.|
|Ottieni una soluzione con un solo progetto|1. Creare una soluzione con un progetto.<br />2. Inserire la soluzione nel controllo del codice sorgente.<br />3. Eliminare tutti i file di progetto in locale.<br />4. Ottenere la soluzione (**File**, **Controllo del codice sorgente**, **Get**).|Tutti i file eliminati vengono ripristinati localmente.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)
