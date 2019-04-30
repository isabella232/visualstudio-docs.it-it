---
title: Prerequisiti per la distribuzione dell'applicazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, platform detection
- ClickOnce deployment, prerequisites
- ClickOnce deployment, dependencies
- prerequisites, ClickOnce
- dependencies, ClickOnce
ms.assetid: fc6e047e-ad94-44e8-8ff5-b6d1f4ca7735
caps.latest.revision: 53
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4945efddb91142ce04f5b117129428ec4a054fc3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63427250"
---
# <a name="application-deployment-prerequisites"></a>Prerequisiti per la distribuzione dell'applicazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Affinché l'applicazione venga installata ed eseguita correttamente, è necessario che nel computer di destinazione siano già installati tutti i componenti da cui l'applicazione dipende. Ad esempio, la maggior parte delle applicazioni create con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hanno una dipendenza da [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]; prima di installare l'applicazione, è necessario che nel computer di destinazione sia presente la versione corretta di Common Language Runtime.  
  
 È possibile selezionare questi prerequisiti sono le **Prerequisites Dialog Box** e installare .NET Framework e altri componenti ridistribuibili come parte dell'installazione. Questa procedura è denominata *bootstrap*. Successivamente [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] genera un programma eseguibile di Windows denominato Setup.exe, noto anche come un *bootstrapper*. Il programma di avvio automatico installa questi prerequisiti prima dell'esecuzione dell'applicazione. Per altre informazioni sulla selezione di questi prerequisiti, vedere [Prerequisites Dialog Box](../ide/reference/prerequisites-dialog-box.md).  
  
 Ogni prerequisito è un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico è un gruppo di directory e file che contengono i file manifesto in cui è descritto come deve essere installato il prerequisito. Se i prerequisiti dell'applicazione non sono elencati nella finestra di dialogo **Prerequisiti**, è possibile creare pacchetti del programma di avvio automatico personalizzati e aggiungerli a Visual Studio. A questo punto è possibile selezionare i prerequisiti nella finestra di dialogo **Prerequisiti**. Per altre informazioni, vedere [creazione di pacchetti Bootstrapper](../deployment/creating-bootstrapper-packages.md).  
  
 Per impostazione predefinita, il bootstrap è abilitato per la distribuzione ClickOnce. Il programma di avvio automatico generato per la distribuzione ClickOnce è firmato. È possibile disabilitare il bootstrap per un componente, ma è consigliabile procedere solo dopo avere verificato che in tutti i computer di destinazione sia già installata la versione corretta del componente.  
  
## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrap e distribuzione ClickOnce  
 Prima di installare un'applicazione in un computer client, [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] esaminerà il client per verificare che siano soddisfatti i requisiti specificati nel manifesto dell'applicazione, tra cui:  
  
- Versione minima richiesta di Common Language Runtime, specificata come dipendenza di assembly nel manifesto dell'applicazione.  
  
- Versione minima del sistema operativo Windows richiesta dall'applicazione, specificata nel manifesto dell'applicazione mediante l'elemento `<osVersionInfo>` (Vedere [ \<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md))  
  
- Versione minima di tutti gli assembly che devono essere preinstallati nella Global Assembly Cache (GAC), specificata dalle dichiarazioni delle dipendenze degli assembly nel manifesto dell'assembly.  
  
  [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] può rilevare i prerequisiti mancanti, ed è possibile installare i prerequisiti tramite un programma di avvio automatico. Per altre informazioni, vedere [Procedura: Installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  
  
> [!NOTE]
> Per modificare i valori nei manifesti generati da strumenti come [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e MageUI.exe, è necessario modificare il manifesto dell'applicazione in un editor di testo, quindi firmare nuovamente sia il manifesto dell'applicazione che quello della distribuzione. Per altre informazioni, vedere [Procedura: Firmare nuovamente i manifesti dell'applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  
  
 Se si usa Visual Studio e ClickOnce per distribuire l'applicazione, i pacchetti del programma di avvio automatico selezionati per impostazione predefinita variano a seconda della versione di .NET Framework inclusa nella soluzione. Se invece si cambia la versione .NET Framework di destinazione, è necessario aggiornare manualmente le opzioni nella finestra di dialogo **Prerequisiti**.  
  
|.NET Framework di destinazione|Pacchetti del programma di avvio automatico selezionati|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  
  
 Con la distribuzione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)], la pagina Publish.htm generata mediante la Pubblicazione guidata di [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] punta a un collegamento per l'installazione della sola applicazione o a un collegamento per l'installazione sia dell'applicazione che dei componenti avviati automaticamente.  
  
 Se il programma di avvio automatico viene generato mediante la Pubblicazione guidata ClickOnce o la pagina di pubblicazione in Visual Studio, il file Setup.exe è firmato automaticamente. Se invece si preferisce usare il certificato del cliente per firmare il programma di avvio automatico, è possibile firmare il file in un secondo momento.  
  
## <a name="bootstrapping-and-msbuild"></a>Bootstrap e MSBuild  
 Se non si usa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], ma le applicazioni vengono compilate dalla riga di comando, l'applicazione di avvio automatico [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] può essere creata mediante un'attività di Microsoft Build Engine (MSBuild). Per altre informazioni, vedere [attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).  
  
 In alternativa al bootstrap, è possibile pre-distribuire i componenti mediante un sistema elettronico di distribuzione del software, ad esempio Microsoft Systems Management Server (SMS).  
  
## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argomenti della riga di comando per il programma di avvio automatico (Setup.exe)  
 Il file Setup.exe generato da [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e dalle attività di MSBuild supporta il piccolo set di argomenti della riga di comando indicato di seguito. Gli eventuali altri argomenti forniti all'applicazione di bootstrap vengono inoltrati al programma di installazione dell'applicazione.  
  
 Se si modifica una qualsiasi opzione del programma di avvio automatico, è necessario modificare il programma di avvio automatico non firmato, quindi firmare il relativo file in un secondo momento.  
  
|Argomento della riga di comando|Descrizione|  
|---------------------------|-----------------|  
|**-?, -h, -help**|Visualizza una finestra di dialogo della Guida.|  
|**-url, -componentsurl**|Visualizza l'URL archiviato e l'URL dei componenti per questa configurazione.|  
|**-url=** `location`|Imposta l'URL in cui Setup.exe cercherà l'applicazione [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)].|  
|**-componentsurl=** `location`|Imposta l'URL in cui Setup.exe cercherà le dipendenze, ad esempio [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].|  
|**-homesite=** `true` **&#124;** `false`|Quando `true`, le dipendenze vengono scaricate dal percorso preferito sul sito del fornitore. Questa impostazione sostituisce il **- componentsurl** impostazione. Quando `false`, le dipendenze vengono scaricate dall'URL specificato da **- componentsurl**.|  
  
## <a name="operating-system-support"></a>Supporto del sistema operativo  
 Il programma di avvio automatico di Visual Studio non è supportato in Windows Server 2008 Server Core o Windows Server 2008 R2 Server Core, che forniscono un ambiente server a bassa manutenzione con funzionalità limitate. Ad esempio, l'opzione di installazione dei componenti di base del server supporta esclusivamente il profilo .NET Framework 3.5 Server Core, quindi non è possibile eseguire le funzionalità di Visual Studio che dipendono dalla versione completa di .NET Framework.  
  
## <a name="see-also"></a>Vedere anche  
 [Scelta di una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)
