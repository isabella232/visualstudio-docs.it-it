---
title: IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs
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
- IDebugProcess3::SetHostingProcessLanguage
helpviewer_keywords:
- IDebugProcess3::SetHostingProcessLanguage
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1f9b849f2da8c834a807286d251cafab8a4c4c27
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47540567"
---
# <a name="idebugprocess3sethostingprocesslanguage"></a>IDebugProcess3::SetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugProcess3::SetHostingProcessLanguage](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage).  
  
Questo metodo imposta la lingua che verrà ospitato il processo sotto. Questo linguaggio è quindi utilizzabile per caricare l'analizzatore di espressioni appropriato dal motore di debug (DE).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetHostingProcessLanguage(  
   REFGUID guidLang  
);  
```  
  
```csharp  
int SetHostingProcessLanguage(  
   ref Guid guidLang  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidLang`  
 [in] `GUID` del linguaggio che deve usare la Germania. Specificare `GUID_NULL` (C++) o `Guid.Empty` (c#) per disporre il DE utilizzare la lingua predefinita.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) può essere utilizzato per recuperare l'impostazione della lingua corrente.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)
