---
title: Risolvere i problemi di individuazione dei modelli in Visual Studio | Microsoft Docs
description: Informazioni su come abilitare la registrazione diagnostica per risolvere i problemi di distribuzione di progetti e modelli personalizzati in Visual Studio SDK.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1ea99c1d74c06ab42ff86f07de4cf5c76e95de43
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102151324"
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

3. Aprire un [prompt dei comandi per gli sviluppatori](../ide/reference/command-prompt-powershell.md) per l'installazione ed eseguire `devenv /updateConfiguration` .

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

## <a name="see-also"></a>Vedi anche

- [Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)
- [Risoluzione dei problemi di Visual Studio](/troubleshoot/visualstudio/welcome-visual-studio/)
