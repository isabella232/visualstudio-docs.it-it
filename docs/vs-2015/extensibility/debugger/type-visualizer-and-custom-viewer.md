---
title: Digitare visualizzatore e il visualizzatore personalizzato | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], custom viewer
- debugging [Debugging SDK], type visualizer
ms.assetid: fd3691e6-9c78-4767-846f-43f85ada4375
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5319721d57212f4fc853ca99c1544a51d4af878c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732128"
---
# <a name="type-visualizer-and-custom-viewer"></a>Visualizzatore di tipi e visualizzatore personalizzato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un visualizzatore di tipo è un componente che consente di visualizzare una porzione di dati in un formato molto specifico. Questo formato è interamente l'implementatore del visualizzatore, ovvero l'utente finale o un fornitore di terze parti di visualizzatori.  
  
 Un visualizzatore personalizzato è la parte di un analizzatore di espressioni personalizzato che consente di visualizzare una porzione di dati in un formato molto specifico. Questo formato è interamente l'implementatore del visualizzatore personalizzato, il che significa che il formato è lasciata all'implementatore dell'analizzatore di espressioni (EE).  
  
## <a name="support-for-type-visualizers-in-an-expression-evaluator"></a>Supporto per i visualizzatori di tipo in un analizzatore di espressioni  
 Un EE in grado di supportare i visualizzatori di tipo grazie al supporto di un set di interfacce accessibile per i visualizzatori: ad esempio le interfacce [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md) e [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md). Si noti tuttavia che l'analizzatore di Espressioni non è responsabile dell'implementazione del Visualizzatore di tipo stesso: l'analizzatore di Espressioni consente semplicemente visualizzatori esterni accedere a informazioni relative al tipo. Questi visualizzatori potrebbero essere forniti con l'analizzatore di Espressioni e installati nella posizione appropriata in Visual Studio, fornito da un altro fornitore di terze parti o anche da all'utente finale.  
  
## <a name="support-for-custom-viewers-in-an-expression-evaluator"></a>Supporto per i visualizzatori personalizzati disponibili in un analizzatore di espressioni  
 Un EE può anche supportare visualizzatori personalizzati in cui l'analizzatore di Espressioni fornisce il codice per la visualizzazione del tipo di dati. Un visualizzatore personalizzato implementa il [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md) si desidera ottenere l'interfaccia che gestisce tutti i compiti di mostrare i dati nel formato desiderato; il Visualizzatore abbia il pieno controllo sulla visualizzazione e può anche consentire il modifica dei dati. Eventuali visualizzatori personalizzati forniti dal motore di esecuzione includono l'analizzatore di Espressioni durante la distribuzione del prodotto.  
  
## <a name="see-also"></a>Vedere anche  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [IDebugCustomViewer](../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IEEVisualizerService](../../extensibility/debugger/reference/ieevisualizerservice.md)   
 [IEEVisualizerDataProvider](../../extensibility/debugger/reference/ieevisualizerdataprovider.md)

