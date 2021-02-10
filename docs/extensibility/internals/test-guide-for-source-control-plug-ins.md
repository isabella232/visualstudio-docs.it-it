---
title: Guida ai test per i plug-in del controllo del codice sorgente | Microsoft Docs
description: Informazioni sul test del plug-in del controllo del codice sorgente con Visual Studio. Questa panoramica include le aree di test comuni.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 951b83f425f1e7171c519fced3fa3a4644279621
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934142"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guida per il test dei plug-in del controllo del codice sorgente
In questa sezione vengono fornite indicazioni per testare il plug-in del controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Viene fornita una panoramica completa delle aree di test più comuni, oltre ad alcune delle aree più complesse che potrebbero essere problematiche. Questa panoramica non è pensata per essere un elenco completo dei test case.

> [!NOTE]
> Alcune correzioni di bug e miglioramenti apportati all'IDE più recente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] possono individuare problemi con i plug-in del controllo del codice sorgente esistenti che non sono stati rilevati in precedenza durante l'utilizzo di versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Si consiglia vivamente di testare il plug-in del controllo del codice sorgente esistente per le aree enumerate in questa sezione, anche se non sono state apportate modifiche al plug-in dalla versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="common-preparation"></a>Preparazione comune
 È necessario un computer con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] e il plug-in del controllo del codice sorgente di destinazione. Un secondo computer configurato in modo analogo può essere usato per alcuni dei test aperti da quelli del controllo del codice sorgente.

## <a name="definition-of-terms"></a>Definizione dei termini
 Ai fini di questa guida di test, utilizzare le definizioni dei termini seguenti:

 Progetto client qualsiasi tipo di progetto disponibile in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] che supporta l'integrazione del controllo del codice sorgente (ad esempio,, [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] ).

 Progetto Web sono disponibili quattro tipi di progetti web: file System, IIS locale, siti remoti e FTP.

- I progetti di file System vengono creati in un percorso locale, ma non richiedono l'installazione del Internet Information Services (IIS) perché sono accessibili internamente tramite un percorso UNC e possono essere inseriti nel controllo del codice sorgente dall'interno dell'IDE, in modo analogo ai progetti client.

- I progetti IIS locali funzionano con IIS installato nello stesso computer e a cui si accede con un URL che punta al computer locale.

- I progetti di siti remoti vengono inoltre creati in un servizio IIS, ma vengono inseriti nel controllo del codice sorgente sul computer server IIS e non dall'interno dell' [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.

- I progetti FTP sono accessibili tramite un server FTP remoto, ma non possono essere inseriti nel controllo del codice sorgente.

  Integrazione di un altro termine per la soluzione o il progetto nel controllo del codice sorgente.

  Versione archivia il database del controllo del codice sorgente a cui si accede tramite l'API del plug-in del controllo del codice sorgente.

## <a name="test-areas-covered-in-this-section"></a>Aree di test descritte in questa sezione

- [Area di test 1: aggiungere o aprire elementi dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1a: aggiungere una soluzione al controllo del codice sorgente

  - Caso 1B: aprire una soluzione dal controllo del codice sorgente

  - Caso 1C: aggiungere una soluzione dal controllo del codice sorgente

- [Area di test 2: Caricare dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Area di test 3: estrarre o annullare l'estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: Estrai/Annulla estrazione

  - Caso 3A: estrazione

  - Caso 3B: estrazione disconnessa

  - Caso 3C: modifica query/Salva query (QEQS)

  - Caso 3D: estrazione invisibile all'utente

  - Caso 3e: Annulla estrazione

- [Area di test 4: Archiviare](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4a: elementi modificati

  - Caso 4B: aggiunta di file

  - Caso 4C: aggiunta di progetti

- [Area di test 5: Modificare il controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5a: binding

  - Caso 5b: annullamento dell'associazione

  - Caso 5C: riassociazione

- [Area di test 6: Eliminare](../../extensibility/internals/test-area-6-delete.md)

- [Area di test 7: Condividi](../../extensibility/internals/test-area-7-share.md)

- [Area di test 8: Cambio di plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8a: modifica automatica

  - Caso 8b: modifica basata sulla soluzione

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)
