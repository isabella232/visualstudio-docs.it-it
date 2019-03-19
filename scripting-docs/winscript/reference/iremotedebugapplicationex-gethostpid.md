---
title: IRemoteDebugApplicationEx:GetHostPid | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IRemoteDebugApplicationEx:GetHostPid
apilocation:
- scrobj.dll
helpviewer_keywords:
- IRemoteDebugApplicationEx:GetHostPid
ms.assetid: 4cf9f46c-29cf-4201-87f0-5b1ddbed2f2b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d660cce006e7f84f1b1c01f1ec0a406b5c4b9df3
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152159"
---
# <a name="iremotedebugapplicationexgethostpid"></a>IRemoteDebugApplicationEx:GetHostPid

Restituisce l'ID di processo per l'applicazione host.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetHostPid(
   DWORD*  dwHostPid
);
```

### <a name="parameters"></a>Parametri

`dwHostPid`

[out] L'identificatore di processo host.

## <a name="return-value"></a>Valore restituito

Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.

|Value|Descrizione|
|-----------|-----------------|
|`S_OK`|Il metodo è riuscito.|

## <a name="remarks"></a>Note

Usato dall'IDE.

## <a name="see-also"></a>Vedere anche

- [Interfaccia IRemoteDebugApplicationEx](iremotedebugapplicationex-interface.md)