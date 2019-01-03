---
title: Funzione SccGetVersion | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetVersion
helpviewer_keywords:
- SccGetVersion function
ms.assetid: a6e786bf-744e-4272-9e21-0be44d23b1a1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b997f3724dc3d1bb0f9155f3b575fef3ce9f2802
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53879627"
---
# <a name="sccgetversion-function"></a>Funzione SccGetVersion
Questa funzione Ottiene il numero di versione dell'API di plug-in controllo di origine supportate per il plug-in del controllo del codice sorgente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
LONG SccGetVersion(void);  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `LONG` tipo di dati che contiene il numero di versione dell'API di plug-in controllo di origine supportati:  
  
|WORD|Descrizione|  
|----------|-----------------|  
|HIWORD|Versione principale|  
|LOWORD|Versione secondaria|  
  
## <a name="remarks"></a>Note  
 Ad esempio, se un controllo del codice sorgente del plug-in supporta la versione 1.3 dell'API dei plug-in controllo di origine, questa funzione restituirà 0x0103.  
  
## <a name="see-also"></a>Vedere anche  
 [Funzioni API del plug-in del controllo del codice sorgente](../extensibility/source-control-plug-in-api-functions.md)