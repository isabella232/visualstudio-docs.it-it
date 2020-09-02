---
title: 'IDebugCoreServer3:: EnableAutoAttach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCoreServer3::EnableAutoAttach
helpviewer_keywords:
- IDebugCoreServer3::EnableAutoAttach
ms.assetid: 06aa633b-263b-4e08-8844-9a52d5120b94
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 45362c9456b99d6cec0af01dcb29844d02363a27
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "62569793"
---
# <a name="idebugcoreserver3enableautoattach"></a>IDebugCoreServer3::EnableAutoAttach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Abilita il fissaggio automatico per i motori di debug specificati.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT EnableAutoAttach(  
   GUID*     rgguidSpecificEngines,  
   DWORD     celtSpecificEngines,  
   LPCOLESTR pszStartPageUrl,  
   BSTR*     pbstrSessionId  
);  
```  
  
```csharp  
int EnableAutoAttach(  
   Guid[]     rgguidSpecificEngines,  
   uint       celtSpecificEngines,  
   string     pszStartPageUrl,  
   out string pbstrSessionId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `rgguidSpecificEngines`  
 in Matrice di GUID per ogni motore di debug da contrassegnare come connessione automatica.  
  
 `celtSpecificEngines`  
 in Numero di motori specificati in `rgguidSpecificEngines` .  
  
 `pszStartPageUrl`  
 in URL iniziale da utilizzare per il fissaggio automatico.  
  
 `pbstrSessionID`  
 out ID della sessione collegata automaticamente.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice errore. Un codice di errore è `E_AUTO_ATTACH_NOT_REGISTERED` , che indica che il class factory di connessione automatica non è stato registrato.  
  
## <a name="remarks"></a>Osservazioni  
 Quando viene avviato un programma associato all'URL specificato, i motori di debug specificati vengono avviati automaticamente e collegati.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)
