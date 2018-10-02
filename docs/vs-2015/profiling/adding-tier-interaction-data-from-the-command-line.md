---
title: Aggiunta di dati di interazione tra livelli dalla riga di comando | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tier interaction profiling method
- profiling tools,tier interaction method
ms.assetid: 5a35647f-03f2-4555-8eeb-fda7e0080e67
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce7713b39acb7736e34f6ab6017b0cd32b1e1cfa
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/05/2018
ms.locfileid: "47590859"
---
# <a name="adding-tier-interaction-data-from-the-command-line"></a>Aggiunta di dati di interazione tra livelli dalla riga di comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiunta di dati di interazione tra livelli dalla riga di comando](https://docs.microsoft.com/visualstudio/profiling/adding-tier-interaction-data-from-the-command-line).  
  
La profilatura delle interazioni tra livelli offre informazioni aggiuntive sui tempi di esecuzione delle chiamate [!INCLUDE[vstecado](../includes/vstecado-md.md)] sincrone nelle funzioni di applicazioni multilivello che comunicano con uno o più database.  
  
 **Windows 8 e Windows Server 2012**  
  
 Per raccogliere dati di interazione tra livelli nelle applicazioni desktop di Windows 8 e nelle applicazioni Windows Server 2012, è necessario utilizzare il metodo di strumentazione. La raccolta di dati di interazione tra livelli nelle applicazioni Windows Store non è supportata.  
  
 **Versioni di Visual Studio**  
  
 I dati di profilatura delle interazioni tra livelli possono essere raccolti usando [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] o [!INCLUDE[vs_pro_current_short](../includes/vs-pro-current-short-md.md)], ma possono essere visualizzati solo in [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)] e [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)].  
  
 **Raccolta di dati TIP in un computer remoto**  
  
 Per raccogliere dati di interazione tra livelli in un computer remoto, è necessario copiare il **vs\_profiler\_**_\<piattaforma >_ **\_**  _\<Lingua >_**.exe** file la _% VSInstallDir %_**\Team Tools\Setups**cartella di Visual Studio nel computer remoto del computer e installarlo. Non è possibile utilizzare gli strumenti di profilatura di [Visual Studio Remote Tools](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) download del pacchetto.  
  
 **Report TIP**  
  
 I dati di interazione tra livelli possono essere visualizzati solo nell'IDE di [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]. I report sull'interazione tra livelli basati su file tramite [VSPerfReport](../profiling/vsperfreport.md) non sono disponibili.  
  
## <a name="adding-tier-interaction-data-with-vsperfcmd"></a>Aggiunta di dati di interazione tra livelli con VSPerfCmd  
 Lo strumento da riga di comando VSPerfASPNETCmd consente di accedere alla funzionalità completa disponibile negli strumenti di profilatura. Per aggiungere l'interazione tra livelli ai dati di profilatura raccolti tramite VSPerfCmd, è necessario usare l'utilità **VSPerfCLREnv** per impostare e rimuovere le variabili di ambiente che abilitano i dati di interazione tra livelli. Le opzioni specificate e le procedure necessarie per la raccolta dei dati dipendono dal tipo di applicazione di cui viene eseguita la profilatura.  
  
### <a name="profiling-stand-alone-applications"></a>Profilatura di applicazioni autonome  
 Per aggiungere i dati di interazione tra livelli in un'applicazione che non viene eseguita da un altro processo, ad esempio un'applicazione desktop di Windows che esegue chiamate [!INCLUDE[vstecado](../includes/vstecado-md.md)] sincrone a un database SQLServer, usare l'opzione **VSPerfClrEnv /InteractionOn** per impostare le variabili di ambiente e l'opzione **VSPerfClrEnv /InteractionOff** per rimuoverle.  
  
 Nell'esempio seguente un'applicazione desktop di Windows viene profilata tramite il metodo di strumentazione e vengono raccolti dati di interazione tra livelli.  
  
##### <a name="profiling-a-windows-desktop-application-example"></a>Esempio di profilatura di un'applicazione desktop di Windows  
  
1.  Aprire una finestra del prompt dei comandi con privilegi di amministratore. Fare clic su **Start**, scegliere **Tutti i programmi** e quindi **Accessori**. Fare clic con il pulsante destro del mouse su **Prompt dei comandi**, quindi scegliere **Esegui come amministratore**.  
  
2.  Inizializzare la profilatura .NET e le variabili di ambiente TIP. Digitare i comandi seguenti:  
  
    ```  
    vsperfclrenv /traceon  
    vsperfclrenv /interactionon  
    ```  
  
3.  Avvia il profiler. Digitare il comando seguente:  
  
    ```  
    vsperfcmd /start:trace /output:Desktop_tip.vsp   
    ```  
  
4.  Avviare l'applicazione con VSPerfCmd. Digitare il comando seguente:  
  
    ```  
    vsperfcmd /launch:DesktopApp.exe  
    ```  
  
5.  Usare l'applicazione per raccogliere i dati di profilatura e quindi chiuderla in modo normale.  
  
6.  Cancellare le variabili di ambiente TIP. Digitare il comando seguente:  
  
    ```  
    vsperfclrenv /off  
    ```  
  
 Per altre informazioni, vedere [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md).  
  
### <a name="profiling-services"></a>Profilatura di servizi  
 Per eseguire la profilatura di servizi, incluse le applicazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], usare l'opzione **VSPerfClrEnv /GlobalInteractionOn** per impostare le variabili di ambiente e l'opzione **VSPerfClrEnv /GlobalInteractionOff** per rimuoverle.  
  
 Quando si esegue la profilatura di servizi, incluse le applicazioni Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)], è spesso necessario riavviare il computer per abilitare la profilatura.  
  
 Nell'esempio seguente un servizio di Windows viene profilato tramite il metodo di strumentazione e vengono raccolti dati di interazione tra livelli.  
  
##### <a name="profiling-a-windows-service-example"></a>Esempio di profilatura di un servizio Windows  
  
1.  Se necessario, installare il servizio.  
  
2.  Aprire una finestra del prompt dei comandi con privilegi di amministratore. Fare clic su **Start**, scegliere **Tutti i programmi** e quindi **Accessori**. Fare clic con il pulsante destro del mouse su **Prompt dei comandi**, quindi scegliere **Esegui come amministratore**.  
  
3.  Inizializzare le variabili di ambiente di profilatura .NET. Digitare il comando seguente:  
  
    ```  
    vsperfclrenv /globaltraceon  
    ```  
  
4.  Inizializzare le variabili di ambiente TIP. Digitare il comando seguente  
  
    ```  
    vsperfclrenv /globalinteractionon  
    ```  
  
5.  Riavviare il computer per registrare le variabili di ambiente.  
  
6.  Aprire una finestra del prompt dei comandi con privilegi di amministratore.  
  
7.  Avvia il profiler. Digitare il comando seguente:  
  
    ```  
    vsperfcmd /start:trace /output:MiddleTier_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
8.  Se necessario, avviare il servizio.  
  
9. Connettere il profiler al servizio. Digitare il comando seguente:  
  
    ```  
    vsperfcmd /attach:MiddleTier.exe /output:MyService_tip.vsp /user:SYSTEM /crosssession   
    ```  
  
10. Usare il servizio e raccogliere i dati di profilatura.  
  
11. Interrompere il profiler. Digitare il comando seguente:  
  
     `vsperfcmd /detach`  
  
12. Cancellare le variabili di ambiente di profilatura .NET e TIP. Digitare il comando seguente:  
  
    ```  
    vsperfclrenv /globaloff  
    ```  
  
13. Riavviare il computer per registrare le variabili di ambiente cancellate.  
  
 Per altre informazioni, vedere uno degli argomenti seguenti:  
  
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)  
  
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)  
  
## <a name="adding-tier-interaction-data-with-vsperfaspnetcmd"></a>Aggiunta di dati di interazione tra livelli con VSPerfASPNETCmd  
 Lo strumento da riga di comando VSPerfASPNETCmd consente di eseguire facilmente la profilatura di applicazioni Web [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]. A differenza dello strumento da riga di comando **VSPerfCmd**, le opzioni sono ridotte, non è necessario impostare variabili di ambiente e non è necessario riavviare il computer. Queste funzionalità di VSPerfASPNETCmd rendono molto facile la raccolta di dati di interazione tra livelli.  
  
 Per aggiungere l'interazione tra livelli ai dati di profilatura raccolti tramite VSPerfASPNETCmd, aggiungere l'opzione **/TIP** alla riga di comando. Ad esempio, utilizzare la riga di comando seguente per raccogliere i dati di interazione tra livelli quando si raccolgono statistiche dell'applicazione per un'applicazione Web di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] utilizzando il metodo di strumentazione:  
  
```  
vsperfaspnetcmd /tip /trace http://localhost/MyWebApp  
```  
  
 Per altre informazioni su VSPerfASPNETCmd, vedere [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).



