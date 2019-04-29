---
title: IDebugProgram2::WriteDump | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::WriteDump
helpviewer_keywords:
- IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: abafa1e3673a334105e8b8ec6e7957f631f000b2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62917292"
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Scrive un dump di un file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `DumpType`  
 [in] Un valore compreso il [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumerazione che specifica il tipo di dump, ad esempio, short o long.  
  
 `pszDumpUrl`  
 [in] URL di scrittura del dump. Si tratta in genere sotto forma di `file://c:\path\filename.ext`, ma può essere qualsiasi URL valido.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un dump del programma in genere includerà lo stack frame corrente, lo stesso stack, un elenco dei thread in esecuzione nel programma e possibilmente memoria che possiede il programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
