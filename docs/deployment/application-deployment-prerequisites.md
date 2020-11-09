---
title: Prerequisiti per la distribuzione dell'applicazione | Microsoft Docs
description: Informazioni sui prerequisiti di distribuzione per le applicazioni, tra cui l'uso della finestra di dialogo Prerequisiti e dei pacchetti del programma di avvio automatico.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c87b0f6ded2960054cb553dbeb85681aa447668b
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94383248"
---
# <a name="application-deployment-prerequisites"></a>Prerequisiti per la distribuzione dell'applicazione

Per installare ed eseguire correttamente l'applicazione, installare prima tutti i componenti da cui dipende l'applicazione nel computer di destinazione. La maggior parte delle applicazioni create usando, ad esempio, dipende [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla .NET Framework. In tal caso, prima di installare l'applicazione, è necessario che nel computer di destinazione sia presente la versione corretta del Common Language Runtime.

 È possibile selezionare questi prerequisiti nella finestra di **dialogo Prerequisiti** e installare il .NET Framework e qualsiasi altro ridistribuibile come parte dell'installazione di. Questa procedura è denominata *bootstrap*. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genera un programma eseguibile di Windows denominato *Setup.exe* , noto anche come programma di *avvio automatico*. Il programma di avvio automatico installa questi prerequisiti prima dell'esecuzione dell'applicazione. Per ulteriori informazioni sulla selezione di questi prerequisiti, vedere la finestra di [dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md).

 Ogni prerequisito è un pacchetto del programma di avvio automatico. Un pacchetto del programma di avvio automatico è un gruppo di directory e file contenente i file manifesto che descrivono la modalità di installazione dei prerequisiti. Se i prerequisiti dell'applicazione non sono elencati nella finestra di dialogo **Prerequisiti** , è possibile creare pacchetti del programma di avvio automatico personalizzati e aggiungerli a Visual Studio. A questo punto è possibile selezionare i prerequisiti nella finestra di dialogo **Prerequisiti**. Per altre informazioni, vedere [creare pacchetti del programma di avvio automatico](../deployment/creating-bootstrapper-packages.md).

 Per impostazione predefinita, il bootstrap è abilitato per la distribuzione ClickOnce. Il programma di avvio automatico generato per la distribuzione ClickOnce è firmato. È possibile disabilitare il bootstrap per un componente, ma solo se si è certi che la versione corretta del componente sia già installata in tutti i computer di destinazione.

## <a name="bootstrapping-and-clickonce-deployment"></a>Bootstrap e distribuzione ClickOnce
 Prima di installare un'applicazione in un computer client, [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] esamina il client per assicurarsi che disponga dei requisiti specificati nel manifesto dell'applicazione. Sono inclusi i requisiti seguenti:

- Versione minima richiesta di Common Language Runtime, specificata come dipendenza di assembly nel manifesto dell'applicazione.

- Versione minima del sistema operativo Windows richiesta dall'applicazione, specificata nel manifesto dell'applicazione mediante l'elemento `<osVersionInfo>` (Vedere [ \<dependency> elemento](../deployment/dependency-element-clickonce-application.md)).

- Versione minima di tutti gli assembly che devono essere preinstallati nella Global Assembly Cache (GAC), come specificato dalle dichiarazioni di dipendenza degli assembly nel manifesto dell'assembly.

  [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] può rilevare i prerequisiti mancanti ed è possibile installare i prerequisiti usando un programma di avvio automatico. Per altre informazioni, vedere [procedura: installare i prerequisiti con un'applicazione ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md).

> [!NOTE]
> Per modificare i valori nei manifesti generati da strumenti quali [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e *MageUI.exe* , è necessario modificare il manifesto dell'applicazione in un editor di testo e quindi firmare nuovamente i manifesti dell'applicazione e della distribuzione. Per altre informazioni, vedere [Procedura: Firmare nuovamente manifesti di applicazione e distribuzione](../deployment/how-to-re-sign-application-and-deployment-manifests.md).

 Se si usa Visual Studio e ClickOnce per distribuire l'applicazione, i pacchetti del programma di avvio automatico selezionati per impostazione predefinita variano a seconda della versione di .NET Framework inclusa nella soluzione. Se invece si cambia la versione .NET Framework di destinazione, è necessario aggiornare manualmente le opzioni nella finestra di dialogo **Prerequisiti**.

|.NET Framework di destinazione|Pacchetti del programma di avvio automatico selezionati|
|---------------------------|------------------------------------|
|.NET Framework 4 Client Profile|.NET Framework 4 Client Profile<br /><br /> Windows Installer 3.1|
|.NET Framework 4|.NET Framework 4<br /><br /> Windows Installer 3.1|

 Con la distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], la pagina *Publish.htm* generata mediante la Pubblicazione guidata di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] punta a un collegamento per l'installazione della sola applicazione o a un collegamento per l'installazione sia dell'applicazione che dei componenti avviati automaticamente.

 Se si genera il programma di avvio automatico utilizzando la pubblicazione guidata ClickOnce o la pagina pubblica in Visual Studio, la *Setup.exe* viene firmata automaticamente. Se invece si preferisce usare il certificato del cliente per firmare il programma di avvio automatico, è possibile firmare il file in un secondo momento.

## <a name="bootstrapping-and-msbuild"></a>Bootstrap e MSBuild
 Se non si usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , ma si compilano le applicazioni nella riga di comando, è possibile creare l' [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] applicazione di bootstrap usando un'attività Microsoft Build Engine (MSBuild). Per altre informazioni, vedere [attività GenerateBootstrapper](../msbuild/generatebootstrapper-task.md).

 In alternativa al bootstrap, è possibile pre-distribuire i componenti mediante un sistema elettronico di distribuzione del software, ad esempio Microsoft Systems Management Server (SMS).

## <a name="bootstrapper-setupexe-command-line-arguments"></a>Argomenti della riga di comando per il programma di avvio automatico (Setup.exe)
 Il *Setup.exe* generato da [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e le attività MSBuild supportano il set di argomenti della riga di comando seguente. Tutti gli altri argomenti vengono trasmessi al programma di installazione dell'applicazione.

 Se si modificano le opzioni del programma di avvio automatico, è necessario modificare il programma di avvio automatico senza segno e successivamente firmare il file del programma di avvio automatico.

| Argomento della riga di comando | Descrizione |
| - | - |
| **-?, -h, -help** | Visualizza una finestra di dialogo della Guida. |
| **-url, -componentsurl** | Visualizza l'URL archiviato e l'URL dei componenti per questa configurazione. |
| **-URL =**`location` | Imposta l'URL in cui *Setup.exe* cercherà l'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]. |
| **-componentsurl=** `location` | Imposta l'URL in cui *Setup.exe* cercherà le dipendenze, ad esempio il .NET Framework. |
| **-homesite=** `true` **&#124;** `false` | Quando `true` , Scarica le dipendenze dal percorso preferito sul sito del fornitore. Questa impostazione esegue l'override dell'impostazione **-ComponentsUrl** . Quando `false` , Scarica le dipendenze dall'URL specificato da **-ComponentsUrl**. |

## <a name="operating-system-support"></a>Supporto dei sistemi operativi
 Il programma di avvio automatico di Visual Studio non è supportato in Windows Server 2008 Server Core o Windows Server 2008 R2 Server Core, poiché forniscono un ambiente server a bassa manutenzione con funzionalità limitate. Ad esempio, l'opzione di installazione dei componenti di base del server supporta solo il profilo .NET Framework 3,5 Server Core, che non è in grado di eseguire le funzionalità di Visual Studio che dipendono dalla .NET Framework completa.

## <a name="see-also"></a>Vedere anche
- [Scegliere una strategia di distribuzione ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md)
- [Sicurezza e distribuzione di ClickOnce](../deployment/clickonce-security-and-deployment.md)