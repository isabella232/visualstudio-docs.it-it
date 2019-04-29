---
title: IScriptEntry::GetRange | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetRange
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetRange
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7baa284be4fa7f45f247df7f4b3d140869f254b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62787737"
---
# <a name="iscriptentrygetrange"></a>IScriptEntry::GetRange
Restituisce la posizione iniziale e la lunghezza di una voce.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pichMin`  
 [out] Per `IScriptEntry` oggetti che specificano un blocco di script, restituisce 0.  
  
 Per `IScriptEntry` oggetti che specificano un oggetto funzione, restituisce la posizione di inizio della funzione nel blocco di script corrente.  
  
 Per `IScriptScriptlet` gli oggetti, restituisce 0.  
  
 `pcch`  
 [out] Per `IScriptEntry` oggetti che specificano un blocco di script, restituisce la lunghezza del testo.  
  
 Per `IScriptEntry` oggetti che specificano un oggetto funzione, restituisce la lunghezza della definizione di funzione.  
  
 Per `IScriptScriptlet` gli oggetti, restituisce la lunghezza della voce.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)