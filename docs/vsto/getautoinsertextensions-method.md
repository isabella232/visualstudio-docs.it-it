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
ms.workload:
- office
ms.openlocfilehash: c4a49942f50a79db604d2363cf2d85762c5ddce5
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102223433"
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
|*psaExtensionNames*|Nomi di estensione delle app per Office.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Commenti
 Ogni app per Office da inserire viene restituita come nome dell'estensione dell'applicazione di Office, che corrisponde a un valore in **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L'host deve cercare questi valori nel registro di sistema e quindi inserire automaticamente le estensioni.
