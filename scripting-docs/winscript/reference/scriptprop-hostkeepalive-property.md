---
title: Proprietà SCRIPTPROP_HOSTKEEPALIVE | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: bfa199f2-28ba-4320-bc0f-2320fad018bd
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3724bfcb1ec42617cda4c89269cb0160accafb1a
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58150205"
---
# <a name="scriptprophostkeepalive-property"></a>Proprietà SCRIPTPROP_HOSTKEEPALIVE
Consente di specificare se il motore di scripting deve essere mantenuto pienamente funzionale se sono presenti riferimenti in sospeso.  
  
 Uso [IActiveScriptProperty::SetProperty](../../winscript/reference/iactivescriptproperty-setproperty.md) per impostare questa proprietà su `true`. Se questa proprietà è impostata su `true`, il motore di scripting viene mantenuto completamente funzionale, purché vi sia almeno un riferimento in sospeso per il motore di script stesso o per un `IDispatch` puntatore a un oggetto JavaScript creato tramite la creazione di script motore. Quando questa proprietà è impostata su `true`, è consigliabile non esplicitamente chiudere o reimpostare il motore di script usando il [IActiveScript::Close](../../winscript/reference/iactivescript-close.md) oppure [IActiveScript:: Setscriptstate](../../winscript/reference/iactivescript-setscriptstate.md) metodi. La versione dell'ultimo riferimento a un oggetto script si arresta il motore di script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
#define SCRIPTPROP_HOSTKEEPALIVE 0x70000004  
```  
  
## <a name="requirements"></a>Requisiti  
 Questa proprietà viene visualizzata solo nella versione di activscp.idl installata con [!INCLUDE[win8](../../javascript/includes/win8-md.md)], con 2707082 KB per Internet Explorer 8 in [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)], o con 2722913 KB per Internet Explorer 9 sul [!INCLUDE[win7](../../winscript/reference/includes/win7-md.md)] o [!INCLUDE[vista_first](../../winscript/reference/includes/vista-first-md.md)].