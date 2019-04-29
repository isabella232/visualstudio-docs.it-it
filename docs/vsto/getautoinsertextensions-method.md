---
title: Metodo GetAutoInsertExtensions
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: fb767ec7301a1d4e0f29003971b017339228fc9f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62972278"
---
# <a name="getautoinsertextensions-method"></a>Metodo GetAutoInsertExtensions
  Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.

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
|*psaExtensionNames*|I nomi di estensione delle App per Office.|

## <a name="return-value"></a>Valore restituito
 Valore HRESULT che indica se il metodo è stato completato correttamente.

## <a name="remarks"></a>Note
 Ogni app per Office deve essere inserito viene restituito come un'estensione di applicazioni di Office, che corrisponde a un valore inferiore **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L'host deve cercare questi valori nel Registro di sistema e quindi inserire automaticamente le estensioni.
