---
title: Funzione SccCloseProject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccCloseProject
helpviewer_keywords:
- SccCloseProject function
ms.assetid: 259c2069-d349-4814-810f-1c3151b7fb84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5a5fe721a3b51f4d3f210e7f2d5450e4f4bc6f41
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66333927"
---
# <a name="scccloseproject-function"></a>Funzione SccCloseProject
Questa funzione consente di chiudere un progetto, contrassegna la fine di una determinata sessione.

## <a name="syntax"></a>Sintassi

```cpp
SCCRTN SccCloseProject (
   LPVOID pvContext
);
```

### <a name="parameters"></a>Parametri
 pvContext la struttura del contesto plug-in del controllo origine.

## <a name="return-value"></a>Valore restituito
 Implementazione di plug-in del controllo dell'origine di questa funzione deve restituire uno dei valori seguenti:

|Value|Descrizione|
|-----------|-----------------|
|SCC_OK|Il progetto è stato chiuso.|
|SCC_E_PROJNOTOPEN|Nessun progetto è aperto.|
|SCC_E_NOTAUTHORIZED|L'utente non è autorizzato a eseguire questa operazione.|
|SCC_E_NONSPECIFICERROR|Errore non specifico.|

## <a name="remarks"></a>Note
 Il [SccOpenProject](../extensibility/sccopenproject-function.md) viene sempre chiamato prima di questa funzione. Una chiamata a questa funzione viene quindi seguita da una chiamata a uno il `SccOpenProject` funzione o il [SccUninitialize](../extensibility/sccuninitialize-function.md), che termina la connessione al sistema di controllo di origine completamente.

## <a name="see-also"></a>Vedere anche
- [Funzioni API del plug-in origine controllo](../extensibility/source-control-plug-in-api-functions.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)