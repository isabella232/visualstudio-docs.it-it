---
title: Prerequisiti per la distribuzione di applicazioni | Microsoft Docs
description: Informazioni sui prerequisiti di distribuzione per le applicazioni, incluso l'uso della finestra di dialogo Prerequisiti e dei pacchetti del programma di avvio automatico.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
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
manager: jmartens
ms.technology: vs-ide-deployment
ms.workload:
- multiple
ms.openlocfilehash: cdf5e873996f27c1ac56e7148dbea2aea491030c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160959"
---
# <a name="application-deployment-prerequisites"></a>Prerequisiti per la distribuzione dell'applicazione

Per fare in modo che l'applicazione sia installata ed eseguita correttamente, installare prima tutti i componenti da cui l'applicazione dipende dal computer di destinazione. Ad esempio, la maggior parte delle applicazioni create con [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hanno una dipendenza dal .NET Framework. In questo caso, la versione corretta di Common Language Runtime deve essere presente nel computer di destinazione prima dell'installazione dell'applicazione.

 È possibile selezionare questi prerequisiti nella finestra **di** dialogo Prerequisiti e installare il .NET Framework e qualsiasi altro ridistribuibile come parte dell'installazione. Questa procedura è denominata *bootstrap*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]genera un Windows eseguibile denominato *Setup.exe*, noto anche come programma *di avvio automatico.* Il programma di avvio automatico installa questi prerequisiti prima dell'esecuzione dell'applicazione. Per altre informazioni sulla selezione di questi prerequisiti, vedere [Finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

 Ogni prerequisito è un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico è un gruppo di directory e file contenenti i file manifesto che descrivono come vengono installati i prerequisiti. Se i prerequisiti dell'applicazione non sono elencati nella finestra di dialogo **Prerequisiti**, è possibile creare pacchetti del programma di avvio automatico personalizzati e aggiungerli a Visual Studio. A questo punto è possibile selezionare i prerequisiti nella finestra di dialogo **Prerequisiti**. Per altre informazioni, vedere [Creare pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md).

 Per impostazione predefinita, il bootstrap è abilitato per la distribuzione ClickOnce. Il programma di avvio automatico generato per la distribuzione ClickOnce è firmato. È possibile disabilitare il bootstrap per un componente, ma solo se si è certi che la versione corretta del componente sia già installata in tutti i computer di destinazione.

## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrap e distribuzione ClickOnce
 Prima di installare un'applicazione in un computer client, esamina il client per verificare che abbia i requisiti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] specificati nel manifesto dell'applicazione. Questi includono i requisiti seguenti:

- Versione minima richiesta di Common Language Runtime, specificata come dipendenza di assembly nel manifesto dell'applicazione.

- Versione minima del sistema operativo Windows richiesta dall'applicazione, specificata nel manifesto dell'applicazione mediante l'elemento `<osVersionInfo>` Vedere [ \<dependency> l'elemento](../deployment/dependency-element-clickonce-application.md).

- Versione minima di tutti gli assembly che devono essere preinstallati nella Global Assembly Cache (GAC), come specificato dalle dichiarazioni di dipendenza dell'assembly nel manifesto dell'assembly.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può rilevare i prerequisiti mancanti ed è possibile installare i prerequisiti usando un programma di avvio automatico. Per altre informazioni, vedere [Procedura: Installare i prerequisiti con un'ClickOnce app.](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)

> [!NOTE]
> Per modificare i valori nei manifesti generati da strumenti come eMageUI.exe, è necessario modificare il manifesto dell'applicazione in un editor di testo e quindi firmare nuovamente i manifesti dell'applicazione e [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] della distribuzione. ** Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Se si usa Visual Studio e ClickOnce per distribuire l'applicazione, i pacchetti del programma di avvio automatico selezionati per impostazione predefinita variano a seconda della versione di .NET Framework inclusa nella soluzione. Se invece si cambia la versione .NET Framework di destinazione, è necessario aggiornare manualmente le opzioni nella finestra di dialogo **Prerequisiti**.

|.NET Framework di destinazione|Pacchetti del programma di avvio automatico selezionati|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Con la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la pagina *Publish.htm* generata mediante la Pubblicazione guidata di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] punta a un collegamento per l'installazione della sola applicazione o a un collegamento per l'installazione sia dell'applicazione che dei componenti avviati automaticamente.

 Se si genera il programma di avvio automatico usando ClickOnce pubblicazione guidata o la pagina di pubblicazione in Visual Studio, laSetup.exe *viene* firmata automaticamente. Se invece si preferisce usare il certificato del cliente per firmare il programma di avvio automatico, è possibile firmare il file in un secondo momento.

## <a name="bootstrapping-and-msbuild"></a>Bootstrap e MSBuild
 Se non si usa , ma si compilano le applicazioni dalla riga di comando, è possibile creare l'applicazione di bootstrap usando un'attività Microsoft Build Engine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] (MSBuild). Per altre informazioni, vedere [Attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).

 In alternativa al bootstrap, è possibile pre-distribuire i componenti mediante un sistema elettronico di distribuzione del software, ad esempio Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argomenti della riga di comando per il programma di avvio automatico (Setup.exe)
 Il *Setup.exe* generato da e le attività MSBuild [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] supportano il set seguente di argomenti della riga di comando. Eventuali altri argomenti vengono inoltrati al programma di installazione dell'applicazione.

 Se si modificano le opzioni del programma di avvio automatico, è necessario modificare il programma di avvio automatico non firmato e quindi firmare in un secondo momento il file del programma di avvio automatico.

| Argomento della riga di comando | Descrizione |
| - | - |
| **-?, -h, -help** | Visualizza una finestra di dialogo della Guida. |
| **-url, -componentsurl** | Visualizza l'URL archiviato e l'URL dei componenti per questa configurazione. |
| **-url=**`location` | Imposta l'URL in cui *Setup.exe* cercherà l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. |
| **-componentsurl=** `location` | Imposta l'URL *Setup.exe* cercare le dipendenze, ad esempio il .NET Framework. |
| **-homesite=** `true` **&#124;**`false` | Quando `true` , scarica le dipendenze dalla posizione preferita nel sito del fornitore. Questa impostazione esegue l'override **dell'impostazione -componentsurl.** Quando `false` , scarica le dipendenze dall'URL specificato da **-componentsurl**. |

## <a name="operating-system-support"></a>Supporto dei sistemi operativi
 Il programma Visual Studio bootstrap non è supportato in Windows Server 2008 Server Core o Windows Server 2008 R2 Server Core, in quanto offre un ambiente server a bassa manutenzione con funzionalità limitate. Ad esempio, l'opzione di installazione Server Core supporta solo il profilo server core di .NET Framework 3.5, che non può eseguire le funzionalità di Visual Studio che dipendono dalla versione .NET Framework.

## <a name="see-also"></a>Vedi anche
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)