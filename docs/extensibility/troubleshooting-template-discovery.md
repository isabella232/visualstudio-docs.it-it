---
title: Risolvere i problemi relativi all'individuazione dei modelli in Visual Studio . Documenti Microsoft
ms.date: 01/02/2018
ms.topic: conceptual
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 078d06c797c3b228c1ea5b1d836dceb0394b3174
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698930"
---
# <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi relativi all'installazione dei modelli

Se si verificano problemi durante la distribuzione dei modelli di progetto o di elemento, è possibile abilitare la registrazione diagnostica.

::: moniker range="vs-2017"

1. Creare un file pkgdef nella cartella *Common7, IDE, CommonExtensions* per l'installazione. Ad esempio, *C:, Programmi (x86) Microsoft Visual Studio 2017 Enterprise Common7 IDE CommonExtensions , EnablePkgDefLogging.pkgdef*.

::: moniker-end

::: moniker range=">=vs-2019"

1. Creare un file pkgdef nella cartella *Common7, IDE, CommonExtensions* per l'installazione. Ad esempio, *C:, Programmi (x86) Microsoft Visual Studio 2019 , Enterprise , Common7 , IDE , CommonExtensions , EnablePkgDefLogging.pkgdef*.

::: moniker-end

2. Aggiungere quanto segue al file pkgdef:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

3. Aprire un [prompt dei comandi per gli sviluppatori](/dotnet/framework/tools/developer-command-prompt-for-vs) per l'installazione ed eseguire `devenv /updateConfiguration`.

::: moniker range="vs-2017"

4. Aprire Visual Studio e avviare le finestre di dialogo Nuovo progetto e Nuovo elemento per inizializzare entrambe le strutture ad albero modello.

   Il log del modello viene ora visualizzato in **%LOCALAPPDATA% , Microsoft , Microsoft , VisualStudio , 15.0_[instanceid] , VsTemplateDiagnosticsList.csv** (instanceid corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione dell'albero del modello aggiunge voci a questo log.

::: moniker-end

::: moniker range=">=vs-2019"

4. Aprire Visual Studio e avviare le finestre di dialogo **Crea un nuovo progetto** e Nuovo **elemento** per inizializzare entrambi gli alberi modello.

   Il log del modello viene ora visualizzato in **%LOCALAPPDATA% , Microsoft , Microsoft , VisualStudio , 16.0_[instanceid] , VsTemplateDiagnosticsList.csv** (instanceid corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione dell'albero del modello aggiunge voci a questo log.

::: moniker-end

Il file di registro contiene le seguenti colonne:

- **FullPathToTemplate**, che ha i seguenti valori:

  - 1 per la distribuzione basata su manifesto

  - 0 per la distribuzione basata su disco

- **NomeFileModello**

- Altre proprietà del modello

> [!NOTE]
> Per disabilitare la registrazione, rimuovere il file pkgdef oppure modificare il valore di `EnableTemplateDiscoveryLog` in `dword:00000000`, quindi eseguire `devenv /updateConfiguration` di nuovo.

## <a name="see-also"></a>Vedere anche

- [Creazione di modelli di progetto e di elemento personalizzati](creating-custom-project-and-item-templates.md)
