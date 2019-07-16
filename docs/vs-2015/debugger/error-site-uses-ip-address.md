---
title: "Errore: Sito Usa l'indirizzo IP | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
f1_keywords:
- vs.debug.error.webdbg_siteusesipaddress
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, Web application errors
ms.assetid: b2b8ddc8-746d-46e3-87a6-b956b1ee048d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 46eace1c566a2810c5914a49654f8393f425fdee
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155744"
---
# <a name="error-site-uses-ip-address"></a>Errore: Il sito usa un indirizzo IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo errore si verifica quando il debugger tenta di connettersi automaticamente a un'applicazione Web che utilizza un indirizzo IP ed è dovuto alla selezione di **Usa indirizzo IP specifico** anziché **Identificazione sito Web** in IIS.  
  
 Per il funzionamento della connessione automatica, occorre creare il progetto con l'indirizzo IP specifico piuttosto che con il semplice nome del computer. In caso contrario, il debugger modificherà il nome del computer in localhost causando l'esito negativo dell'invio del verbo debug a IIS.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1. Utilizzare la connessione manuale, scegliendo **Connetti a processo** dal menu Debug.  
  
     -oppure-  
  
2. Modificare l'impostazione **Identificazione sito Web IIS**.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: Errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)
