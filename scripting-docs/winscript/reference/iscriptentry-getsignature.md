---
title: IScriptEntry::GetSignature | Microsoft Docs
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
ms.openlocfilehash: 70cc1939ae4eb1e3c58d31b3d42b7f1b4603ce9e
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58145304"
---
# <a name="iscriptentrygetsignature"></a>IScriptEntry::GetSignature
Restituisce informazioni sul tipo per un `IScriptEntry` oggetto funzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppti`  
 [out] Digitare le informazioni associate a questo `IScriptEntry` oggetto funzione.  
  
 `piMethod`  
 [out] Indice di metodo nel `ITypeInfo` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Impostare le informazioni sul tipo utilizzando [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) oppure [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md). Informazioni sul tipo può essere generati anche tramite il movimento in base alla relativa rappresentazione in funzione interna.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)