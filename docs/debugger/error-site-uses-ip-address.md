---
title: Il sito usa l'indirizzo IP | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b869a536ca3445069d9caf84eb862e407dfbe6dc
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852537"
---
# <a name="error-site-uses-ip-address"></a>Errore: il sito utilizza un indirizzo IP
Questo errore si verifica quando il debugger tenta di connettersi automaticamente a un'applicazione Web che utilizza un indirizzo IP ed è dovuto alla selezione di **Usa indirizzo IP specifico** anziché **Identificazione sito Web** in IIS.

 Per il funzionamento della connessione automatica, occorre creare il progetto con l'indirizzo IP specifico piuttosto che con il semplice nome del computer. In caso contrario, il debugger modificherà il nome del computer in localhost causando l'esito negativo dell'invio del verbo debug a IIS.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Utilizzare la connessione manuale, scegliendo **Connetti a processo** dal menu Debug.

     -oppure-

2. Modificare l'impostazione **Identificazione sito Web IIS**.

## <a name="see-also"></a>Vedere anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)