---
title: Proprietà IDebugArrayObject2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugArrayObject2 interface
ms.assetid: be6e504d-4ab3-4141-a61b-0953ee0e038e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a8a6580d0cbdead7866bbc6dd106a2aa0ea56f76
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736234"
---
# <a name="idebugarrayobject2"></a>IDebugArrayObject2
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Rappresenta un oggetto matrice gestita e consente a un analizzatore di espressioni (EE) di determinare l'indice di base (limiti inferiori) per la matrice.

## <a name="syntax"></a>Sintassi

```
IDebugArrayObject2 : IDebugArrayObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questo viene implementato dal motore di debug gestito (DE).

## <a name="methods"></a>Metodi
 Oltre ai metodi sul IDebugArrayObject interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md) interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[GetBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-getbaseindices.md)|Recupera gli indici di base (limiti inferiori) per ogni indice in base al numero di dimensioni nella matrice.|
|[HasBaseIndices](../../../extensibility/debugger/reference/idebugarrayobject2-hasbaseindices.md)|Determina se la matrice ha indici di base (limiti inferiori) definiti.|

## <a name="remarks"></a>Osservazioni
 Un analizzatore di espressioni utilizza questa interfaccia per rappresentare le matrici gestite in un albero di analisi.

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
