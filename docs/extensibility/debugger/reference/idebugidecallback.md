---
description: Consente a un analizzatore di espressioni (EE) di visualizzare un messaggio nella finestra di output del debugger.
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 461003f3bdb83e51e8b5c525895d134b717d8fc6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105091903"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

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
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Invia la stringa di messaggio specificata alla finestra di output del debugger.|

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
