---
title: Guida di test per i plug-in del controllo del codice sorgente | Microsoft Docs
description: Informazioni sul test del plug-in del controllo del codice sorgente con Visual Studio. Questa panoramica include aree di test comuni.
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 66d2b57b97c60b9d485a3804d13d42925bd038942f4115e68ea046e27a7958c1
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121431799"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guida per il test dei plug-in del controllo del codice sorgente
In questa sezione vengono fornite indicazioni per testare il plug-in del controllo del codice sorgente con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Viene fornita una panoramica completa delle aree di test più comuni, nonché di alcune delle aree più complesse che possono essere problematiche. Questa panoramica non è destinata a essere un elenco completo di test case.

> [!NOTE]
> Alcune correzioni di bug e miglioramenti all'IDE più recente possono individuare problemi con i plug-in del controllo del codice sorgente esistenti che non sono stati rilevati in precedenza durante l'uso di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . È consigliabile testare il plug-in del controllo del codice sorgente esistente per le aree enumerate in questa sezione, anche se non sono state apportate modifiche al plug-in dalla versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="common-preparation"></a>Preparazione comune
 È necessario un computer con e il plug-in di controllo del codice [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sorgente di destinazione installato. Un secondo computer configurato in modo simile può essere usato per alcuni dei test Open from Source Control .

## <a name="definition-of-terms"></a>Definizione dei termini
 Ai fini di questa guida di test, usare le definizioni dei termini seguenti:

 Progetto client Qualsiasi tipo di progetto disponibile in che supporta l'integrazione del controllo del codice sorgente , ad [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esempio [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] , o [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

 Progetto Web Sono disponibili quattro tipi di progetti Web: File system, IIS locale, Siti remoti e FTP.

- I progetti del file system vengono creati in un percorso locale, ma non richiedono l'installazione di Internet Information Services (IIS) perché sono accessibili internamente tramite un percorso UNC e possono essere inseriti nel controllo del codice sorgente dall'interno dell'IDE, in modo simile ai progetti client.

- I progetti IIS locali funzionano con IIS installato nello stesso computer e a cui si accede con un URL che punta al computer locale.

- I progetti di Siti remoti vengono creati anche in servizi IIS, ma vengono inseriti nel controllo del codice sorgente nel computer server IIS e non all'interno [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] dell'IDE.

- I progetti FTP sono accessibili tramite un server FTP remoto, ma non possono essere inseriti nel controllo del codice sorgente.

  Integrazione Un altro termine per la soluzione o il progetto nel controllo del codice sorgente.

  Archivio versioni Database del controllo del codice sorgente a cui si accede tramite l'API plug-in del controllo del codice sorgente.

## <a name="test-areas-covered-in-this-section"></a>Aree di test trattate in questa sezione

- [Area di test 1: aggiungere o aprire elementi dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1a: Aggiungere una soluzione al controllo del codice sorgente

  - Caso 1b: Aprire la soluzione dal controllo del codice sorgente

  - Caso 1c: Aggiungere una soluzione dal controllo del codice sorgente

- [Area di test 2: Caricare dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Area di test 3: estrarre o annullare l'estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: Estrarre/annullare l'estrazione

  - Caso 3a: Check Out

  - Caso 3b: Checkout disconnesso

  - Caso 3c: Query Edit/Query Save (QEQS)

  - Caso 3d: estrazione invisibile all'utente

  - Caso 3e: Annullare l'estrazione

- [Area di test 4: Archiviare](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4a: Elementi modificati

  - Caso 4b: Aggiunta di file

  - Caso 4c: Aggiunta di progetti

- [Area di test 5: Modificare il controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5a: Associare

  - Caso 5b: Annullare l'associazione

  - Caso 5c: Riassociazione

- [Area di test 6: Eliminare](../../extensibility/internals/test-area-6-delete.md)

- [Area di test 7: Condividi](../../extensibility/internals/test-area-7-share.md)

- [Area di test 8: Cambio di plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8a: Modifica automatica

  - Caso 8b: Modifica basata su soluzioni

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)
