---
title: Punti di interruzione (Visual Studio SDK) | Microsoft Docs
description: 'Informazioni sui tre tipi di punti di interruzione: pending, Bound ed Error. Questo articolo elenca le interfacce usate per implementare i tipi.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoints
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: fa9f244ec60e336e9a7596ff839842211d516b7d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99930811"
---
# <a name="breakpoints-visual-studio-sdk"></a>Punti di interruzione (Visual Studio SDK)
Sono disponibili tre tipi di punti di interruzione: pending, Bound ed Error.

 **Un punto di interruzione in sospeso:**

- È un'astrazione che contiene tutte le informazioni necessarie per associare un punto di interruzione a uno o più contesti di codice in uno o più programmi. Ogni volta che un programma di cui è in corso il debug provoca il caricamento del codice, il motore di debug controlla tutti i punti di interruzione in sospeso per verificare se è possibile eseguirne il binding.

   Un punto di interruzione in sospeso non viene mai associato al codice, ma piuttosto raccoglie e viene detto che contiene tutti i punti di interruzione associati generati.

- È rappresentato da un'interfaccia [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) .

  **Un punto di interruzione associato:**

- È un'astrazione per un punto di interruzione associato o associato a un singolo contesto di codice. Ogni punto di interruzione associato viene generato in risposta a un punto di interruzione in sospeso. Un punto di interruzione in sospeso può, tuttavia, generare più di un punto di interruzione associato.

   Quando il codice viene scaricato, un punto di interruzione associato può essere non associato ed eliminato.

- È rappresentato da un'interfaccia [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md) .

  **Un punto di interruzione dell'errore:**

- È un'astrazione per la descrizione di un errore durante il tentativo di associare un punto di interruzione in sospeso a un contesto di codice. Un punto di interruzione dell'errore descrive un errore nella posizione o nell'espressione del punto di interruzione. Per ulteriori informazioni, vedere [associazione](../../extensibility/debugger/binding-breakpoints.md)di punti di interruzione.

   L'errore del punto di interruzione può essere un errore o un avviso.

- È rappresentato da un'interfaccia [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md) .

## <a name="see-also"></a>Vedi anche
- [Programmi](../../extensibility/debugger/programs.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [Contesto del codice](../../extensibility/debugger/code-context.md)
- [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)
- [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)
