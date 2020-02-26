---
title: WriteAllTLogs | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
apiname:
- WriteAllTLogs
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- WriteAllTLogs
ms.assetid: 1fa3e10b-263c-4960-a9ad-485c02a7a872
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7c64f0079a03b730fb700cfbc6320c5dffa05d7a
ms.sourcegitcommit: 2ae2436dc3484b9dfa10e0483afba1e5a02a52eb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/25/2020
ms.locfileid: "77579509"
---
# <a name="writealltlogs"></a>WriteAllTLogs
Scrive i log di rilevamento per tutti i thread e contesti.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT WINAPI WriteAllTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);
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
- [WriteContextTLogs](../msbuild/writecontexttlogs.md)