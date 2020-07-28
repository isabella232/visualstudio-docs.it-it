---
title: Risolvere i problemi di individuazione dei modelli in Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 89ff5b9974f20841378f367c3cb631a8d4cf7787
ms.sourcegitcommit: 9a7fb8556a5f3dbb4459122fefc7e7a8dfda753a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/27/2020
ms.locfileid: "87235043"
---
# <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione del modello

Se si verificano problemi durante la distribuzione dei modelli di progetto o di elemento, è possibile abilitare la registrazione diagnostica.

::: moniker range="vs-2017"

1. Creare un file pkgdef nella cartella *Common7\IDE\CommonExtensions* per l'installazione. Ad esempio *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Creare un file pkgdef nella cartella *Common7\IDE\CommonExtensions* per l'installazione. Ad esempio *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Aggiungere il codice seguente al file pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Aprire un [prompt dei comandi per gli sviluppatori](/dotnet/framework/tools/developer-command-prompt-for-vs) per l'installazione ed eseguire `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Aprire Visual Studio e avviare le finestre di dialogo nuovo progetto e nuovo elemento per inizializzare entrambi gli alberi del modello.

   Il log del modello viene ora visualizzato in **%LocalAppData%\Microsoft\VisualStudio\15.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione dell'albero del modello aggiunge voci a questo log.

::: moniker-end

::: moniker range=">=vs-2019"

4. Aprire Visual Studio e avviare le finestre di dialogo **Crea un nuovo progetto** e **nuovo elemento** per inizializzare entrambi gli alberi del modello.

   Il log del modello viene ora visualizzato in **%LocalAppData%\Microsoft\VisualStudio\16.0_ [InstanceId] \VsTemplateDiagnosticsList.csv** (InstanceId corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione dell'albero del modello aggiunge voci a questo log.

::: moniker-end

Il file di log contiene le colonne seguenti:

- **FullPathToTemplate**, con i valori seguenti:

  - 1 per la distribuzione basata su manifesto

  - 0 per la distribuzione basata su disco

- **TemplateFileName**

- Altre proprietà del modello

> [!NOTE]
> Per disabilitare la registrazione, rimuovere il file pkgdef o modificare il valore di `EnableTemplateDiscoveryLog` in `dword:00000000` , quindi eseguire di `devenv /updateConfiguration` nuovo l'operazione.

## <a name="see-also"></a>Vedere anche

- [Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)
- [Risoluzione dei problemi di Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
