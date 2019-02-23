---
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58684cc5139d2797a08b74d9c0309252141e2498
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56723396"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Consente a un analizzatore di espressioni (EE) visualizzare un messaggio nella finestra di output del debugger.

## <a name="syntax"></a>Sintassi

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questo callback viene implementato dal motore di debug gestito.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Che può essere utilizzata da un analizzatore di espressioni per inviare l'output alla finestra di output del debugger.

## <a name="methods"></a>Metodi
 Questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Invia la stringa di messaggio specificato alla finestra di output del debugger.|

## <a name="requirements"></a>Requisiti
 Intestazione: EE.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll