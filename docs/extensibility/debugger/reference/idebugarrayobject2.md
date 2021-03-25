---
description: Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (EE) di determinare l'indice di base (limiti inferiori) per la matrice.
title: IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 169f4df61bcd4a58e74e0d83cee362b3926d2b36
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067569"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (EE) di determinare l'indice di base (limiti inferiori) per la matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa operazione viene implementata dal motore di debug gestito (DE).

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) , questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera gli indici di base (limiti inferiori) per ogni indice dato il numero di dimensioni nella matrice.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina se la matrice ha indici di base (limiti inferiori) definiti.|

## <a name="remarks"></a>Commenti
 Un analizzatore di espressioni usa questa interfaccia per rappresentare le matrici gestite in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
