---
title: 'IScriptEntry:: GetSignature | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptEntry.GetSignature
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptEntry::GetSignature
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7b07ac64ce7e427a793f0af0db9a7905441d39b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575425"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Restituisce informazioni sul tipo per un oggetto `IScriptEntry` funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppti`  
 out Informazioni sul tipo associate a questo oggetto `IScriptEntry` funzione.  
  
 `piMethod`  
 out Indice del metodo nell'oggetto `ITypeInfo`.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Per impostare le informazioni sul tipo, utilizzare [IScriptEntry:: sesignature](../../winscript/reference/iscriptentry-setsignature.md) o [IScriptNode:: CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Le informazioni sul tipo possono anche essere generate dalla voce basata sulla rappresentazione della funzione interna.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)