---
title: Metodo GetAutoInsertExtensions
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
ms.openlocfilehash: f5d88af6f24306b7b243359c9797a2cb7e7449bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543507"
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

## <a name="remarks"></a>Osservazioni
 Ogni app per Office da inserire viene restituita come nome dell'estensione dell'applicazione di Office, che corrisponde a un valore in **HKEY_CURRENT_USER \software\microsoft\office\wef\developer**. L'host deve cercare questi valori nel registro di sistema e quindi inserire automaticamente le estensioni.
