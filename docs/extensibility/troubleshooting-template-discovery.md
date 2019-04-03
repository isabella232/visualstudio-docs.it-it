---
title: Risolvere i problemi di individuazione dei modelli in Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a1ea74d3c5f3fed961a956e9a55a4930d009d530
ms.sourcegitcommit: d4bea2867a4f0c3b044fd334a54407c0fe87f9e8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/01/2019
ms.locfileid: "58790225"
---
# <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione del modello

Se si verificano problemi relativi alla distribuzione dei modelli di progetto o un elemento, è possibile abilitare la registrazione diagnostica.

::: moniker range="vs-2017"

1. Creare un file pkgdef nel *Common7\IDE\CommonExtensions* cartella per l'installazione. Ad esempio, *C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Creare un file pkgdef nel *Common7\IDE\CommonExtensions* cartella per l'installazione. Ad esempio, *C:\Program Files (x86) \Microsoft Visual Studio\2019\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Aggiungere quanto segue al file pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Aprire una [prompt dei comandi sviluppatore](/dotnet/framework/tools/developer-command-prompt-for-vs) per l'installazione e l'esecuzione `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Aprire Visual Studio e avviare le finestre di dialogo Nuovo progetto e nuovo elemento per inizializzare entrambi gli alberi di modello.

   Il log di modello viene visualizzato nel **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione di struttura ad albero del modello aggiunge voci al log.

::: moniker-end

::: moniker range=">=vs-2019"

4. Aprire Visual Studio e avviare il **creare un nuovo progetto** e **nuovo elemento** finestre di dialogo per l'inizializzazione sia alberi del modello.

   Il log di modello viene visualizzato nel **%LOCALAPPDATA%\Microsoft\VisualStudio\16.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione di struttura ad albero del modello aggiunge voci al log.

::: moniker-end

Il file di log contiene le colonne seguenti:

- **FullPathToTemplate**, che presenta i seguenti valori:

    - 1 per la distribuzione basata su manifesto

    - 0 per la distribuzione basata su disco

- **TemplateFileName**

- Altre proprietà del modello

> [!NOTE]
> Per disabilitare la registrazione, rimuovere il file pkgdef o modificare il valore della `EnableTemplateDiscoveryLog` al `dword:00000000`, quindi eseguire `devenv /updateConfiguration` nuovamente.

## <a name="see-also"></a>Vedere anche

- [Creazione di modelli di progetto ed elemento personalizzati](creating-custom-project-and-item-templates.md)