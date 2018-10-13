---
title: Problemi di sicurezza | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c20ef751960bed02b6b6b1d393f168a9b8e510f
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49219375"
---
# <a name="security-issues"></a>Problemi relativi alla sicurezza
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per eseguire il debug di un programma che Usa Visual Studio, le sole autorizzazioni necessite sono gli stessi uno sviluppatore deve eseguire il programma. Sono inclusi il debug remoto per la maggior parte delle situazioni (alcune situazioni che comportano altri servizi, ad esempio il servizio di informazioni Internet, potrebbe essere necessario un livello superiore di autorizzazioni).  
  
 Mentre è in esecuzione Visual Studio, il gestore di debug di processi (PDM) tiene traccia dei processi di debug nel computer locale. In modalità remota, viene avviato un programma denominato msvsmon.exe dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. Si noti che msvsmon.exe non è un servizio e deve essere avviata manualmente per abilitare il debug remoto su tale computer. Quando Visual Studio (o msvsmon.exe) non è in esecuzione, nessun processo viene tenuta traccia per il debug.  
  
 Ciò significa che uno sviluppatore può eseguire il debug di programmi che potrà iniziare senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug di processi avviati da un altro utente, se tale altra persona è un membro dello stesso gruppo di sicurezza. Per abilitare il debug remoto, è necessario solo per copiare i necessari file all'istanza remota del computer e avviare msvsmon.exe (vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) per altri dettagli).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Gestione di Debug di processi](../../extensibility/debugger/process-debug-manager.md)   
 [Impostare Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)

