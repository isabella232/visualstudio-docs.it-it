---
title: Visualizzatore di tipo e visualizzatore personalizzato Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b8def9d28279f601ff488fca457982806629c0b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712459"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizzatore di tipo e visualizzatore personalizzato
Un visualizzatore di tipo è un componente che visualizza una parte di dati in un formato specifico. Il formato è interamente a che implementa il visualizzatore, sia esso l'utente finale o un fornitore di terze parti di visualizzatori.

 Un visualizzatore personalizzato è la parte di un analizzatore di espressioni personalizzato che visualizza una parte di dati in un formato specifico. Questo formato dipende interamente dall'implementatore del visualizzatore personalizzato, il che significa che il formato dipende dall'implementatore dell'analizzatore di espressioni (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Supporto per i visualizzatori di tipo in un analizzatore di espressioniSupport for type visualizers in an expression evaluator
 Un EE supporta i visualizzatori di tipo supportando un set di interfacce accessibili ai visualizzatori: interfacce quali [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Tuttavia, EE non è responsabile per l'implementazione del visualizzatore di tipo stesso: l'eE consente semplicemente visualizzatori esterni l'accesso alle informazioni sul tipo. Tali visualizzatori potrebbero essere spediti insieme a EE e installati nella posizione appropriata in Visual Studio, forniti da un altro fornitore di terze parti o anche dall'utente finale.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Supporto per visualizzatori personalizzati in un analizzatore di espressioniSupport for custom viewers in an expression evaluator
 Un EE può anche supportare visualizzatori personalizzati in cui l'EE stesso fornisce il codice per la visualizzazione del tipo di dati. Un visualizzatore personalizzato implementa il [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) interfaccia, che gestisce tutti i compiti di visualizzare i dati in qualsiasi formato desiderato; il visualizzatore ha il pieno controllo sul display e può anche lasciare che i dati vengano modificati. Tutti i visualizzatori personalizzati forniti dall'EE vengono forniti con l'EE quando il prodotto viene spedito.

## <a name="see-also"></a>Vedere anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Valutatore di espressioni](../../extensibility/debugger/expression-evaluator.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
