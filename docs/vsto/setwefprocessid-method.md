---
title: Metodo SetWefProcessId
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
ms.openlocfilehash: 7807d0495c5f0548178b1bc2ecae12d57cc3b072
ms.sourcegitcommit: c0202a77d4dc562cdc55dc2e6223c062281d9749
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/24/2019
ms.locfileid: "54876122"
---
# <a name="setwefprocessid-method"></a>Metodo SetWefProcessId
  Fornisce l'identificatore di processo che eseguirà il contenuto Web estensioni Framework (WCF).  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*dwProcessId*|L'identificatore di processo che verrà usato per eseguire il contenuto di WCF.|  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Questo metodo deve essere chiamato dopo aver creato il processo contenuto WEF ma prima dell'esecuzione di qualsiasi contenuto WEF.  
  
 Se si desidera che l'ambiente di sviluppo per collegare un debugger al processo contenuto WEF, l'ambiente è necessario eseguire questa operazione nell'implementazione di questo metodo.  
