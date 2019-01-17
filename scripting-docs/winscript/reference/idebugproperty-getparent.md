---
title: IDebugProperty::GetParent | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetParent
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetParent
ms.assetid: 673d625b-acca-45c4-88f4-b72275042f8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 34e4d38a4a04134535925d130b0660e52a0c0b19
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54344915"
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
Ottiene la proprietà padre di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetParent (  
   IDebugProperty** ppParent  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppParent`  
 [out] Restituisce il `IDebugProperty` interfaccia che rappresenta l'elemento padre della proprietà.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore valido `HRESULT`, in genere `S_OK`.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)