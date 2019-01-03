---
title: IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IDebugProcessSecurity::QueryCanSafelyAttach
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9ecc1d7970fe8be98d199130db6e87847de3aee
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53839005"
---
# <a name="idebugprocesssecurityquerycansafelyattach"></a>IDebugProcessSecurity::QueryCanSafelyAttach
Questo metodo consente il fornitore della porta visualizzare un avviso prima che l'utente si connette a un processo non sicuro.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT QueryCanSafelyAttach();  
```  
  
```csharp  
int QueryCanSafelyAttach();  
```  
  
## <a name="return-value"></a>Valore restituito  
 I valori restituiti sono come segue:  
  
-   `S_OK`: La connessione al processo è sicura e non viene visualizzata alcuna finestra di dialogo di avviso.  
  
-   `S_FALSE`: La connessione potrebbe essere un problema di sicurezza e viene visualizzata una finestra di dialogo con un avviso.  
  
-   `FAILURE`: La connessione al processo avrà esito negativo.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)