---
title: Init | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c55ddec8-9101-4673-979b-4109caca9146
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0b2ed132e072d9ca8a0b9c98bfc5be6e25931805
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72734996"
---
# <a name="init"></a>Init
Prepara il componente di diagnostica della grafica integrato nell'applicazione per acquisire e registrare attivamente le informazioni grafiche in un file di log di grafica.

## <a name="syntax"></a>Sintassi

```C++
void Init(
  std::function<void (int len, wchar_t * pszBuffer)> vsgLogGetter
);
```

#### <a name="parameters"></a>Parametri
 `vsgLogGetter` Entità richiamabile, ad esempio una funzione, un puntatore a una funzione, un oggetto lambda o funzione, che accetta come parametri la lunghezza di un buffer composto da `wchar_t` e da un puntatore al buffer e che restituisce `void`. Una volta richiamata, l'entità richiamabile determina il nome del file che verrà utilizzato per registrare le informazioni grafiche e scrive tale nome nel buffer specificato prima della restituzione.

## <a name="remarks"></a>Osservazioni
 La funzione `Init` viene automaticamente chiamata quando viene costruita un'istanza della classe `VsgDbg` specificando il parametro `bDefaultInit` del costruttore come `true`; in caso contrario, `Init` deve essere chiamata in modo esplicito prima di acquisire e registrare attivamente le informazioni grafiche.

 È possibile finalizzare e chiudere il file di log di grafica attivo chiamando `UnInit`, quindi acquisire e registrare altre informazioni grafiche in un nuovo file di log di grafica chiamando nuovamente `Init`. È possibile ripetere questa procedura tutte le volte che si desidera creare diversi file di log di grafica indipendenti utilizzando la stessa istanza `VsgDbg`.

## <a name="see-also"></a>Vedere anche
- [UnInit](init.md)