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
ms.openlocfilehash: e066da4c1c294669ad4baf4932c6d934e283a9c4914e9c23efc45ef3b1f2335d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121226102"
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
