---
title: Metodo SetWefProcessId
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
ms.openlocfilehash: b426237816bfee53e7c3e50c19e29168b27e16e1
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/01/2018
ms.locfileid: "34693432"
---
# <a name="setwefprocessid-method"></a>Metodo SetWefProcessId
  Fornisce l'identificatore di processo che verrà eseguito il contenuto Web estensioni Framework (WEF).  
  
## <a name="syntax"></a>Sintassi  
  
```csharp  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*cui dwProcessId*|L'identificatore di processo che verrà utilizzato per eseguire il contenuto WEF.|  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Questo metodo deve essere chiamato dopo aver creato il processo del contenuto WEF ma prima dell'esecuzione di qualsiasi contenuto WEF.  
  
 Se si desidera l'ambiente di sviluppo per collegare un debugger al processo WEF contenuto, l'ambiente è necessario eseguire questa operazione nell'implementazione di questo metodo.  
  
  