---
description: Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (edizione Enterprise) di determinare l'indice di base (limiti inferiori) per la matrice.
title: Interfaccia IDebugArrayObject2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8f7509b56b577e17c3522191c1c16c3ba84f2419cda7763c0dcc8dbbd9d4ec1f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121323833"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (edizione Enterprise) di determinare l'indice di base (limiti inferiori) per la matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa funzionalità viene implementata dal motore di debug gestito.

## <a name="methods"></a>Metodi
 Oltre ai metodi [nell'interfaccia IDebugArrayObject,](../../../extensibility/debugger/reference/idebugarrayobject.md) questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera gli indici di base (limiti inferiori) per ogni indice in base al numero di dimensioni nella matrice.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina se per la matrice sono definiti indici di base (limiti inferiori).|

## <a name="remarks"></a>Commenti
 Un analizzatore di espressioni usa questa interfaccia per rappresentare matrici gestite in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
