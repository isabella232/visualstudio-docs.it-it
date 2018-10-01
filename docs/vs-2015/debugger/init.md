---
title: Init | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d394ce2f149be842b42ffe4661cfbc361858bd71
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527479"
---
# <a name="init"></a>Init
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Init](https://docs.microsoft.com/visualstudio/debugger/graphics/init).  
  
Prepara il componente di diagnostica della grafica integrato nell'applicazione per acquisire e registrare attivamente le informazioni grafiche in un file di log di grafica.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
void Init(  
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `vsgLogGetter`  
 Entità richiamabile, ad esempio una funzione, un puntatore a una funzione, un oggetto lambda o funzione che accetta come parametri la lunghezza di un buffer composto da `wchar_t` e da un puntatore a tale buffer e che restituisce `void`. Una volta richiamata, l'entità richiamabile determina il nome del file che verrà utilizzato per registrare le informazioni grafiche e scrive tale nome nel buffer specificato prima della restituzione.  
  
## <a name="remarks"></a>Note  
 La funzione `Init` viene automaticamente chiamata quando viene costruita un'istanza della classe `VsgDbg` specificando il parametro `bDefaultInit` del costruttore come `true`; in caso contrario, `Init` deve essere chiamata in modo esplicito prima di acquisire e registrare attivamente le informazioni grafiche.  
  
 È possibile finalizzare e chiudere il file di log di grafica attivo chiamando `UnInit`, quindi acquisire e registrare altre informazioni grafiche in un nuovo file di log di grafica chiamando nuovamente `Init`. È possibile ripetere questa procedura tutte le volte che si desidera creare diversi file di log di grafica indipendenti utilizzando la stessa istanza `VsgDbg`.  
  
## <a name="see-also"></a>Vedere anche  
 [UnInit](../debugger/init.md)



