---
description: Questo errore si verifica quando il debugger tenta di connettersi automaticamente a un'applicazione Web che utilizza un indirizzo IP
title: Il sito usa indirizzi IP | Microsoft Docs
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
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 07c7cfe629710a880f85a22c38eced5068edf7bad580be6fb44150f75e5c5aa4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420131"
---
# <a name="error-site-uses-ip-address"></a>Errore: il sito utilizza un indirizzo IP
Questo errore si verifica quando il debugger tenta di connettersi automaticamente a un'applicazione Web che utilizza un indirizzo IP ed è dovuto alla selezione di **Usa indirizzo IP specifico** anziché **Identificazione sito Web** in IIS.

 Per il funzionamento della connessione automatica, occorre creare il progetto con l'indirizzo IP specifico piuttosto che con il semplice nome del computer. In caso contrario, il debugger modificherà il nome del computer in localhost causando l'esito negativo dell'invio del verbo debug a IIS.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Utilizzare la connessione manuale, scegliendo **Connetti a processo** dal menu Debug.

     -oppure-

2. Modificare l'impostazione **Identificazione sito Web IIS**.

## <a name="see-also"></a>Vedi anche
- [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
