---
title: 'Procedura: Raccogliere dati sulle prestazioni per un sito Web | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vsperf.url.url
- vsperf.chooseurl
- vs.performance.wizard.asppage
- vsperf.url.ok
- vsperf.url.cancel
helpviewer_keywords:
- Profiling Tools,profiling ASP.NET
- web sites, performance profiling
- ASP.NET, performance profilng
ms.assetid: a62d27fd-a966-4065-bebe-6874195a71fb
caps.latest.revision: 38
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3307b5372852d6f3e269264a02fa2c90cb1acd22
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63432793"
---
# <a name="how-to-collect-performance-data-for-a-web-site"></a>Procedura: Raccogliere dati sulle prestazioni per un sito Web
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per raccogliere dati sulle prestazioni di un'applicazione Web di **, è possibile usare la** Creazione guidata sessione di prestazioni [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] . È possibile profilare un'applicazione Web aperta in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] oppure un sito Web di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] disponibile nel computer locale e non aperto nell'IDE di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
> [!NOTE]
> La **Creazione guidata sessione di prestazioni** consente di aggiungere dati di interazione tra livelli (TIP), dati relativi alle prestazioni di JScript o entrambi ai dati di profilatura raccolti. L'opzione TIP raccoglie dati dai processi sul lato server. L'opzione di profilatura JScript raccoglie dati da script in esecuzione in un sito Web locale o remoto. Nella maggior parte dei casi, è consigliabile scegliere solo una delle opzioni.  
  
 In base alle autorizzazioni di accesso a livello utente che un amministratore ha reso disponibili, un singolo utente può avere o meno le autorizzazioni di sicurezza necessarie per creare una sessione del profiler sul computer che ospita il processo ASP.NET. Gli esempi seguenti illustrano le possibili differenze tra i diversi tipi di utenti:  
  
- Se l'amministratore ha impostato l'avvio del driver e del servizio, alcuni utenti possono accedere a funzionalità di profilatura avanzate.  
  
- Gli utenti di dominio possono accedere soltanto ad esempi di profilatura.  
  
- Alcuni utenti possono negare l'accesso alle funzionalità di profilatura a tutti gli altri utenti.  
  
  Per altre informazioni, vedere [Profilatura e sicurezza in Windows Vista](../profiling/profiling-and-windows-vista-security.md) e le opzioni ADMIN in [VSPerfCmd](../profiling/vsperfcmd.md).  
  
### <a name="to-profile-a-web-site-project"></a>Per profilare un progetto di sito Web  
  
1. Aprire il progetto Web di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] in [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] o [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.  
  
3. Nella prima pagina della procedura guidata selezionare un metodo di profilatura e quindi fare clic su **Avanti**. Per altre informazioni sui metodi di profilatura, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md). Tenere presente che il metodo di profilatura del visualizzatore di concorrenza non è disponibile per le applicazioni Web.  
  
4. Nell'elenco a discesa **Specificare l'applicazione di destinazione per la profilatura** verificare che il progetto corrente sia selezionato e quindi fare clic su **Avanti**.  
  
5. Nella terza pagina della procedura guidata è possibile scegliere di aggiungere dati di profilatura dell'interazione tra livelli (TIP), dati da JavaScript in esecuzione nelle pagine Web o entrambi.  
  
    - Per raccogliere dati di interazione tra livelli, selezionare la casella di controllo **Abilita profilatura interazione tra livelli** .  
  
    - Per raccogliere dati da JavaScript in esecuzione nelle pagine Web, selezionare la casella di controllo **Profila JavaScript** .  
  
6. Scegliere **Avanti**.  
  
7. Nella quarta pagina della procedura guidata fare clic su **Fine**.  
  
8. Verrà creata una sessione di prestazioni per l'applicazione di [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] e il sito Web verrà avviato nel browser. Verificare la funzionalità che si vuole profilare e quindi chiudere il browser.  
  
     Il profiler genera il file di dati e apre la visualizzazione Riepilogo dei dati nella finestra principale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
### <a name="to-profile-a-web-site-without-opening-a-project-in-visual-studio"></a>Per profilare un sito Web senza aprire un progetto in Visual Studio  
  
1. Aprire [!INCLUDE[vsPreShort](../includes/vspreshort-md.md)] o [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)].  
  
2. Nel menu **Analizza** fare clic su **Avvia Creazione guidata sessione di prestazioni**.  
  
3. Nella prima pagina della procedura guidata selezionare un metodo di profilatura e quindi fare clic su **Avanti**. Per altre informazioni, vedere [Informazioni sui metodi di raccolta delle prestazioni](../profiling/understanding-performance-collection-methods.md).  
  
4. Nella seconda pagina della procedura guidata, selezionare l'opzione **Profilatura di un'applicazione ASP.NET o JavaScript** e quindi fare clic su **Avanti**.  
  
5. Nella terza pagina della procedura guidata digitare l'URL della home page dell'applicazione nella casella **Specificare l'URL o il percorso che esegue l'applicazione Web** e quindi fare clic su **Avanti**.  
  
   - Per un sito Web basato su un server (IIS), digitare l'URL, ad esempio **http://localhost/MySite/default.aspx**. In questo modo verrà profilata l'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] presente nel computer locale nella radice dell'applicazione di MySite e in Internet Explorer verrà aperta la pagina default.aspx del sito per avviare la sessione.  
  
   - Per un sito Web basato su file, digitare un percorso, ad esempio file///**c:\WebSites\MySite\default.aspx**. In questo modo verrà profilata l'applicazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] presente in c:\webSites\MySite e in Internet Explorer verrà aperta la pagina http://localhost:nnnn/MySite/default.aspx per avviare la sessione.  
  
   - Per i siti esterni che si desidera raccogliere dati JavaScript, digitare l'URL, ad esempio http:\//www.contoso.com.  
  
     Per altre informazioni, visualizzare le pagine delle proprietà per un file binario di destinazione [!INCLUDE[vstecasp](../includes/vstecasp-md.md)] .  
  
6. Nella terza pagina della procedura guidata è possibile scegliere di aggiungere dati di profilatura dell'interazione tra livelli (TIP), dati da JavaScript in esecuzione nelle pagine Web o entrambi.  
  
   - Per raccogliere dati di interazione tra livelli, selezionare la casella di controllo **Abilita profilatura interazione tra livelli** .  
  
   - Per raccogliere dati da JavaScript in esecuzione nelle pagine Web, selezionare la casella di controllo **Profila JavaScript** .  
  
7. Scegliere **Avanti**.  
  
8. Nella quarta pagina della procedura guidata fare clic su **Fine**.  
  
9. Verrà creata una sessione di prestazioni per l'applicazione ASP.NET e il sito Web verrà avviato nel browser. Verificare la funzionalità che si vuole profilare e quindi chiudere il browser.  
  
     Il profiler genera il file di dati e apre la visualizzazione Riepilogo dei dati nella finestra principale di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Overviews](../profiling/overviews-performance-tools.md)  (Panoramiche)  
 [Configuring Performance Sessions](../profiling/configuring-performance-sessions.md)  (Configurazione di sessioni di prestazioni)  
 [Informazioni sui valori dei dati di strumentazione](../profiling/understanding-instrumentation-data-values.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)
