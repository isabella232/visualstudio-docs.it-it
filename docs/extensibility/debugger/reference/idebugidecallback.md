---
title: Proprietà IDebugIDECallback . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727835"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Consente a un analizzatore di espressioni (EE) di visualizzare un messaggio nella finestra di output del debugger.

## <a name="syntax"></a>Sintassi

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questo callback viene implementato dal motore di debug gestito.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Può essere utilizzato da un analizzatore di espressioni per inviare l'output alla finestra di output del debugger.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa il metodo seguente:This interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[Messaggio visualizzato](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Invia la stringa di messaggio specificata alla finestra di output del debugger.|

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
