---
title: IDebugPointerField | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c22d2570311885a3717190c871f0cca2d90756b
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58965674"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia rappresenta un tipo di puntatore.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugPointerField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Il provider di simboli implementa questa interfaccia per rappresentare un puntatore.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Uso [QueryInterface](http://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) per ottenere questa interfaccia dalle [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_POINTER`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel `IDebugField` e `IDebugContainerField` interfacce, questa interfaccia implementa il metodo seguente:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive la destinazione dell'indicatore di misura.|  
  
## <a name="remarks"></a>Note  
 In C/C++, un puntatore può essere un contenitore, se viene usato con la notazione di matrice. Ad esempio, dato `char *pString`, `pString` dispone di un tipo di puntatore a `char`. `pString[3]` ha il tipo di un contenitore che è un puntatore a `char` che fa riferimento il quarto elemento di tale contenitore.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
