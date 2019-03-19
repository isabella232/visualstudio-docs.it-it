---
title: Interfaccia IDebugPropertyEnumType_All | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugPropertyEnumType_All
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugPropertyEnumType_All interface
ms.assetid: 4d0f4fd5-e5f7-47cb-b746-860d6363e2cd
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b9ddd9fb24aa83a6027d6d705de6a748a96b2e28
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149296"
---
# <a name="idebugpropertyenumtypeall-interface"></a>Interfaccia IDebugPropertyEnumType_All
Il `IDebugPropertyEnumType` interfacce sono definite in modo che ognuno di loro IID può essere passato come filtro per `IDebugProperty::EnumMembers` durante la richiesta l'enumeratore appropriato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
IDebugPropertyEnumType_All : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugPropertyEnumType_All::GetName](../../winscript/reference/idebugpropertyenumtype-all-getname.md)|Restituisce una stringa di testo che descrive il nome|  
  
 Le interfacce seguenti ereditano da `IDebugPropertyEnumType_All`, e non dispone di alcun metodi aggiuntivi.  
  
```cpp
IDebugPropertyEnumType_Arguments : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Locals : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_LocalsPlusArgs : IDebugPropertyEnumType_All   
IDebugPropertyEnumType_Registers : IDebugPropertyEnumType_All  
```  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)