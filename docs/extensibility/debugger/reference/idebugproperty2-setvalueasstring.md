---
description: Imposta il valore di una proprietà da una stringa specificata.
title: IDebugProperty2::SetValueAsString | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2::SetValueAsString
helpviewer_keywords:
- IDebugProperty2::SetValueAsString
ms.assetid: 9e6a5054-41b7-4223-b509-b93689d366a5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6d71f6926e9b973f83ae8f6d8e4a64ac127eaca6cf85e335cb6970c261c56840
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121449014"
---
# <a name="idebugproperty2setvalueasstring"></a>IDebugProperty2::SetValueAsString
Imposta il valore di una proprietà da una stringa specificata.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT SetValueAsString ( 
   LPCOLESTR pszValue,
   UINT      nRadix,
   DWORD     dwTimeout
);
```

```csharp
int SetValueAsString ( 
   string pszValue,
   uint   nRadix,
   uint   dwTimeout
);
```

## <a name="parameters"></a>Parametri
`pszValue`\
[in] Stringa contenente il valore da impostare.

`nRadix`\
[in] Radice da utilizzare nell'interpretazione di qualsiasi informazione numerica. Può essere 0 per tentare di determinare automaticamente la radice.

`dwTimeout`\
[in] Specifica il tempo massimo, in millisecondi, di attesa prima della restituzione da questo metodo. Usare `INFINITE` per attendere a tempo indeterminato.

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce il codice di errore. Nella tabella seguente vengono illustrati altri valori possibili.

|Valore|Descrizione|
|-----------|-----------------|
|`E_SETVALUE_VALUE_CANNOT_BE_SET`|Non è stato possibile convertire la stringa in un valore di proprietà oppure non è stato possibile impostarlo.|
|`E_SETVALUE_VALUE_IS_READONLY`|la proprietà è di sola lettura.|

## <a name="see-also"></a>Vedi anche
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
