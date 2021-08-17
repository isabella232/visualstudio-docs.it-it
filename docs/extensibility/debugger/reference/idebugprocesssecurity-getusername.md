---
description: Ottiene il nome utente dal fornitore della porta.
title: IDebugProcessSecurity::GetUserName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity::GetUserName
ms.assetid: c73c60ac-da6e-45ae-8f04-95353a24ca3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a376a8d51d7b4d974bf0c7b609bbc53cc334cb33
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122057577"
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
[out] Stringa contenente il nome utente.

## <a name="return-value"></a>Valore restituito
 Se il metodo ha esito positivo, viene restituito `S_OK`. In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 `GetUserName` restituisce il nome utente visualizzato nella colonna **Nome** utente della finestra **di dialogo** Collega a processo. Per visualizzare la **finestra di dialogo** Collega a processo , scegliere Collega **a** processo **dal** menu Strumenti nell'ambiente di sviluppo [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] integrato (IDE).

## <a name="see-also"></a>Vedi anche
- [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)
