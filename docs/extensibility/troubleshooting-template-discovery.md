---
title: Risolvere i problemi di individuazione dei modelli in Visual Studio | Microsoft Docs
description: Informazioni su come abilitare la registrazione diagnostica per risolvere i problemi relativi alla distribuzione di progetti e modelli personalizzati nell'SDK Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: bda204e4d9b25c5eca7670494e8e1112089b0d5a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122062589"
---
# <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione dei modelli

Se si verificano problemi durante la distribuzione dei modelli di progetto o di elemento, è possibile abilitare la registrazione diagnostica.

::: moniker range="vs-2017"

1. Creare un file pkgdef nella *cartella Common7\IDE\CommonExtensions* per l'installazione. Ad esempio, *C:\Programmi (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Creare un file pkgdef nella *cartella Common7\IDE\CommonExtensions* per l'installazione. Ad esempio, *C:\Programmi (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Aggiungere quanto segue al file pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Aprire un [Prompt dei comandi per gli sviluppatori](../ide/reference/command-prompt-powershell.md) per l'installazione ed eseguire `devenv /updateConfiguration` .

::: moniker range="vs-2017"

4. Aprire Visual Studio e avviare le finestre di dialogo Nuovo Project nuovo elemento e Nuovo elemento per inizializzare entrambi gli alberi modello.

   Il log modello viene ora visualizzato in **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv(instanceid** corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione dell'albero dei modelli aggiunge voci a questo log.

::: moniker-end

::: moniker range=">=vs-2019"

4. Aprire Visual Studio e avviare le finestre di dialogo **Crea un nuovo progetto** e Nuovo **elemento** per inizializzare entrambi gli alberi dei modelli.

   Il log modello viene ora visualizzato in **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv(instanceid** corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione dell'albero dei modelli aggiunge voci a questo log.

::: moniker-end

Il file di log contiene le colonne seguenti:

- **FullPathToTemplate**, con i valori seguenti:

  - 1 per la distribuzione basata su manifesto

  - 0 per la distribuzione basata su disco

- **TemplateFileName**

- Altre proprietà del modello

> [!NOTE]
> Per disabilitare la registrazione, rimuovere il file pkgdef o modificare il valore di `EnableTemplateDiscoveryLog` in , quindi eseguire di `dword:00000000` `devenv /updateConfiguration` nuovo.

## <a name="see-also"></a>Vedi anche

- [Creazione di modelli di progetto ed elemento personalizzati](creating-custom-project-and-item-templates.md)
- [Visual Studio risoluzione dei problemi](/troubleshoot/visualstudio/welcome-visual-studio/)
