---
title: "Errore: Sito Usa l'indirizzo IP | Microsoft Docs"
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62d975903bc29835cbf43a21e38fe727a37aec9c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49306358"
---
# <a name="error-site-uses-ip-address"></a>Errore: il sito utilizza un indirizzo IP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questo errore si verifica quando il debugger tenta di connettersi automaticamente a un'applicazione Web che utilizza un indirizzo IP Ciò si verifica se si modificano **Identificazione sito Web** al **Usa indirizzo IP specifico** in IIS.  
  
 Per il funzionamento della connessione automatica, occorre creare il progetto con l'indirizzo IP specifico piuttosto che con il semplice nome del computer. In caso contrario, il debugger modificherà il nome del computer in localhost causando l'esito negativo dell'invio del verbo debug a IIS.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Utilizzare la connessione manuale (dal menu Debug, scegli **Connetti a processo**).  
  
     -oppure-  
  
2.  Modifica il **Identificazione sito Web IIS** impostazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni Web: errori e risoluzione dei problemi](../debugger/debugging-web-applications-errors-and-troubleshooting.md)



