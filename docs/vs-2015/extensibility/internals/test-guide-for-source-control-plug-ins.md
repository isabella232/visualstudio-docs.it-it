---
title: Guida per i Plug-in controllo codice sorgente di test | Microsoft Docs
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
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
caps.latest.revision: 27
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: eea089da8c8e0b7e626f58660a57cd499a93fb7c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778906"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guida per il test dei plug-in del controllo del codice sorgente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Questa sezione vengono fornite indicazioni per il test di controllo del codice sorgente del plug-in con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Viene fornita una panoramica completa di aree di test più comuni, nonché tra gli aspetti più complessi che possono causare problemi. Questa panoramica non intende essere un elenco completo dei test case.  
  
> [!NOTE]
>  Alcune correzioni di bug e miglioramenti per la versione più recente [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE possa rivelare problemi esistenti origine plug-in del controllo che sono stati precedentemente non rilevato durante l'utilizzo di versioni precedenti di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. È consigliabile testare il controllo del codice sorgente esistente del plug-in per le aree enumerate in questa sezione, anche se non sono state apportate modifiche per il plug-in rispetto alla versione precedente di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="common-preparation"></a>Preparazione comune  
 Un computer con [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e controllo del codice sorgente di destinazione del plug-in installato, è necessario. Per alcune di apertura dal controllo del codice sorgente test, è possibile usare una seconda macchina configurata in modo analogo.  
  
## <a name="definition-of-terms"></a>Definizione dei termini  
 Ai fini di questa guida per i test, usare le definizioni dei termini seguenti:  
  
 Progetto client  
 Qualsiasi tipo disponibile nel progetto [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] che supporta l'integrazione del controllo codice sorgente (ad esempio [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], o [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)]).  
  
 Progetto Web  
 Esistono quattro tipi di progetti Web: File System, IIS locale, siti remoti e FTP.  
  
- File System progetti vengono creati in un percorso locale, ma non richiedono Internet Information Services (IIS) per essere installato come si accede internamente tramite un percorso UNC e possono essere posti sotto il controllo del codice sorgente all'interno dell'IDE, molto simile a progetti client.  
  
- Progetti IIS locali funzionano con IIS in cui è installato nello stesso computer e sono accessibili con un URL che punta al computer locale.  
  
- I progetti di siti remoti vengono creati anche in un servizi di IIS, ma vengono inseriti nel controllo del codice sorgente nel computer server IIS e non da all'interno di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
- I progetti FTP sono accessibili tramite un server FTP remoto ma non può essere inseriti nel controllo del codice sorgente.  
  
  Integrazione di  
  Un altro termine per la soluzione o progetto incluso nel controllo del codice sorgente.  
  
  Versione Store  
  Il database di controllo di origine a cui si accede tramite l'API dei plug-in del controllo origine.  
  
## <a name="test-areas-covered-in-this-section"></a>Aree di test trattate in questa sezione  
  
-   [Area di test 1: Aggiungere o aprire elementi dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)  
  
    -   Caso 1a: Aggiungi soluzione al controllo del codice sorgente  
  
    -   Caso 1b: aprire soluzioni dal controllo del codice sorgente  
  
    -   Caso 1c: Aggiungi soluzione dal controllo del codice sorgente  
  
-   [Area di test 2: Recuperare elementi dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)  
  
-   [Area di test 3: Estrarre o annullare l'estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)  
  
    -   Caso 3: Estrarre / Annulla estrazione  
  
    -   Caso 3: estrarre  
  
    -   Caso 3b: disconnessa estrazione  
  
    -   Caso 3c: Query di modifica/Query salvare (QEQS)  
  
    -   Caso 3d: Estrazione invisibile all'utente  
  
    -   Caso 3e: Annulla estrazione  
  
-   [Area di test 4: Archiviare](../../extensibility/internals/test-area-4-check-in.md)  
  
    -   Caso 4a: elementi modificati  
  
    -   Caso 4b: aggiunta di file  
  
    -   Caso c 4: aggiunta di progetti  
  
-   [Area di test 5: Modificare il controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)  
  
    -   Caso 5a: eseguire l'associazione  
  
    -   Caso 5b: separazione  
  
    -   Caso 5C: Rebind  
  
-   [Area di test 6: Eliminare](../../extensibility/internals/test-area-6-delete.md)  
  
-   [Area di test 7: Condividere](../../extensibility/internals/test-area-7-share.md)  
  
-   [Area di test 8: Cambio di plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)  
  
    -   Caso 8a: modifiche automatico  
  
    -   Caso 8b: modifica basati su soluzioni  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)

