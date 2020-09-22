---
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 131f5a5f276b3f93d2ede3d088556b6832cc3651
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840155"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo ottiene le utilità del computer per un server.  
  
> [!NOTE]
> Questo metodo è obsoleto: non usare ( [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato). Viene mantenuto per motivi cronologici.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUtil`  
 out Restituisce un' `IDebugMDMUtil2_V7` interfaccia che rappresenta le informazioni sulle utilità del computer.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL` , che indica che il metodo non è implementato.  
  
## <a name="remarks"></a>Commenti  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
