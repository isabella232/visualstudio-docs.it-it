---
title: Debug di applicazioni Web distribuite | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ASP.NET Web applications
- Web services, debugging
- XML, debugging Web services
- debugging Web services
- ASP.NET, debugging Web applications
- XML Web services, debugging
ms.assetid: b938a91b-be96-416f-83bc-4177e7f3929a
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 923a8e104f03a4014f269f587d5cb3a1da5266b7
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51807542"
---
# <a name="debugging-deployed-web-applications"></a>Debug di applicazioni Web distribuite
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se è necessario eseguire il debug di un'applicazione Web in esecuzione su un server di produzione, è consigliabile procedere con cautela. In caso di connessione al processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] per eseguire il debug e raggiungere un punto di interruzione, ad esempio, tutto il codice gestito nel processo di lavoro si arresta. L'arresto di tutto il codice gestito nel processo di lavoro può comportare l'arresto del lavoro per tutti gli utenti del server. Prima di eseguire il debug su un server di produzione, tenere in considerazione il potenziale impatto sulle attività produttive.  
  
 Per utilizzare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per eseguire il debug di un'applicazione distribuita, è necessario effettuare la connessione al processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] e verificare che il debugger abbia accesso ai simboli per l'applicazione. Inoltre, è necessario individuare e aprire i file di origine dell'applicazione. Per altre informazioni, vedere [specifica simboli (PDB) e i file di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md), [procedura: trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md), e [requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md).  
  
> [!NOTE]
>  Molte applicazioni Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] fanno riferimento a DLL contenenti logica di business o altro codice utile. Tale riferimento consente di copiare automaticamente la DLL dal computer locale alla cartella \bin della directory virtuale dell'applicazione Web. Quando si esegue il debug, tenere presente che l'applicazione Web fa riferimento a tale copia della DLL e non alla copia presente sul computer locale.  
  
 La connessione al processo di lavoro [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] è praticamente identica alla connessione a qualsiasi altro processo remoto. Quando si è connessi, se non è aperto il progetto corretto, viene visualizzata una finestra di dialogo quando l'applicazione si interrompe. In questa finestra di dialogo è necessario immettere il percorso dei file di origine dell'applicazione. Il nome file specificato nella finestra di dialogo deve corrispondere a quello specificato nei simboli di debug, che si trovano sul server Web. Per altre informazioni, vedere [connettersi a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)   
 [Procedura: abilitare il debug per le applicazioni ASP.NET](../debugger/how-to-enable-debugging-for-aspnet-applications.md)   
 [Procedura: trovare il nome del processo ASP.NET](../debugger/how-to-find-the-name-of-the-aspnet-process.md)   
 [Specificare file di simboli (PDB) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)



