---
title: Metodo SetWefProcessId
description: Informazioni sul modo in cui il Metodo SetWefProcessId fornisce l'identificatore del processo che eseguirà il contenuto del framework Web Extensions (WEF).
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 523279d70215af90ea070ea8272a5221d9947582
ms.sourcegitcommit: 4bd2b770e60965fc0843fc25318a7e1b46137875
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/15/2020
ms.locfileid: "97524323"
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
