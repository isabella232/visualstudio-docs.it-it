---
title: IDispatchEx::GetNameSpaceParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetNameSpaceParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetNameSpaceParent method
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1abe2a880e12d6a4a3c1dfda32d30722525858f5
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58154556"
---
# <a name="idispatchexgetnamespaceparent"></a>IDispatchEx::GetNameSpaceParent
Recupera l'interfaccia per l'elemento padre dello spazio dei nomi di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppunk`  
 Indirizzo di un `IUnknown` puntatore a interfaccia che riceve l'interfaccia dell'elemento padre dello spazio dei nomi.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce `S_OK` se ha esito positivo o un codice di errore definiti dall'OLE in caso contrario.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)