---
title: IRemoteDebugApplicationEx:ForceStepMode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:ForceStepMode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:ForceStepMode
ms.assetid: 83e69a3e-e4c9-4ddd-b01b-1820e4177a03
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3cb5c94c55709f5ecdbd6bae63ee3366f3dfeb2f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54790854"
---
# <a name="iremotedebugapplicationexforcestepmode"></a>IRemoteDebugApplicationEx:ForceStepMode

Forza il debugger in modalità di istruzione singola.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ForceStepMode(
   IRemoteDebugApplicationThread*  pStepThread
);
```

### <a name="parameters"></a>Parametri

`pStepThread`

[in] Thread per il monitoraggio di Debug del processo al passaggio. Se null, PDM Cancella il relativo avanzamento nell'esecuzione thread.

## <a name="return-value"></a>Valore restituito

Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.

|Value|Descrizione|
|-----------|-----------------|
|`S_OK`|Il metodo è riuscito.|

## <a name="see-also"></a>Vedere anche

- [Interfaccia IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)