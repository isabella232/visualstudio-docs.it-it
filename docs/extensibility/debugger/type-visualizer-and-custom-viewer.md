---
title: Visualizzatore di tipi e visualizzatore personalizzato | Microsoft Docs
description: Informazioni sui componenti del Visualizzatore di tipi e sui visualizzatori personalizzati, che visualizzano i dati in un formato specifico e le differenze tra di essi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 869f0997ee166b9b7eb29c1a313854437d670ee4
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057819"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizzatore di tipi e visualizzatore personalizzato
Un visualizzatore di tipi è un componente che visualizza una porzione di dati in un formato specifico. Il formato è interamente fino a chi implementa il visualizzatore, ovvero l'utente finale o un fornitore di visualizzatori di terze parti.

 Un visualizzatore personalizzato è la parte di un analizzatore di espressioni personalizzato che visualizza una parte di dati in un formato specifico. Questo formato è interamente all'implementatore del visualizzatore personalizzato, il che significa che il formato spetta all'implementatore dell'analizzatore di espressioni (EE).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Supporto per i visualizzatori di tipi in un analizzatore di espressioni
 Un EE supporta i visualizzatori di tipi grazie al supporto di un set di interfacce accessibili ai visualizzatori: interfacce quali [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Tuttavia, EE non è responsabile dell'implementazione del visualizzatore del tipo stesso: EE consente solo ai visualizzatori esterni di accedere alle informazioni sul tipo. Questi visualizzatori potrebbero essere spediti insieme ad EE e installati nel posto appropriato in Visual Studio, fornito da un altro fornitore di terze parti o anche dall'utente finale.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Supporto per i visualizzatori personalizzati in un analizzatore di espressioni
 Un EE può inoltre supportare i visualizzatori personalizzati nei quali EE fornisce il codice per la visualizzazione del tipo di dati. Un visualizzatore personalizzato implementa l'interfaccia [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) , che gestisce tutti i compiti di visualizzazione dei dati nel formato desiderato. il visualizzatore dispone del controllo completo sulla visualizzazione e può anche consentire la modifica dei dati. Tutti i visualizzatori personalizzati forniti da EE sono dotati di EE quando il prodotto viene spedito.

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
