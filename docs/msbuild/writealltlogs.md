---
title: WriteAllTLogs | Microsoft Docs
description: Informazioni sulla sintassi, i requisiti e il valore restituito per WriteAllTLogs, che scrive i log di rilevamento per tutti i thread e i contesti.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 754b34b872ba0f0f677a194194b2ff893e7107e1
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047483"
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

 **HRESULT** con il bit **succeeded** impostato se il contesto di rilevamento è stato creato.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)