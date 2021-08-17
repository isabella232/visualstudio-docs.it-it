---
title: WriteAllTLogs | Microsoft Docs
description: Informazioni su sintassi, requisiti e valore restituito per WriteAllTLogs, che scrive log di rilevamento per tutti i thread e contesti.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: db57baaa0a31b8882d7a2fe7a72c051dae748b59
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108135"
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

 HRESULT **con** il bit **SUCCEEDED** impostato se è stato creato il contesto di rilevamento.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [WriteContextTLogs](../msbuild/writecontexttlogs.md)