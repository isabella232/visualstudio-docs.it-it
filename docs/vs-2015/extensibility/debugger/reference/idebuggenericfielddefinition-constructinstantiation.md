---
title: 'IDebugGenericFieldDefinition:: ConstructInstantiation | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- ConstructInstantiation
- IDebugGenericFieldDefinition::ConstructInstantiation
ms.assetid: ef8ae261-a98b-4dc2-93b3-7c5191818ba2
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 57a28cfd3b2ccd2ff37fae80d426817b664972fb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180905"
---
# <a name="idebuggenericfielddefinitionconstructinstantiation"></a>IDebugGenericFieldDefinition::ConstructInstantiation
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Costruisce un'istanza di campo in base a una matrice di argomenti di tipo.  
  
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
 in Numero di argomenti nella `ppArgs` matrice.  
  
 `ppArgs`  
 in Matrice che contiene gli argomenti di tipo. Gli argomenti di tipo devono essere tipi chiusi (generics non generici o con istanze complete).  
  
 `ppConstructedField`  
 out Restituisce l'interfaccia [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che rappresenta il nuovo campo.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 I vincoli non vengono controllati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugGenericFieldDefinition](../../../extensibility/debugger/reference/idebuggenericfielddefinition.md)
