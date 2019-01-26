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
ms.openlocfilehash: debe61f07a8aa8711f1bb0b75ff0c2b39a528b21
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54875836"
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
