---
title: Installare versioni di Visual Studio side-by-side
ms.date: 07/24/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 1a57d124029f5c654d41dcea621d6df95e29842f
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211313"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Installare versioni di Visual Studio side-by-side

È possibile installare Visual Studio in un computer in cui è già installata una versione precedente o successiva di Visual Studio.

::: moniker range="vs-2017"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2017 per aprire una soluzione creata in Visual Studio 2015, successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non siano state implementate funzionalità specifiche di Visual Studio 2017.

* Se si prova a usare Visual Studio 2017 per aprire una soluzione creata in Visual Studio 2015 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2017. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true).

::: moniker-end

::: moniker range=">= vs-2019"

Prima di installare le versioni side-by-side, verificare le condizioni seguenti:

* Se si usa Visual Studio 2019 per aprire una soluzione creata in Visual Studio 2017, successivamente è possibile aprire e modificare nuovamente la soluzione nella versione precedente purché non siano state implementate funzionalità specifiche di Visual Studio 2019.

* Se si prova a usare Visual Studio 2019 per aprire una soluzione creata in Visual Studio 2017 o in una versione precedente, potrebbe essere necessario modificare i progetti e i file per renderli compatibili con Visual Studio 2019. Per altre informazioni vedere la pagina [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md).

::: moniker-end

* Se si disinstalla una versione di Visual Studio da un computer in cui sono installate più versioni, le associazioni di file per Visual Studio verranno rimosse per tutte le versioni.

* Visual Studio non aggiorna automaticamente le estensioni, perché non tutte le estensioni sono compatibili. È necessario reinstallare le estensioni da [Visual Studio Marketplace](https://marketplace.visualstudio.com/) o dall'autore del software.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Installare versioni secondarie di Visual Studio side-by-side

Quando si esegue l'aggiornamento da una versione secondaria di Visual Studio alla successiva, il programma di installazione di Visual Studio aggiornerà l'installazione corrente alla versione successiva nel canale per impostazione predefinita. Ad esempio, quando si installa l'anteprima di 16.6.4, il programma di installazione tenterà di sostituire l'installazione corrente di 16.6.3 Preview, perché entrambe le versioni si trovano nel canale 16,6 Preview. Ciò garantisce che le versioni precedenti di Visual Studio non stiano occupando spazio sul computer. In alcuni casi specifici, può essere utile installare le versioni secondarie side-by-side. In questo esempio, ciò significherebbe avere sia 16.6.3 che 16.6.4 nello stesso computer.

1. Scaricare il [file del programma di avvio automatico di Visual Studio](/visualstudio/releases/2019/history#installing-an-earlier-release) per la versione secondaria di cui si vuole eseguire l'installazione side-by-side con le versioni esistenti di Visual Studio.
2. Aprire il prompt dei comandi in modalità amministratore. A tale scopo, aprire il menu Start di Windows, digitare "cmd", fare clic con il pulsante destro del mouse sul risultato della ricerca del prompt dei comandi e selezionare **Esegui come amministratore**. Nel prompt dei comandi passare alla directory in cui si trova il file del programma di avvio automatico di Visual Studio.
3. Eseguire il comando seguente, specificando un nuovo percorso di cartella per il percorso di installazione e sostituendo il nome del file con estensione exe con il nome del programma di avvio automatico appropriato per la versione di Visual Studio che si sta installando. Il nome del file con estensione exe deve corrispondere o essere simile a uno dei file seguenti:
   * vs_community.exe per Visual Studio Community
   * vs_professional.exe per Visual Studio Professional
   * vs_enterprise.exe per Visual Studio Enterprise

   ```
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<2019 AddNewPath>"
   ```

4. Seguire le finestre di dialogo del programma di installazione per selezionare i componenti necessari per l'installazione. Per altre informazioni, vedere [installare Visual Studio](install-visual-studio.md#step-4---choose-workloads).

## <a name="net-framework-versions-and-side-by-side-installations"></a>Versioni di .NET Framework e installazioni side-by-side

I progetti Visual Basic, Visual C# e Visual F# usano l'opzione **Framework di destinazione** in **Creazione progetti** per specificare la versione di .NET Framework che un progetto usa. Per un progetto C++ è possibile modificare manualmente il framework di destinazione modificando il file con estensione vcxproj. Per altre informazioni, vedere la pagina [Compatibilità tra le versioni in .NET Framework](/dotnet/framework/migration-guide/version-compatibility).

Quando si crea un progetto, è possibile specificare a quale versione di .NET Framework è destinato il progetto nell'elenco **.NET Framework** della finestra di dialogo **Nuovo progetto** .

Per informazioni specifiche del linguaggio, vedere l'argomento corrispondente nella tabella seguente.

::: moniker range="vs-2017"

| Linguaggio | Argomento |
|--------------|-----------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C# | [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true) |
| Visual F# | [Sviluppare con F# in Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true) |
|C++ | [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installa Visual Studio](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Linguaggio | Argomento |
|--------------|-----------|
| Visual Basic | [Application Page, Project Designer (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Applicazione (pagina), Creazione progetti (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Sviluppare con F# in Visual Studio](../ide/fsharp-visual-studio.md) |
| C++ | [Procedura: Modificare il framework di destinazione e il set di strumenti della piattaforma](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Installa Visual Studio](install-visual-studio.md)
* [Trasferire, migrare e aggiornare progetti di Visual Studio](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [Compilazione di applicazioni isolate C/C++ e di assembly side-by-side](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end