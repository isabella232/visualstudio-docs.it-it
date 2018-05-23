---
title: Metodo GetAutoInsertExtensions
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: f8573576b40afabb5ec568a0c471e7b1d79560ba
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/22/2018
---
# <a name="getautoinsertextensions-method"></a>Metodo GetAutoInsertExtensions
  Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.  
  
 Questo metodo è riservato per utilizzi futuri.  
  
## <a name="syntax"></a>Sintassi  
  
```c  
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
 Ogni app per Office deve essere inserito viene restituito come un'estensione di applicazione di Office, che corrisponde a un valore in **HKEY_CURRENT_USER\Software\Microsoft\Office\WEF\Developer**. L'host deve cercare questi valori nel Registro di sistema e quindi inserire automaticamente le estensioni.  
  
  