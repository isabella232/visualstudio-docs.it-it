---
description: Ottiene il nome utente dal fornitore della porta.
title: 'IDebugProcessSecurity:: GetUserName | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 42a13075b233d5b0fe70b314a4b2d025a2a4c7d3
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105076303"
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

## <a name="remarks"></a>Commenti
 `GetUserName` Restituisce il nome utente visualizzato nella colonna **nome utente** della finestra di dialogo **Connetti a processo** . Per visualizzare la finestra di dialogo **Connetti a processo** , scegliere **Connetti a processo** dal menu **strumenti** nel [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] Integrated Development Environment (IDE).

## <a name="see-also"></a>Vedi anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
