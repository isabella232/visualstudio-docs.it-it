---
title: Guida di test per i plug-in del controllo del codice sorgente Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- plug-ins, source control
- source control [Visual Studio SDK], testing plug-ins
- tests, source control plug-ins
- testing, source control plug-ins
- source control plug-ins, test guide
ms.assetid: 13b74765-0b7c-418e-8cd9-5f2e8db51ae5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6b3f8e76e977472a3459697a650b32dae657c22
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704381"
---
# <a name="test-guide-for-source-control-plug-ins"></a>Guida per il test dei plug-in del controllo del codice sorgente
In questa sezione vengono fornite indicazioni per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]testare il plug-in del controllo del codice sorgente con . Viene fornita una panoramica completa delle aree di test più comuni, nonché di alcune delle aree più complesse che possono essere problematiche. Questa panoramica non deve essere un elenco esaustivo di test case.

> [!NOTE]
> Alcune correzioni di bug e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] miglioramenti all'IDE più recente possono individuare i problemi con i plug-in del controllo del codice sorgente esistenti che non sono stati rilevati in precedenza durante l'utilizzo di versioni precedenti di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. È consigliabile testare il plug-in del controllo del codice sorgente esistente per le aree enumerate in questa sezione, anche se non sono state apportate modifiche al plug-in dalla versione precedente di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].

## <a name="common-preparation"></a>Preparazione comune
 È necessario [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] un computer in cui sia installato il plug-in del controllo del codice sorgente di destinazione. Un secondo computer configurato in modo simile può essere utilizzato per alcuni dei test Apri dal controllo del codice sorgente.

## <a name="definition-of-terms"></a>Definizione dei termini
 Ai fini di questa guida al test, utilizzare le seguenti definizioni di termini:

 Progetto client Qualsiasi tipo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di progetto disponibile in che [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]supporta [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)]l'integrazione del controllo del codice sorgente, ad esempio , o .

 Progetto Web Esistono quattro tipi di progetti Web: File System, IIS locale, Siti remoti e FTP.

- I progetti di file system vengono creati in un percorso locale, ma non richiedono l'installazione di Internet Information Services (IIS) in quanto vi si accede internamente tramite un percorso UNC e possono essere inseriti nel controllo del codice sorgente dall'interno dell'IDE, in modo analogo ai progetti client.

- I progetti IIS locali funzionano con IIS installato nello stesso computer e vi si accede con un URL che punta al computer locale.

- I progetti di siti remoti vengono creati anche in un servizio IIS, ma vengono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] inseriti nel controllo del codice sorgente nel computer server IIS e non dall'interno dell'IDE.

- I progetti FTP sono accessibili tramite un server FTP remoto, ma non possono essere inseriti nel controllo del codice sorgente.

  Enlistment Un altro termine per la soluzione o il progetto nel controllo del codice sorgente.

  Archivio versioni Il database del controllo del codice sorgente a cui si accede tramite l'API del plug-in del controllo del codice sorgente.

## <a name="test-areas-covered-in-this-section"></a>Aree di prova trattate in questa sezione

- [Area di test 1: Aggiungi a/Apri dal controllo del codice sorgente](../../extensibility/internals/test-area-1-add-to-open-from-source-control.md)

  - Caso 1a: aggiungere una soluzione al controllo del codice sorgenteCase 1a: Add Solution to Source Control

  - Caso 1b: Apri soluzione dal controllo del codice sorgenteCase 1b: Open Solution from Source Control

  - Caso 1c: aggiungere una soluzione dal controllo del codice sorgenteCase 1c: Add Solution from Source Control

- [Area di test 2: Recuperare elementi dal controllo del codice sorgente](../../extensibility/internals/test-area-2-get-from-source-control.md)

- [Area di test 3: Estrai/Annulla estrazione](../../extensibility/internals/test-area-3-check-out-undo-checkout.md)

  - Caso 3: Estrai/Annulla estrazione

  - Caso 3a: Check-Out

  - Caso 3b: estrazione disconnessa

  - Caso 3c: Modifica query/Salvataggio query (QEQS)

  - Caso 3d: Estrazione invisibile all'utente

  - Caso 3e: Annulla estrazione

- [Area di test 4: Archiviare](../../extensibility/internals/test-area-4-check-in.md)

  - Caso 4a: Elementi modificati

  - Caso 4b: Aggiunta di file

  - Caso 4c: Aggiunta di progetti

- [Area di test 5: Modificare il controllo del codice sorgente](../../extensibility/internals/test-area-5-change-source-control.md)

  - Caso 5a: Lega

  - Caso 5b: Disassociazione

  - Caso 5c: Riassociare

- [Area di test 6: Eliminare](../../extensibility/internals/test-area-6-delete.md)

- [Area di test 7: Condividere](../../extensibility/internals/test-area-7-share.md)

- [Area di test 8: Cambio di plug-in](../../extensibility/internals/test-area-8-plug-in-switching.md)

  - Caso 8a: Cambio automatico

  - Caso 8b: Modifica basata su soluzione

## <a name="see-also"></a>Vedere anche
- [Plug-in del controllo del codice sorgente](../../extensibility/source-control-plug-ins.md)
