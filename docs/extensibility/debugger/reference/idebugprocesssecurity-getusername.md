---
title: Proprietà IDebugProcessSecurity::NomeUtente.IDebugProcessSecurity::GetUserName . Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
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
[fuori] Stringa contenente il nome utente.

## <a name="return-value"></a>Valore restituito
 Se il metodo ha esito positivo, viene restituito `S_OK`. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni
 `GetUserName`restituisce il nome utente visualizzato nella colonna **Nome utente** della finestra di dialogo Connetti **a processo.** Per visualizzare la finestra di dialogo **Connetti a processo** , scegliere Connetti a **processo** dal menu **Strumenti** nell'ambiente [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] di sviluppo integrato (IDE).

## <a name="see-also"></a>Vedere anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
