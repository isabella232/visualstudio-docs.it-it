---
title: IDebugClassField::EnumBaseClasses | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugClassField::EnumBaseClasses
helpviewer_keywords:
- IDebugClassField::EnumBaseClasses method
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: acfdc872ba5f7cf1989ea1d9ec67f82f1c0419b0
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955588"
---
# <a name="idebugclassfieldenumbaseclasses"></a>IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Crea un enumeratore per le classi di base di questa classe.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```csharp  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppEnum`  
 [out] Restituisce un [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) oggetto che rappresenta l'elenco delle classi base. Restituisce un valore null se esistono classi base.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK, restituisce S_SH_NO_BASE_CLASSES se esistono classi base (e `ppEnum` parametro è impostato su un valore null); in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Le classi di base dell'oggetto enumeratore vengono specificate nell'ordine della classe base più immediata (o più derivata) alla classe di base più remota. Si consideri, ad esempio, le classi C++ seguente:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 L'enumerazione restituisce le classi di base nell'ordine `Level2`, `Level1`, `Root`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)
