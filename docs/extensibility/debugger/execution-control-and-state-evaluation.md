---
title: Controllo dell'esecuzione e valutazione dello stato | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8961d2e06c7013b5667191c190053047f82de77d
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39232403"
---
# <a name="execution-control-and-state-evaluation"></a>Valutazione di controllo e lo stato di esecuzione
Debug di un'applicazione richiede l'implementazione di tali funzionalità di controllo di esecuzione come l'esecuzione di funzioni, l'arresto nei punti di interruzione e continuare l'esecuzione. Debug di base di Visual Studio il controllo dell'esecuzione sugli eventi inviati tra i componenti del debugger.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Controllo del programma](../../extensibility/debugger/program-control.md)  
 Elenca le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, l'esecuzione, l'esecuzione di istruzioni, continuare, la sospensione e ripresa.  
  
 [Metodi correlati al punto di interruzione](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definisce il limite e in attesa di tipi di punti di interruzione che supportano Visual Studio.  
  
 [Valutazione dello stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md)  
 Illustra l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di interruzione.  
  
 [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Spiega come il motore di debug (DE), gestione espressione valutazione (EE) e sessione di debug sono coinvolti nell'analisi e valutazione di un'espressione immessi in una delle finestre dell'IDE.  
  
 [Eventi di controllo](../../extensibility/debugger/control-events.md)  
 Descrive l'interfaccia utilizzata per inviare gli eventi durante l'esecuzione del programma controllato.