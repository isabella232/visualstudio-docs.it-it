---
title: IDebugPortSupplier3::CanPersistPorts | Microsoft Docs
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
- IDebugPortSupplier3::CanPersistPorts
helpviewer_keywords:
- IDebugPortSupplier3::CanPersistPorts
ms.assetid: 4127760c-e602-4e86-9232-457e382a52c7
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4f3799e4003edca0ce2722ad1365777f6be7e43c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528942"
---
# <a name="idebugportsupplier3canpersistports"></a>IDebugPortSupplier3::CanPersistPorts
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugPortSupplier3::CanPersistPorts](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugportsupplier3-canpersistports).  
  
Questo metodo determina se il fornitore della porta può mantenere le porte (mediante la scrittura su disco) tra le chiamate del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT CanPersistPorts();  
```  
  
```csharp  
int CanPersistPorts();  
```  
  
#### <a name="parameters"></a>Parametri  
 Nessuno.  
  
## <a name="return-value"></a>Valore restituito  
 `S_OK` Se le porte possono essere resi persistenti, o `S_FALSE` per indicare che le porte non possono essere persistente.  
  
## <a name="remarks"></a>Note  
 Se il fornitore della porta può rendere persistenti le porte, dovrebbe eseguire questa operazione quando viene eliminata e quindi ricaricarli quando ne viene creata un'istanza ancora una volta.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md)

