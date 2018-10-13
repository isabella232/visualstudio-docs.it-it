---
title: 'Errore: Il servizio di Visual Studio Remote Debugger nel computer di destinazione non può connettersi al computer | Microsoft Docs'
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
- vs.debug.error.service_access_denied_oncallback
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 89ecf99d-66bf-4da0-a840-aa95b0be1702
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a1c9e52c700f83b3da56bb7db82e1e4cd7976767
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49297761"
---
# <a name="error-the-visual-studio-remote-debugger-service-on-the-target-computer-cannot-connect-back-to-this-computer"></a>Errore: il servizio Visual Studio Remote Debugger nel computer di destinazione non è in grado di riconnettersi a questo computer
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il messaggio di errore viene visualizzato per segnalare che l'account utente utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio non è in grado di eseguire l'autenticazione per la connessione al computer dal quale viene eseguito il debug.  
  
 Nella tabella riportata di seguito sono indicati gli account in grado di accedere al computer:  
  
|||||  
|-|-|-|-|  
||Account LocalSystem|Account di dominio|Account locali con lo stesso nome utente e la stessa password in entrambi i computer|  
|Entrambi i computer nello stesso dominio|Yes|Yes|Yes|  
|Entrambi i computer in domini con trust bidirezionale|No|No|Yes|  
|Uno o entrambi i computer in un gruppo di lavoro|No|No|Yes|  
|Computer in domini diversi|No|No|Yes|  
  
 Si tenga inoltre presente quanto segue:  
  
-   L'account utilizzato per l'esecuzione del servizio Debugger remoto di Visual Studio deve essere un account amministrativo nel computer remoto in modo da poter eseguire il debug di qualsiasi processo.  
  
-   L'account deve anche essere concesse le `Log on as a service` privilegi nel computer remoto che usa la **criteri di sicurezza locali** strumento di amministrazione.  
  
-   Se si intende utilizzare un accesso al computer con account locale, è necessario eseguire il servizio Debugger remoto di Visual Studio con un account locale.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Assicurarsi che il servizio Debugger remoto di Visual Studio sia configurato in modo corretto nel computer remoto. Per altre informazioni, vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c).  
  
2.  Eseguire il servizio Debugger remoto utilizzando un account in grado di accedere al computer host del debugger, come indicato nella tabella precedente.  
  
### <a name="to-add-log-on-as-a-service-privilege"></a>Per aggiungere un privilegio "Accesso come servizio"  
  
1.  Nel **avviare** menu, scegliere **Pannello di controllo**.  
  
2.  Nel Pannello di controllo, scegliere **visualizzazione classica**, se necessario.  
  
3.  Fare doppio clic su **Strumenti di amministrazione**.  
  
4.  Nella finestra Strumenti di amministrazione, fare doppio clic su **criteri di sicurezza locali**.  
  
5.  Nel **impostazioni di sicurezza locali** finestra, espandere il **criteri locali** cartella.  
  
6.  Fare clic su **Assegnazione diritti utente**.  
  
7.  Nel **criterio** colonna, fare doppio clic su **Accedi come servizio** per visualizzare le assegnazioni dei criteri di gruppo locali correnti nel **Accedi come servizio** nella finestra di dialogo.  
  
8.  Per aggiungere nuovi utenti, scegliere il **Aggiungi utente o gruppo** pulsante.  
  
9. Dopo aver aggiunto gli utenti, fare clic **OK**.  
  
### <a name="to-work-around-this-error"></a>Per risolvere il problema  
  
-   Eseguire Remote Debugging Monitor come applicazione anziché come servizio.  
  
## <a name="see-also"></a>Vedere anche  
 [Risoluzione dei problemi e gli errori di debug remoto](../debugger/remote-debugging-errors-and-troubleshooting.md)   
 [Remote Debugging](../debugger/remote-debugging.md)



