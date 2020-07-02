---
title: Metodo SetWefProcessId
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 13a6748e2e3b66f581a3c72c1f847e0329189e64
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85537332"
---
# <a name="setwefprocessid-method"></a>Metodo SetWefProcessId
  Fornisce l'identificatore del processo che eseguirà il contenuto del framework Web Extensions (WEF).

## <a name="syntax"></a>Sintassi

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*dwProcessId*|Identificatore del processo che verrà usato per eseguire il contenuto di WEF.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Osservazioni
 Questo metodo deve essere chiamato dopo la creazione del processo di contenuto WEF, ma prima dell'esecuzione di qualsiasi contenuto di WEF.

 Se si vuole che l'ambiente di sviluppo alleghi un debugger al processo di contenuto WEF, l'ambiente deve eseguire questa operazione nell'implementazione di questo metodo.
