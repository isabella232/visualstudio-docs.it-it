---
title: 'Area di test 2: Ottenere dal controllo del codice sorgente | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, getting items from source control
- source control [Visual Studio SDK], getting items from
ms.assetid: cbd345c5-ca43-4630-b7a4-85564f4e2090
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d7942aa658208143aea3c3ae3a09eb677568f17
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60067183"
---
# <a name="test-area-2-get-from-source-control"></a>Area di test 2: Caricare dal controllo del codice sorgente
Questa area di test riguarda casi di test per il recupero di elementi dall'archivio delle versioni tramite il comando Get. Questi test case possono essere applicati a locali e ai progetti Web.

## <a name="command-menu-access"></a>Accesso a comandi di Menu
 Nell'esempio [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] nei test case vengono usati percorsi di menu ambiente di sviluppo integrato.

##### <a name="get-latest-version"></a>Ottenere la versione più recente:

- **File**, **controllo del codice sorgente**, **Leggi ultima versione**.

- **File**, **Leggi ultima versione**.

- Menu di scelta rapida **Leggi ultima versione**.

- Ottieni: **File**, **controllo del codice sorgente**, **ottenere**.

## <a name="expected-behavior"></a>Comportamento previsto

##### <a name="get-latest-version"></a>Ottenere la versione più recente:
 Esegue un recupero automatico (senza interfaccia utente) della versione più recente dell'elemento dall'archivio delle versioni.

##### <a name="get"></a>Ottieni:
 Consente di visualizzare il **ottenere** nella finestra di dialogo e consente all'utente di apportare modifiche al set di file che verranno recuperate, nonché modificare le opzioni che influiscono sul modo in cui vengono recuperati i file.

## <a name="test-cases"></a>Test case

|Operazione|Passi del test|Per verificare i risultati previsti|
|------------|----------------|--------------------------------|
|Ottenere la versione più recente di un file che non esiste in locale|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Elimina la copia locale dell'elemento.<br />5.  Ottenere la versione più recente dell'elemento (Menu di scelta rapida **Leggi ultima versione**).|File di elemento viene recuperato in locale.|
|Ottenere un file che non esiste in locale|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Elimina la copia locale dell'elemento.<br />5.  Ottenere l'elemento (**File**, **controllo del codice sorgente**, **Ottieni** \<elemento >).|File di elemento viene recuperato in locale.|
|Ottenere un file che è stato estratto in modo esclusivo e modificato localmente|1.  Creare un progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Estrae l'elemento del progetto in modo esclusivo.<br />5.  Modificare la copia locale.<br />6.  Ottenere la versione più recente dell'elemento (**File**, **Leggi ultima versione del** \<elemento >). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7.  Fare clic su **sostituire** pulsante nella finestra di dialogo di avviso.|**ReResult dal passaggio 6** `:`<br /><br /> Finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **ReResult dal passaggio 7:**<br /><br /> Modifica file locale è sostituita dalla versione originale dall'archivio versioni.<br /><br /> File è di lettura/scrittura.|
|Ottenere e sostituire i file che è stato estratto, condiviso e modificato localmente|1.  Creare un nuovo progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Estrarre l'elemento del progetto come condiviso.<br />5.  Modificare la copia locale.<br />6.  Ottenere la versione più recente dell'elemento (**File**, **Leggi ultima versione del** \<elemento >). Se questo passaggio ha esito positivo, continuare con il passaggio successivo.<br />7.  Fare clic su **sostituire** nella finestra di dialogo di avviso.|**Risultato del passaggio 6:**<br /><br /> Finestra di dialogo di avviso indica che il file è estratto.<br /><br /> **Risultato del passaggio 7:**<br /><br /> Modifica file locale è sostituita dalla versione originale dall'archivio versioni.<br /><br /> File è di lettura/scrittura.|
|Ottenere un file che esistono in locale, identica a quella più recente nell'archivio delle versioni|1.  Creare un nuovo progetto.<br />2.  Aggiungere un elemento al progetto.<br />3.  Inserire il progetto nel controllo del codice sorgente.<br />4.  Ottenere l'elemento (**File**, **controllo del codice sorgente**, **Ottieni** \<elemento >).|File locale è invariato.|
|Ottenere una soluzione con un unico progetto|1.  Creare una soluzione con un unico progetto.<br />2.  Inserire la soluzione nel controllo del codice sorgente.<br />3.  Eliminare tutti i file di progetto in locale.<br />4.  Ottenere la soluzione (**File**, **controllo del codice sorgente**, **Ottieni**).|Tutti i file eliminati vengono ripristinati in locale.|

## <a name="see-also"></a>Vedere anche
- [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)