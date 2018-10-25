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
ms.openlocfilehash: f78d72bad8cb12b72f4b51e113d23dcd64ada8fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49838361"
---
# <a name="idebugpropertygetparent"></a>IDebugProperty::GetParent
Ottiene la proprietà padre di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```  
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