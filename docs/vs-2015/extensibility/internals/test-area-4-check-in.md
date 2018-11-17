---
title: 'Area di test 4: Controllare | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], checking items in
- source control plug-ins, checking items in
ms.assetid: d0329fa8-7a8d-4d30-b67b-6f2a97b75a30
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 97a610325a5165a1de2cc50fede5bbabf182ef5e
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51783305"
---
# <a name="test-area-4-check-in"></a>Area di test 4: Archiviare
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Quest'area del plug-in test di controllo del codice sorgente illustra l'invio di elementi aggiornati nell'archivio versioni tramite il **Archivia** comando.  
  
## <a name="command-menu-access"></a>Accesso a comandi di Menu  
 Nell'esempio [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nei test case vengono usati percorsi di menu ambiente di sviluppo integrato.  
  
##### <a name="check-in"></a>Si collegano:  
 **File**, **controllo del codice sorgente**, **Archivia**.  
  
 **File**, **archiviare**.  
  
 Menu di scelta rapida **Archivia**.  
  
## <a name="common-expected-behavior"></a>Comportamento previsto comune  
  
-   Vengono visualizzati i progetti e i file aggiunti a una soluzione o progetto incluso nel controllo del codice sorgente nel **Archivia** finestra di dialogo e il **archiviazioni in sospeso** finestra.  
  
-   Dopo il check-in, gli elementi aggiunti vengono visualizzati nel controllo del codice sorgente.  
  
-   Dopo il check-in, gli elementi aggiornati sono versioni correttamente nell'archivio.  
  
## <a name="test-cases"></a>Test case  
 Di seguito sono specifici test case per l'area di test di archiviazione.  
  
### <a name="case-4a-modified-items"></a>Caso 4a: elementi modificati  
 Viene descritto l'utilizzo di controllo in azione per aggiornare un file di controllo del codice sorgente che è stato modificato.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Modificare un file di testo che è stato estratto, archiviare solo i file (**Archivia** nella finestra di dialogo)|1.  Creare un nuovo progetto con un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre e modificare il file di testo.<br />4.  Archiviare tramite la finestra di dialogo Archivia (**File**, **controllo del codice sorgente**, **Archivia**).|Comportamento previsto comune.|  
|Modificare un file di testo che è stato estratto, archiviare solo i file (**archiviazioni in sospeso** finestra)|1.  Creare un nuovo progetto con un file di testo.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Estrarre e modificare il file di testo.<br />4.  Archiviare tramite il **archiviazioni in sospeso** finestra.|Comportamento previsto comune.|  
  
### <a name="case-4b-adding-files"></a>Caso 4b: aggiunta di file  
 Quando si aggiunge un file a un progetto o un elemento a una soluzione, necessario modificare anche il progetto o soluzione. In questo modo il file padre è anche stato estratto e deve essere archiviato per completare l'aggiunta.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungere un file di testo e archivia i file (**Archivia** nella finestra di dialogo)|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file di testo al progetto.<br />4.  Se richiesto, accettare check-out del progetto.<br />5.  Selezionare la soluzione in **Esplora soluzioni**.<br />6.  Archivia dal **Archivia** nella finestra di dialogo.|Comportamento previsto comune.|  
|Aggiungere un file di testo e archivia i file (**archiviazioni in sospeso** finestra)|1.  Creare un nuovo progetto.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un file di testo al progetto.<br />4.  Se richiesto, accettare check-out del progetto.<br />5.  Controllare nella soluzione dal **archiviazioni in sospeso** finestra.|Comportamento previsto comune|  
  
### <a name="case-4c-adding-projects"></a>Caso c 4: aggiunta di progetti  
 Quando si aggiunge un progetto a una soluzione, necessario modificare anche la soluzione. In questo modo il file della soluzione è anche stato estratto e deve essere archiviato per completare l'aggiunta.  
  
|Operazione|Passi del test|Per verificare i risultati previsti|  
|------------|----------------|--------------------------------|  
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente (**Archivia** nella finestra di dialogo)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto.<br />4.  Se richiesto, accettare check-out della soluzione.<br />5.  Archivia dal **Archivia** nella finestra di dialogo.|Comportamento previsto comune.|  
|Aggiungere un progetto a una soluzione vuota nel controllo del codice sorgente (**archiviazioni in sospeso** finestra)|1.  Creare una soluzione vuota.<br />2.  Aggiungere la soluzione al controllo del codice sorgente.<br />3.  Aggiungere un nuovo progetto.<br />4.  Se richiesto, accettare check-out della soluzione.<br />5.  Controllare nella soluzione dal **archiviazioni in sospeso** finestra.|Comportamento previsto comune.|  
  
## <a name="see-also"></a>Vedere anche  
 [Guida per il test dei plug-in del controllo del codice sorgente](../../extensibility/internals/test-guide-for-source-control-plug-ins.md)

