---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 217118d96fbcf50f267570bcd1c26abd5d8128c3
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520279"
---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugCoreServer2::GetMachineUtilities_V7](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugcoreserver2-getmachineutilities-v7).  
  
Questo metodo ottiene le utilità di computer per un server.  
  
> [!NOTE]
>  Questo metodo è obsoleto: non usare ([!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato). Questa viene conservata per motivi cronologici.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```csharp  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUtil`  
 [out] Restituisce un `IDebugMDMUtil2_V7` interfaccia che rappresenta le informazioni di utilità macchina.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`, che indica che il metodo non è implementato.  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)

