---
title: "Errore: il sito usa l'indirizzo IP | Microsoft Docs"
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
ms.openlocfilehash: 58db12ba9dbbc9526ac86262a6be5b2c0a7f765e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85460546"
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