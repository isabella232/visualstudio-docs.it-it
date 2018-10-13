---
title: IDebugGenericFieldDefinition::ConstructInstantiation | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c5bb2ed0b869a400629123687451da61a9355daa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49283439"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Costruisce un'istanza del campo Data una matrice di argomenti di tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT ConstructInstantiation(  
   ULONG32       cArgs,  
   IDebugField** ppArgs,  
   IDebugField** ppConstructedField  
);  
```  
  
```csharp  
int ConstructInstantiation(  
   uint            cArgs,  
   IDebugField[]   ppArgs,  
   out IDebugField ppConstructedField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `cArgs`  
 [in] Numero di argomenti in di `ppArgs` matrice.  
  
 `ppArgs`  
 [in] Matrice che contiene gli argomenti di tipo. Gli argomenti di tipo devono essere tipi chiusi (non generico o istanziato completa di generics).  
  
 `ppConstructedField`  
 [out] Restituisce il [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia che rappresenta il nuovo campo.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 I vincoli non vengono controllati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)

