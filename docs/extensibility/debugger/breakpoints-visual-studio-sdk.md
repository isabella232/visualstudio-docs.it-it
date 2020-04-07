---
title: Punti di interruzione (Visual Studio SDK) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7c9d61c82886f237e8c9f544a59d8fe167548277
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739198"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punti di interruzione (Visual Studio SDK)
Esistono tre tipi di punti di interruzione: in sospeso, associato ed errore.

 **Un punto di interruzione in sospeso:A pending breakpoint:**

- È un'astrazione che contiene tutte le informazioni necessarie per associare un punto di interruzione a uno o più contesti di codice in uno o più programmi. Ogni volta che un programma in fase di debug causa il caricamento del codice, il motore di debug controlla tutti i punti di interruzione in sospeso per verificare se possono essere associati.

   Un punto di interruzione in sospeso non si associa mai al codice, ma raccoglie e si dice che contenga tutti i punti di interruzione associati che genera.

- È rappresentato da un [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) interfaccia.

  **Un punto di interruzione associato:A bound breakpoint:**

- È un'astrazione per un punto di interruzione associato o associato a un singolo contesto di codice. Ogni punto di interruzione associato viene generato in risposta a un punto di interruzione in sospeso. Un punto di interruzione in sospeso può, tuttavia, generare più di un punto di interruzione associato.

   Quando il codice viene scaricato, un punto di interruzione associato può essere non associato ed eliminato.

- È rappresentato da un [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) interfaccia.

  **Un punto di interruzione di errore:An error breakpoint:**

- È un'astrazione per la descrizione di un errore nel tentativo di associare un punto di interruzione in sospeso a un contesto di codice. Un punto di interruzione di errore descrive un errore nella posizione o nell'espressione del punto di interruzione stesso. Per ulteriori informazioni, vedere [Associazione di punti di interruzione](../../extensibility/debugger/binding-breakpoints.md).

   L'errore del punto di interruzione può essere un errore o un avviso.

- È rappresentato da un [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) interfaccia.

## <a name="see-also"></a>Vedere anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
