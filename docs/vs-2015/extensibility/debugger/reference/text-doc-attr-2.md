---
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 761c94673a5f5cec55ce0174561946f1d5302cb4
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58969237"
---
# <a name="textdocattr2"></a>TEXT_DOC_ATTR_2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Vengono descritti gli attributi di un documento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef DWORD TEXT_DOC_ATTR_2;  
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
```csharp  
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;  
```  
  
## <a name="members"></a>Membri  
 TEXT_DOC_ATTR_READONLY_2  
 Indica che il documento è di sola lettura.  
  
## <a name="remarks"></a>Note  
  
> [!NOTE]
>  Questo valore non viene effettivamente definito nell'assembly per il linguaggio C#. In alternativa, è necessario copiare la definizione per il file di origine.  
  
 Passato come argomento per il [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)
