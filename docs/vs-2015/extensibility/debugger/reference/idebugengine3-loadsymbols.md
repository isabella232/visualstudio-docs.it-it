---
title: IDebugEngine3::LoadSymbols | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine3::LoadSymbols
helpviewer_keywords:
- IDebugEngine3::LoadSymbols
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 29f8af5e258da923ec814e0a224dcf87cbbfae9e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964898"
---
# <a name="idebugengine3loadsymbols"></a>IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Simboli di caricamenti (in base alle esigenze) per tutti i moduli in fase di debug da questo motore di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```csharp  
int LoadSymbols();  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 Ciò consente di caricare simboli di debug per tutti i moduli di cui viene fatto riferimento da questo motore di debug. I simboli sono caricati solo se non siano già stati caricati. I simboli vengono cercati nei percorsi di set da una chiamata a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## <a name="see-also"></a>Vedere anche  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)
