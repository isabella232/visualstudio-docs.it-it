---
title: Enumeratore directory Status Code | Microsoft Docs
description: L'enumeratore SccDirStatus contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo del codice sorgente e viene usato da SccDirQueryInfo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 81f7e81ded2b45b560350c065e13ef69455468d9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122159529"
---
# <a name="directory-status-code-enumerator"></a>Enumeratore del codice di stato della directory
`SccDirStatus`L'enumeratore contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo del codice sorgente. Questa enumerazione viene utilizzata da [SccDirQueryInfo.](../extensibility/sccdirqueryinfo-function.md) Questa funzionalità è stata introdotta nella versione 1.2 dell'API plug-in del controllo del codice sorgente.

## <a name="syntax"></a>Sintassi

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Members
 SCC_DIRSTATUS_INVALID impossibile ottenere lo stato. non si basano su di esso.

 SCC_DIRSTATUS_NOTCONTROLLED Directory non è sotto il controllo del codice sorgente.

 SCC_DIRSTATUS_CONTROLLED Directory è sotto il controllo del codice sorgente.

 SCC_DIRSTATUS_EMPTYPROJ Project corrispondente a questa directory è vuoto.

## <a name="see-also"></a>Vedi anche
- [Plug-in del controllo del codice sorgente](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
