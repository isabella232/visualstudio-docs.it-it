---
title: Controllo dell'esecuzione e valutazione dello stato | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bda531e94bdea07ee37eed2b0b79e6f0667ba28e
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315242"
---
# <a name="execution-control-and-state-evaluation"></a>Valutazione di controllo e lo stato di esecuzione
Debug di un'applicazione richiede l'implementazione di tali funzionalità di controllo di esecuzione come l'esecuzione di funzioni, l'arresto nei punti di interruzione e continuare l'esecuzione. Debug di base di Visual Studio il controllo dell'esecuzione sugli eventi inviati tra i componenti del debugger.

## <a name="in-this-section"></a>Contenuto della sezione
 [Controllo del programma](../../extensibility/debugger/program-control.md) Elenca le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, l'esecuzione, l'esecuzione di istruzioni, continuare, la sospensione e ripresa.

 [I metodi correlati al punto di interruzione](../../extensibility/debugger/breakpoint-related-methods.md) definisce il limite e in attesa di tipi di punti di interruzione che supportano Visual Studio.

 [Valutazione dello stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md) illustra l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di interruzione.

 [Valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) spiega come il motore di debug (DE), la valutazione dell'espressione (EE) e gestione del debug sessione coinvolti nell'analisi e la valutazione dell'espressione immessa in una delle finestre dell'IDE.

 [Controllare gli eventi](../../extensibility/debugger/control-events.md) illustra l'interfaccia utilizzata per inviare gli eventi durante l'esecuzione del programma controllato.