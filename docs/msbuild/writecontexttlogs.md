---
title: WriteContextTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteContextTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5c0793cc6d9f11cd1074c5cd0091687b154c069
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579466"
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Scrive i file di log per il contesto corrente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
```

#### <a name="parameters"></a>Parametri
[in] `intermediateDirectory`

 Directory in cui archiviare il log di rilevamento.

[in] `tlogRootName`

 Nome radice del nome file di log.

## <a name="return-value"></a>Valore restituito
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato creato.

## <a name="requirements"></a>Requisiti
 **Intestazione:** *FileTracker. h*

## <a name="see-also"></a>Vedere anche
- [WriteAllTLogs](../msbuild/writealltlogs.md)