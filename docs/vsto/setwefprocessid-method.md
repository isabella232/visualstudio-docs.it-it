---
title: Metodo SetWefProcessId
description: Informazioni su come il metodo SetWefProcessId fornisce l'identificatore del processo che eseguirà il contenuto di Web Extensions Framework (WEF).
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 6d3fee5832c96de8fddec605399c9bd6ef565c2a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122032173"
---
# <a name="setwefprocessid-method"></a>Metodo SetWefProcessId
  Fornisce l'identificatore del processo che eseguirà il contenuto di Web Extensions Framework (WEF).

## <a name="syntax"></a>Sintassi

```csharp
HRESULT SetWefProcessId(
    [in] DWORD dwProcessId
);
```

#### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*dwProcessId*|Identificatore del processo che verrà usato per eseguire il contenuto WEF.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Commenti
 Questo metodo deve essere chiamato dopo la creazione del processo di contenuto WEF, ma prima dell'esecuzione di qualsiasi contenuto WEF.

 Se si vuole che l'ambiente di sviluppo allegare un debugger al processo del contenuto WEF, l'ambiente deve eseguire questa operazione nell'implementazione di questo metodo.
