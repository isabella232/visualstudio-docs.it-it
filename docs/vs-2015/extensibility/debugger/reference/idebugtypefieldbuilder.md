---
title: IDebugTypeFieldBuilder | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder interface
ms.assetid: 2dfed0be-6972-4bec-baec-f0b78df9ef97
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84a4da6bcd306e409582077f66fab1a40b7d7942
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68199709"
---
# <a name="idebugtypefieldbuilder"></a>IDebugTypeFieldBuilder
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Rappresenta la possibilità di creare un campo che rappresenta un tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugTypeFieldBuilder : IUnknown  
```  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Questa interfaccia viene ottenuta dal provider di simboli.  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreatePrimitive](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createprimitive.md)|Crea un oggetto che rappresenta un tipo primitivo.|  
|[CreatePointerToType](../../../extensibility/debugger/reference/idebugtypefieldbuilder-createpointertotype.md)|Crea un puntatore al tipo specificato.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh. h  
  
 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
