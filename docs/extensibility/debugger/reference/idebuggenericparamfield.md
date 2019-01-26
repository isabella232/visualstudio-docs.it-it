---
title: IDebugGenericParamField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugGenericParamField interface
ms.assetid: ba24f499-5ba7-4c67-83e6-923229b52327
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e7cc68af4d5b53a36e9affc038951e2be63de90f
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954618"
---
# <a name="idebuggenericparamfield"></a>IDebugGenericParamField
Rappresenta un parametro per un tipo generico di codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugGenericParamField : IDebugField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Utilizzato per il supporto dei generics.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia, questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ConstraintCount](../../../extensibility/debugger/reference/idebuggenericparamfield-constraintcount.md)|Restituisce il numero di vincoli che sono associati a questo parametro generico.|  
|[GetConstraints](../../../extensibility/debugger/reference/idebuggenericparamfield-getconstraints.md)|Recupera i vincoli che sono associati a questo parametro generico.|  
|[GetFlags](../../../extensibility/debugger/reference/idebuggenericparamfield-getflags.md)|Recupera i flag per il parametro generico.|  
|[GetIndex](../../../extensibility/debugger/reference/idebuggenericparamfield-getindex.md)|Recupera l'indice del parametro generico.|  
|[GetNameOfFormalParam](../../../extensibility/debugger/reference/idebuggenericparamfield-getnameofformalparam.md)|Recupera il nome del parametro generico.|  
|[GetOwner](../../../extensibility/debugger/reference/idebuggenericparamfield-getowner.md)|Recupera il proprietario del tipo o metodo di questo parametro generico.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll