---
title: Guida per i Plug-in controllo codice sorgente di test | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40de16290e52755ab92d09edf0c90c045ad4dc86
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60061034"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guida per il test dei plug-in del controllo del codice sorgente
Questa sezione vengono fornite indicazioni per il test di controllo del codice sorgente del plug-in con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Viene fornita una panoramica completa di aree di test più comuni, nonché tra gli aspetti più complessi che possono causare problemi. Questa panoramica non intende essere un elenco completo dei test case.

> [!NOTE]
>  Alcune correzioni di bug e miglioramenti per la versione più recente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE possa rivelare problemi esistenti origine plug-in del controllo che sono stati precedentemente non rilevato durante l'utilizzo di versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È consigliabile testare il controllo del codice sorgente esistente del plug-in per le aree enumerate in questa sezione, anche se non sono state apportate modifiche per il plug-in rispetto alla versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Preparazione comune
 Un computer con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e controllo del codice sorgente di destinazione del plug-in installato, è necessario. Per alcune di apertura dal controllo del codice sorgente test, è possibile usare una seconda macchina configurata in modo analogo.

## <a name="definition-of-terms"></a>Definizione dei termini
 Ai fini di questa guida per i test, usare le definizioni dei termini seguenti:

 Client di progetto disponibili in qualsiasi tipo di progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che supporta l'integrazione del controllo codice sorgente (ad esempio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]).

 Progetto Web sono disponibili quattro tipi di progetti Web: File System, IIS locale, siti remoti e FTP.

- File System progetti vengono creati in un percorso locale, ma non richiedono Internet Information Services (IIS) per essere installato come si accede internamente tramite un percorso UNC e possono essere posti sotto il controllo del codice sorgente all'interno dell'IDE, molto simile a progetti client.

- Progetti IIS locali funzionano con IIS in cui è installato nello stesso computer e sono accessibili con un URL che punta al computer locale.

- I progetti di siti remoti vengono creati anche in un servizi di IIS, ma vengono inseriti nel controllo del codice sorgente nel computer server IIS e non da all'interno di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- I progetti FTP sono accessibili tramite un server FTP remoto ma non può essere inseriti nel controllo del codice sorgente.

  Controllare l'integrazione di un altro termine per la soluzione o progetto in origine.

  Versione Store, il database di controllo di origine a cui si accede tramite l'API dei plug-in del controllo origine.

## <a name="test-areas-covered-in-this-section"></a>Aree di test trattate in questa sezione

- [Area di test 1: Aggiungere a / Apri dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

    - Case 1a: Aggiungi soluzione al controllo del codice sorgente

    - Case 1b: Apri soluzione dal controllo del codice sorgente

    - Caso 1c: Aggiungi soluzione dal controllo del codice sorgente

- [Area di test 2: Ottenere dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Area di test 3: Check-Out / Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

    - Caso 3: Check-Out / Annulla estrazione

    - Case 3a: Estrai

    - Case 3b: Estrazione disconnessa

    - Caso 3C: Query Edit/Query Save (QEQS)

    - Caso 3d: Estrazione automatica

    - Case 3e: Annulla estrazione

- [Area di test 4: Check-In](../../extensibility/internals/test-area-4-check-in.md)

    - Case 4a: Elementi modificati

    - Case 4b: Aggiunta di file

    - Caso 4c: Aggiunta di progetti

- [Area di test 5: Modifica controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)

    - Case 5a: Eseguire l'associazione

    - Case 5b: annullamento del binding

    - Caso 5C: riassociazione

- [Area di test 6: Delete](../../extensibility/internals/test-area-6-delete.md)

- [Area di test 7: Condividi](../../extensibility/internals/test-area-7-share.md)

- [Area di test 8: Cambio di plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

    - Case 8a: Modifiche automatico

    - Case 8b: Modifica basati su soluzioni

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)