---
title: Controllo dell'esecuzione e valutazione dello stato Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dc76ae97e8baa6ce78dd4d565109d6a19e2051e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738748"
---
# <a name="execution-control-and-state-evaluation"></a>Controllo dell'esecuzione e valutazione dello stato
Il debug di un'applicazione richiede l'implementazione di tali funzionalità di controllo dell'esecuzione, ad esempio l'esecuzione di istruzioni nelle funzioni, l'arresto in corrispondenza dei punti di interruzione e la continuazione dell'esecuzione. Il debug di Visual Studio basa il controllo dell'esecuzione sugli eventi inviati tra i componenti del debugger.

## <a name="in-this-section"></a>Contenuto della sezione
 [Controllo del programma](../../extensibility/debugger/program-control.md) Vengono elencate le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, esecuzione, esecuzione di istruzioni, continuazione, sospensione e ripresa.

 [Metodi correlati ai punti di interruzione](../../extensibility/debugger/breakpoint-related-methods.md) Definisce i tipi associati e in sospeso di punti di interruzione supportati da Visual Studio.

 [Valutazione dello stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md) Viene illustrata l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di interruzione.

 [Valutazione delle espressioni](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md) Viene illustrato come il motore di debug (DE), la valutazione delle espressioni (EE) e il gestore di debug della sessione sono coinvolti nell'analisi e nella valutazione di un'espressione immessa in una delle finestre dell'IDE.

 [Eventi di controllo](../../extensibility/debugger/control-events.md) Viene illustrata l'interfaccia utilizzata per inviare eventi durante l'esecuzione controllata del programma.
