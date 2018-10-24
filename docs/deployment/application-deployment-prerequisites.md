---
title: Prerequisiti per la distribuzione dell'applicazione | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 421092218cdeb889fe195917e46b123c73e7e1f9
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49851803"
---
# <a name="application-deployment-prerequisites"></a>Prerequisiti per la distribuzione dell'applicazione

Affinché l'applicazione per installare ed eseguire correttamente, prima di tutto installare tutti i componenti da cui l'applicazione dipende nel computer di destinazione. Ad esempio, la maggior parte delle applicazioni create utilizzando [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] attiva una dipendenza di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. In questo caso, la versione corretta di common language runtime deve essere presente nel computer di destinazione prima di installare l'applicazione.  

 È possibile selezionare questi prerequisiti sono le **Prerequisites Dialog Box** e installare .NET Framework e qualsiasi altro componente ridistribuibile come parte dell'installazione. Questa pratica è nota come *bootstrap*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Genera un programma eseguibile di Windows denominato *Setup.exe*, noto anche come una *bootstrapper*. Il programma di avvio automatico installa questi prerequisiti prima dell'esecuzione dell'applicazione. Per altre informazioni sulla selezione di questi prerequisiti, vedere [finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).  

 Ogni prerequisito è un pacchetto del programma di avvio automatico. Un pacchetto di programma di bootstrap è un gruppo di file che contiene i file manifesto che descrivono la modalità in cui sono installati i prerequisiti e le directory. Se non sono elencati i prerequisiti dell'applicazione nel **la finestra di dialogo dei prerequisiti**, è possibile creare programmi di avvio automatico personalizzati e aggiungerli a Visual Studio. È quindi possibile selezionare i prerequisiti nel **Prerequisites Dialog Box**. Per altre informazioni, vedere [creano bootstrapper package](../deployment/creating-bootstrapper-packages.md).  

 Per impostazione predefinita, il bootstrap è abilitato per la distribuzione ClickOnce. Il programma di avvio automatico generato per la distribuzione ClickOnce è firmato. È possibile disabilitare il bootstrap per un componente, ma solo se si è certi che la versione corretta del componente è già installata in tutti i computer di destinazione.  

## <a name="bootstrapping-and-clickonce-deployment"></a>Avvio automatico e la distribuzione ClickOnce  
 Prima di installare un'applicazione in un computer client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esamina il client per verificare che abbia i requisiti specificati nel manifesto dell'applicazione. Sono inclusi i requisiti seguenti:  

- Versione minima richiesta di Common Language Runtime, specificata come dipendenza di assembly nel manifesto dell'applicazione.  

- Versione minima del sistema operativo Windows richiesta dall'applicazione, specificata nel manifesto dell'applicazione mediante l'elemento `<osVersionInfo>` (Vedere [ \<dipendenza > elemento](../deployment/dependency-element-clickonce-application.md).)  

- La versione minima di tutti gli assembly che devono essere preinstallati nella global assembly cache (GAC), come specificato dalle dichiarazioni delle dipendenze degli assembly nel manifesto dell'assembly.  

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può rilevare i prerequisiti mancanti, ed è possibile installare i prerequisiti tramite un programma di avvio automatico. Per altre informazioni, vedere [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).  

> [!NOTE]
>  Per modificare i valori nei manifesti generati dagli strumenti, ad esempio [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e *MageUI.exe*, è necessario modificare il manifesto dell'applicazione in un editor di testo e quindi firmare nuovamente i manifesti di distribuzione sia l'applicazione. Per altre informazioni, vedere [procedura: firmare manifesti dell'applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).  

 Se si usa Visual Studio e ClickOnce per distribuire l'applicazione, i pacchetti del programma di avvio automatico selezionati per impostazione predefinita variano a seconda della versione di .NET Framework inclusa nella soluzione. Tuttavia, se si modifica la versione di .NET Framework di destinazione, è necessario aggiornare le opzioni nella finestra di **Prerequisites Dialog Box** manualmente.  

|.NET Framework di destinazione|Pacchetti del programma di avvio automatico selezionati|  
|---------------------------|------------------------------------|  
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|  
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|  

 Con [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] distribuzione, il *Publish. htm* pagina generata dal [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] pubblicazione guidata punta a un collegamento che consente di installare solo l'applicazione o a un collegamento che consente di installare l'applicazione e l'avvio automatico componenti.  

 Se si genera il programma di bootstrap utilizzando la pubblicazione guidata ClickOnce o la pagina di pubblicazione in Visual Studio, il *Setup.exe* è firmato automaticamente. Se invece si preferisce usare il certificato del cliente per firmare il programma di avvio automatico, è possibile firmare il file in un secondo momento.  

## <a name="bootstrapping-and-msbuild"></a>Bootstrap e MSBuild  
 Se non si usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ma piuttosto la compilazione delle applicazioni dalla riga di comando, è possibile creare il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] bootstrap dell'applicazione tramite un'attività di Microsoft Build Engine (MSBuild). Per altre informazioni, vedere [attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).  

 In alternativa al bootstrap, è possibile pre-distribuire i componenti mediante un sistema elettronico di distribuzione del software, ad esempio Microsoft Systems Management Server (SMS).  

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argomenti della riga di comando di avvio automatico (Setup.exe)  
 Il *Setup.exe* generati da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e le attività di MSBuild supporta il set di argomenti della riga di comando seguente. Altri argomenti vengono inoltrati al programma di installazione dell'applicazione.  

 Se si modificano le opzioni di avvio automatico, è necessario modificare il programma di avvio senza segno e quindi accedere in seguito il file di programma di avvio automatico.  


| Argomento della riga di comando | Descrizione |
| - | - |
| **-?, -h, - help** | Visualizza una finestra di dialogo della Guida. |
| **-url - componentsurl** | Visualizza l'URL archiviato e l'URL dei componenti per questa configurazione. |
| **-url =** `location` | Imposta l'URL in cui *Setup.exe* cercherà il [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] dell'applicazione. |
| **-componentsurl =** `location` | Imposta l'URL in cui *Setup.exe* cercherà le dipendenze, ad esempio il [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. |
| **-homesite =** `true`**&#124;** `false` | Quando `true`, le dipendenze vengono scaricate dal percorso preferito sul sito del fornitore. Questa impostazione sostituisce il **- componentsurl** impostazione. Quando `false`, le dipendenze vengono scaricate dall'URL specificato da **- componentsurl**. |

## <a name="operating-system-support"></a>Supporto del sistema operativo  
 Il programma di bootstrap di Visual Studio non è supportato in Windows Server 2008 Server Core o Windows Server 2008 R2 Server Core, in quanto forniscono un ambiente server a bassa manutenzione con funzionalità limitata. Ad esempio, l'opzione di installazione Server Core supporta solo il profilo di .NET Framework 3.5 Server Core, che non è possibile eseguire le funzionalità di Visual Studio che dipendono da .NET Framework completo.  

## <a name="see-also"></a>Vedere anche  
 [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)   
 [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)