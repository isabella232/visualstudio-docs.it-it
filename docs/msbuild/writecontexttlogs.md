---
title: WriteContextTLogs | Microsoft Docs
description: Informazioni sulla sintassi, i requisiti e il valore restituito per WriteContextTLogs, che consente di scrivere i file di log per il contesto corrente.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 622cbebdb4073dfd9b4237e9dfbcb8bbf4a506de
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047382"
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

 **HRESULT** con il bit **succeeded** impostato se il contesto di rilevamento è stato creato.

## <a name="requirements"></a>Requisiti

 **Intestazione:** *FileTracker.h*

## <a name="see-also"></a>Vedi anche

- [WriteAllTLogs](../msbuild/writealltlogs.md)