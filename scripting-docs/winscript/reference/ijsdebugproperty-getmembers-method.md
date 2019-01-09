---
title: 'Metodo ijsdebugproperty:: GetMembers | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 351862f488aceb5fd3e9176cc4676e70b197d803
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54087027"
---
# <a name="ijsdebugpropertygetmembers-method"></a>Metodo IJsDebugProperty::GetMembers
Ottiene i membri di questo oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `members`  
 [in] Flag per specificare che cosa è incluso nelle informazioni del membro.  
  
 `ppEnum`  
 [out] I membri dell'oggetto.  
  
## <a name="return-value"></a>Valore restituito  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag.h  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IJsDebugProperty](../../winscript/reference/ijsdebugproperty-interface.md)