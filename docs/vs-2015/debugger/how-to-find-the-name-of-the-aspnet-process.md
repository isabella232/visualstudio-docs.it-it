---
title: 'Procedura: trovare il nome del processo ASP.NET | Microsoft Docs'
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
- ASP.NET debugging, ASP.NET process
- ASP.NET process
ms.assetid: 931a7597-b0f0-4a28-931d-46e63344435f
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 223e060083554169ab6ffdb95faf4979e9466d02
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49825621"
---
# <a name="how-to-find-the-name-of-the-aspnet-process"></a>Procedura: individuare il nome del processo ASP.NET
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per connettersi a un'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in esecuzione, è necessario conoscere il nome del processo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)].  
  
- Se si esegue IIS 6.0 o IIS 7.0, il nome sarà w3wp.exe.  
  
- Se si esegue una versione precedente di IIS, il nome sarà invece aspnet_wp.exe.  
  
  Per le applicazioni compilate usando [!INCLUDE[vsprvslong](../includes/vsprvslong-md.md)] o versioni successive, il [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] codice può risiedere nel file system ed eseguire il server di prova WebDev.WebServer.exe. In tal caso, è necessario connettersi a WebDev.WebServer.exe anziché al processo [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. Questo scenario è valido solo per il debug locale.  
  
  Le applicazioni ASP più obsolete vengono eseguite nel processo IIS inetinfo.exe quando sono in esecuzione all'interno del processo.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-determine-whether-project-code-resides-on-the-file-system-or-iis"></a>Per determinare se il codice di progetto risiede nel file system o in IIS  
  
1.  In Visual Studio, aprire **Esplora soluzioni** se non è già aperto.  
  
2.  Selezionare il nodo superiore che contiene il nome dell'applicazione.  
  
3.  Se il **proprietà** titolo della finestra contiene un percorso di file, il codice dell'applicazione si trova nel file system.  
  
     In caso contrario, il **proprietà** titolo della finestra conterrà il nome del sito Web.  
  
### <a name="to-determine-the-iis-version-under-which-the-application-is-running"></a>Per determinare la versione di IIS in cui l'applicazione è in esecuzione  
  
1.  Trovare **strumenti di amministrazione** ed eseguirlo. A seconda del sistema operativo, potrebbe trattarsi di un'icona all'interno **Pannello di controllo**, o una voce di menu che viene visualizzato quando si fa clic **avviare**.  
  
     In Windows XP **Pannello di controllo** può essere nella visualizzazione classica o categoria. In visualizzazione per categorie, è necessario fare clic su **passa alla visualizzazione classica** oppure **prestazioni e manutenzione** per visualizzare il **strumenti di amministrazione** icona.  
  
2.  Dal **strumenti di amministrazione**, eseguire Internet Information Services. Viene visualizzata una finestra di dialogo MMC.  
  
3.  Se nel riquadro sinistro sono elencati più computer, selezionare quello in cui risiede il codice dell'applicazione.  
  
4.  La versione di IIS è nel **versione** colonna del riquadro di destra.  
  
## <a name="see-also"></a>Vedere anche  
 [Prerequisiti per il debug di applicazioni Web remoto](../debugger/prerequistes-for-remote-debugging-web-applications.md)   
 [Requisiti di sistema](../debugger/aspnet-debugging-system-requirements.md)   
 [Preparazione al Debug di ASP.NET](../debugger/preparing-to-debug-aspnet.md)   
 [Debug di script e applicazioni Web](../debugger/debugging-web-applications-and-script.md)



