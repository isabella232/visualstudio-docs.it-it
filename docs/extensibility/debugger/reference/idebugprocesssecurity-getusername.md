---
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ef00a0b7489c3e5cb709520546f3d3f26c8a4eba
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80723254"
---
# <a name="idebugprocesssecuritygetusername"></a>IDebugProcessSecurity::GetUserName
Ottiene il nome utente dal fornitore della porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetUserName(
    BSTR *pbstrUserName
);
```

```csharp
int GetUserName (
    string pbstrUserName
);
```

## <a name="parameters"></a>Parametri
`pbstrUserName`\
out Stringa che contiene il nome utente.

## <a name="return-value"></a>Valore restituito
 Se il metodo ha esito positivo, viene restituito `S_OK`. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 `GetUserName` Restituisce il nome utente visualizzato nella colonna **nome utente** della finestra di dialogo **Connetti a processo** . Per visualizzare la finestra di dialogo **Connetti a processo** , scegliere **Connetti a processo** dal menu **strumenti** nel [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE).

## <a name="see-also"></a>Vedere anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
