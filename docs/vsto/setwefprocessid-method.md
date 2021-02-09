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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 9c3d745f14185d46dce08d46b8c56391b108627d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882408"
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

## <a name="remarks"></a>Commenti
 Questo metodo deve essere chiamato dopo la creazione del processo di contenuto WEF, ma prima dell'esecuzione di qualsiasi contenuto di WEF.

 Se si vuole che l'ambiente di sviluppo alleghi un debugger al processo di contenuto WEF, l'ambiente deve eseguire questa operazione nell'implementazione di questo metodo.
