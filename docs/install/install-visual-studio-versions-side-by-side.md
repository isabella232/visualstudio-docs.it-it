---
title: Installare versioni di Visual Studio side-by-side
description: Informazioni su come installare Visual Studio in un computer in cui è già installata una versione precedente o Visual Studio versione successiva di .
ms.custom: SEO-VS-2020
ms.date: 03/29/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.openlocfilehash: c8d1da5f8cb5c237fe02a41197825d5086fc6471
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307021"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installare versioni di Visual Studio side-by-side

È possibile installare Visual Studio in un computer in cui è già installata una versione precedente o successiva di Visual Studio.

::: moniker range="vs-2017"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2017 per aprire una soluzione creata in Visual Studio 2015, successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non siano state implementate funzionalità specifiche di Visual Studio 2017.

* Se si prova a usare Visual Studio 2017 per aprire una soluzione creata in Visual Studio 2015 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2017. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true).

::: moniker-end

::: moniker range="vs-2019"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2019 per aprire una soluzione creata in Visual Studio 2017, successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non siano state implementate funzionalità specifiche di Visual Studio 2019.

* Se si prova a usare Visual Studio 2019 per aprire una soluzione creata in Visual Studio 2017 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2019. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

::: moniker range=">=vs-2022"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2022 per aprire una soluzione creata in Visual Studio 2017 o Visual Studio 2019, è possibile aprire e modificare di nuovo la soluzione nella versione precedente, purché non siano state implementate funzionalità specifiche di Visual Studio 2022.

* Se si tenta di usare Visual Studio 2022 per aprire una soluzione creata in Visual Studio 2019 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file in modo che siano compatibili con Visual Studio 2022. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Se si disinstalla una versione di Visual Studio da un computer in cui sono installate più versioni, le associazioni di file per Visual Studio verranno rimosse per tutte le versioni.

* Visual Studio non aggiorna automaticamente le estensioni, perché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni da [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o dall'autore del software.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Installare versioni Visual Studio secondarie side-by-side

Quando si esegue l'aggiornamento da una versione secondaria di Visual Studio alla successiva, il programma di installazione di Visual Studio aggiornerà per impostazione predefinita l'installazione corrente alla versione più recente in tale canale. Si supponga, ad esempio, che sia stata appena rilasciata la versione 16.9.4. Il programma di installazione tenterà di sostituire l'installazione corrente della versione 16.9.3 (o inferiore) con la versione 16.9.4, poiché entrambe le versioni fanno parte del canale di rilascio [di Visual Studio 2019](/visualstudio/productinfo/release-rhythm). La sostituzione della versione precedente con la versione più recente durante l'aggiornamento garantisce che le versioni precedenti Visual Studio non occupano spazio nel computer. Tuttavia, in alcuni casi specifici, può essere utile installare versioni secondarie diverse di Visual Studio side-by-side. Ad esempio, è possibile avere sia 16.9.3 che 16.9.4 nello stesso computer.

::: moniker range="vs-2017"

1. Scaricare il programma di avvio automatico più recente per Visual Studio 2017 versione 15.9 dalla pagina delle versioni precedenti di [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/) per la versione che si vuole installare side-by-side con la versione esistente di Visual Studio.

1. Aprire il prompt dei comandi in modalità amministratore. A tale scopo, aprire il menu Start Windows, digitare "cmd", fare clic con il pulsante destro del mouse sul risultato della ricerca del prompt dei comandi e scegliere **Esegui come amministratore.** Nel prompt dei comandi passare alla cartella in cui si trova il Visual Studio del programma di avvio automatico.

1. Eseguire il comando seguente, specificando un nuovo percorso di cartella per il percorso di installazione e sostituendo il nome del file .exe con il nome del programma di avvio automatico appropriato per la versione di Visual Studio che si sta installando. Il .exe file deve corrispondere o essere simile a uno dei file seguenti:

   * vs_enterprise.exe per Visual Studio Enterprise
   * vs_professional.exe per Visual Studio Professional

1. Seguire le finestre di dialogo del programma di installazione per selezionare i componenti necessari per l'installazione. Per altre informazioni, vedere [Installare Visual Studio](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range="vs-2019"

1. Scaricare il file del programma di avvio automatico di Visual Studio 2019 dalla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads) o dalla pagina delle versioni di [Visual Studio 2019](/visualstudio/releases/2019/history#installing-an-earlier-release) per la versione secondaria che si vuole installare side-by-side con la versione esistente di Visual Studio.

1. Aprire il prompt dei comandi in modalità amministratore. A tale scopo, aprire il menu Start Windows, digitare "cmd", fare clic con il pulsante destro del mouse sul risultato della ricerca del prompt dei comandi e scegliere **Esegui come amministratore.** Nel prompt dei comandi passare alla cartella in cui si trova il Visual Studio del programma di avvio automatico.

1. Eseguire il comando seguente, specificando un nuovo percorso di cartella per il percorso di installazione e sostituendo il nome del file .exe con il nome del programma di avvio automatico appropriato per la versione di Visual Studio che si sta installando. Il .exe file deve corrispondere o essere simile a uno dei file seguenti:

   * vs_enterprise.exe per Visual Studio Enterprise
   * vs_professional.exe per Visual Studio Professional
   * vs_community.exe per Visual Studio Community

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Seguire le finestre di dialogo del programma di installazione per selezionare i componenti necessari per l'installazione. Per altre informazioni, vedere [Installare Visual Studio](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range=">=vs-2022"

1. Scaricare il file del programma di avvio automatico di Visual Studio 2022 dalla pagina dei download di [Visual Studio](https://visualstudio.microsoft.com/downloads) o dalla pagina delle versioni di [Visual Studio 2022](/visualstudio/releases/2022/history) per la versione secondaria che si vuole installare side-by-side con la versione esistente di Visual Studio.

1. Aprire il prompt dei comandi in modalità amministratore. A tale scopo, aprire il menu Start Windows, digitare "cmd", fare clic con il pulsante destro del mouse sul risultato della ricerca del prompt dei comandi e scegliere **Esegui come amministratore.** Nel prompt dei comandi passare alla cartella in cui si trova il Visual Studio del programma di avvio automatico.

1. Eseguire il comando seguente, specificando un nuovo percorso di cartella per il percorso di installazione e sostituendo il nome del file .exe con il nome del programma di avvio automatico appropriato per la versione di Visual Studio che si sta installando. Il .exe file deve corrispondere o essere simile a uno dei file seguenti:

   * vs_enterprise.exe per Visual Studio Enterprise
   * vs_professional.exe per Visual Studio Professional
   * vs_community.exe per Visual Studio Community

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Seguire le finestre di dialogo del programma di installazione per selezionare i componenti necessari per l'installazione. Per altre informazioni, vedere [Installare Visual Studio](install-visual-studio.md#step-4---choose-workloads).
   
::: moniker-end

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versioni di .NET Framework e installazioni side-by-side

I progetti Visual Basic, Visual C# e Visual F# usano l'opzione **Framework di destinazione** in **Creazione progetti** per specificare la versione di .NET Framework che un progetto usa. Per un progetto C++ è possibile modificare manualmente il framework di destinazione modificando il file con estensione vcxproj. Per altre informazioni, vedere la pagina [Compatibilità tra le versioni in .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Quando si crea un progetto, è possibile specificare a quale versione di .NET Framework è destinato il progetto nell'elenco **.NET Framework** della finestra di dialogo **Nuovo progetto** .

Per informazioni specifiche del linguaggio, vedere l'argomento corrispondente nella tabella seguente.

::: moniker range="vs-2017"

| Lingua     | Argomento                                                                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C#    | [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true)                 |
| Visual F#    | [Sviluppare con F# in Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true)                                               |
| C++          | [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/)                         |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Lingua     | Argomento                                                                                                                           |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)         |
| Visual C#    | [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md)                         |
| Visual F#    | [Sviluppare con F# in Visual Studio](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Installa Visual Studio](install-visual-studio.md)
* [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
