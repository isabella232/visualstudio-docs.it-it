---
title: Punti di interruzione (Visual Studio SDK) | Microsoft Docs
description: 'Informazioni sui tre tipi di punti di interruzione: in sospeso, associato ed errore. Questo articolo elenca le interfacce usate per implementare i tipi.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 6aa20a2329416a16fb33776ad6b20db951b58da9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122073409"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punti di interruzione (Visual Studio SDK)
Esistono tre tipi di punti di interruzione: in sospeso, associato ed errore.

 **Un punto di interruzione in sospeso:**

- Astrazione che contiene tutte le informazioni necessarie per associare un punto di interruzione a uno o più contesti di codice in uno o più programmi. Ogni volta che un programma in fase di debug causa il caricamento del codice, il motore di debug controlla tutti i punti di interruzione in sospeso per verificare se possono essere associati.

   Un punto di interruzione in sospeso non viene mai associato al codice, ma raccoglie e viene detto che contiene tutti i punti di interruzione associati generati.

- È rappresentato da [un'interfaccia IDebugPendingBreakpoint2.](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

  **Punto di interruzione associato:**

- Astrazione per un punto di interruzione associato o associato a un singolo contesto del codice. Ogni punto di interruzione associato viene generato in risposta a un punto di interruzione in sospeso. Un punto di interruzione in sospeso può tuttavia generare più di un punto di interruzione associato.

   Quando il codice viene scaricato, un punto di interruzione associato può essere annullato e eliminato.

- È rappresentato da [un'interfaccia IDebugBoundBreakpoint2.](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)

  **Punto di interruzione dell'errore:**

- Astrazione per descrivere un errore durante il tentativo di associare un punto di interruzione in sospeso a un contesto del codice. Un punto di interruzione di errore descrive un errore nella posizione o nell'espressione del punto di interruzione stessa. Per altre informazioni, vedere [Associazione di punti di interruzione](../../extensibility/debugger/binding-breakpoints.md).

   L'errore del punto di interruzione può essere un errore o un avviso.

- È rappresentato da [un'interfaccia IDebugErrorBreakpoint2.](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)

## <a name="see-also"></a>Vedi anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
