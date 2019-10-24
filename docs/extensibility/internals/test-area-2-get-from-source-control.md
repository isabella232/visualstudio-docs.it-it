---
title: 'Area di test 2: ottenere dal controllo del codice sorgente | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dca98c927209062d2a1fc67c309d2f32c18d1b5d
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722576"
---
# <a name="test-area-2-get-from-source-control"></a>Area di test 2: Recuperare elementi dal controllo del codice sorgente
Questa area di test include i test case per il recupero di elementi dall'archivio delle versioni tramite il comando Get. Questi test case possono essere applicati sia ai progetti locali che ai progetti Web.

## <a name="command-menu-access"></a>Accesso al menu dei comandi
 Nei test case vengono utilizzati i seguenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment i percorsi dei menu.

##### <a name="get-latest-version"></a>Ottenere la versione più recente:

- **File**, **controllo del codice sorgente**, **ottenere la versione più recente**.

- **File**, **ottenere la versione più recente**.

- Menu di scelta rapida, **ottenere la versione più recente**.

- Get: **file**, **controllo del codice sorgente**, **Get**.

## <a name="expected-behavior"></a>Comportamento previsto

##### <a name="get-latest-version"></a>Ottenere la versione più recente:
 Esegue un recupero invisibile all'utente della versione più recente dell'elemento dall'archivio delle versioni.

##### <a name="get"></a>Ottieni:
 Visualizza la finestra di dialogo Ottieni e consente all'utente di apportare modifiche al set di file che verrà recuperato, nonché di modificare le opzioni che influiscono sulla modalità di **recupero** dei file.

## <a name="test-cases"></a>Test case

|Operazione|Passi del test|Risultati previsti da verificare|
|------------|----------------|--------------------------------|
|Ottenere la versione più recente di un file che non esiste localmente|1. creare un progetto.<br />2. aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. eliminare la copia locale dell'elemento.<br />5. ottenere la versione più recente dell'elemento (menu di scelta rapida, **ottenere la versione più recente**).|Il file di elemento viene recuperato localmente.|
|Ottenere un file che non esiste localmente|1. creare un progetto.<br />2. aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. eliminare la copia locale dell'elemento.<br />5. ottenere l'elemento (**file**, **controllo del codice sorgente**, **Get** \<item >).|Il file di elemento viene recuperato localmente.|
|Ottenere un file che è stato estratto in modo esclusivo e modificato localmente|1. creare un progetto.<br />2. aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Estrarre l'elemento del progetto in modo esclusivo.<br />5. modificare la copia locale.<br />6. ottenere la versione più recente dell'elemento (**file**, **ottenere la versione più recente di** \<item >). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. fare clic sul pulsante **Sostituisci** nella finestra di dialogo di avviso.|**Risultato del passaggio 6** `:`<br /><br /> La finestra di dialogo di avviso indica che il file è stato estratto.<br /><br /> **Risultato del passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dall'archivio delle versioni.<br /><br /> Il file è di lettura/scrittura.|
|Ottenere e sostituire il file estratto, condiviso e modificato localmente|1. creare un nuovo progetto.<br />2. aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. Estrarre l'elemento del progetto come condiviso.<br />5. modificare la copia locale.<br />6. ottenere la versione più recente dell'elemento (**file**, **ottenere la versione più recente di** \<item >). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7. fare clic su **Sostituisci** nella finestra di dialogo di avviso.|**Risultato del passaggio 6:**<br /><br /> La finestra di dialogo di avviso indica che il file è stato estratto.<br /><br /> **Risultato del passaggio 7:**<br /><br /> Il file locale modificato viene sostituito dalla versione originale dall'archivio delle versioni.<br /><br /> Il file è di lettura/scrittura.|
|Ottenere un file esistente localmente, uguale alla versione più recente nell'archivio delle versioni|1. creare un nuovo progetto.<br />2. aggiungere un elemento al progetto.<br />3. Inserire il progetto nel controllo del codice sorgente.<br />4. ottenere l'elemento (**file**, **controllo del codice sorgente**, **Get** \<item >).|Il file locale è invariato.|
|Ottenere una soluzione con un progetto|1. creare una soluzione con un progetto.<br />2. Inserire la soluzione nel controllo del codice sorgente.<br />3. eliminare tutti i file di progetto in locale.<br />4. ottenere la soluzione (**file**, **controllo del codice sorgente**, **Get**).|Tutti i file eliminati vengono ripristinati localmente.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)