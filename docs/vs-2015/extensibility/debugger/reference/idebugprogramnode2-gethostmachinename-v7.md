---
title: 'IDebugProgramNode2:: GetHostMachineName_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramNode2::GetHostMachineName
helpviewer_keywords:
- IDebugProgramNode2::GetHostMachineName_V7
- IDebugProgramNode2::GetHostMachineNameIDebugProgramNode2::GetHostMachineName
ms.assetid: a992f2c9-f68b-4146-8cc2-027753bf7ce6
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 63e4f1a3621dde3fba5e8a2dabf45eaceb5d8ea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839752"
---
# <a name="idebugprogramnode2gethostmachinename_v7"></a>IDebugProgramNode2::GetHostMachineName_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Deprecato. NON USARE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetHostMachineName_V7 (   
   BSTR* pbstrHostMachineName  
);  
```  
  
```csharp  
int GetHostMachineName_V7 (   
   out string pbstrHostMachineName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrHostMachineName`  
 out Restituisce il nome del computer in cui è in esecuzione il programma.  
  
## <a name="return-value"></a>Valore restituito  
 Un'implementazione deve sempre restituire `E_NOTIMPL` .  
  
## <a name="remarks"></a>Commenti  
  
> [!WARNING]
> A partire da [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] , questo metodo non viene più usato e deve sempre restituire `E_NOTIMPL` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
