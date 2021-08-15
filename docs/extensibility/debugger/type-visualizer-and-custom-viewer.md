---
title: Visualizzatore di tipi e visualizzatore personalizzato | Microsoft Docs
description: Informazioni sui componenti del visualizzatore di tipi e sui visualizzatori personalizzati, che visualizzano i dati in un formato specifico e sulle differenze tra di essi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 0a3e5e678edd5d616ea3ffc132dce0b8e28e3ef170242ba7c9611cb9f6920201
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121306023"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizzatore di tipi e visualizzatore personalizzato
Un visualizzatore di tipi è un componente che visualizza una parte di dati in un formato specifico. Il formato dipende interamente da chi implementa il visualizzatore, che si tratta dell'utente finale o di un fornitore di visualizzatori di terze parti.

 Un visualizzatore personalizzato è la parte di un analizzatore di espressioni personalizzato che visualizza una parte di dati in un formato specifico. Questo formato dipende interamente dall'implementatore del visualizzatore personalizzato, il che significa che il formato dipende dall'implementatore dell'analizzatore di espressioni (edizione Enterprise).

## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Supporto per i visualizzatori di tipi in un analizzatore di espressioni
 Un edizione Enterprise supporta i visualizzatori di tipi supportando un set di interfacce accessibili ai visualizzatori: interfacce come [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEEVisualizerDataProvider.](../../extensibility/debugger/reference/ieevisualizerdataprovider.md) Tuttavia, il edizione Enterprise non è responsabile dell'implementazione del visualizzatore di tipi stesso: il edizione Enterprise consente semplicemente ai visualizzatori esterni di accedere alle informazioni sul tipo. Tali visualizzatori possono essere spediti insieme al edizione Enterprise e installati nella posizione appropriata in Visual Studio, forniti da un altro fornitore di terze parti o anche dall'utente finale.

## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Supporto per i visualizzatori personalizzati in un analizzatore di espressioni
 Un edizione Enterprise può anche supportare visualizzatori personalizzati in cui il edizione Enterprise fornisce il codice per la visualizzazione del tipo di dati. Un visualizzatore personalizzato implementa [l'interfaccia IDebugCustomViewer,](../../extensibility/debugger/reference/idebugcustomviewer.md) che gestisce tutti i compiti di visualizzare i dati nel formato desiderato. il visualizzatore ha il controllo completo sulla visualizzazione e può anche consentire la modifica dei dati. Tutti i visualizzatori personalizzati forniti dal edizione Enterprise con il edizione Enterprise al momento della spedizione del prodotto.

## <a name="see-also"></a>Vedi anche
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
- [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)
- [Motore di debug](../../extensibility/debugger/debug-engine.md)
- [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)
- [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)
