---
description: Ottiene informazioni sulle app per Office che devono essere inserite automaticamente durante il debug.
title: Metodo GetAutoInsertExtensions
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
ms.openlocfilehash: 7bb7a75c4bc1abd5c5fb29c55a3be42e44ff2af55403c1d9ecccbf00efb5c755
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121268326"
---
# <a name="getautoinsertextensions-method"></a>Metodo GetAutoInsertExtensions
  Ottiene informazioni sulle app per Office che devono essere inserite automaticamente durante il debug.

 Questo metodo è riservato per utilizzi futuri.

## <a name="syntax"></a>Sintassi

```csharp
HRESULT GetAutoInsertExtensions(
    [out, retval] SAFEARRAY(BSTR)* psaExtensionNames
);
```

### <a name="parameters"></a>Parametri

|Parametro|Descrizione|
|---------------|-----------------|
|*psaExtensionNames*|I nomi delle estensioni delle app per Office.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Commenti
 Ogni app per Office da inserire viene restituita come Office di estensione dell'applicazione, che corrisponde a un valore in **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L'host deve cercare questi valori nel Registro di sistema e quindi inserire automaticamente le estensioni.
