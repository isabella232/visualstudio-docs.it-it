---
title: Risolvere i problemi di individuazione dei modelli in Visual Studio | Microsoft Docs
ms.date: 01/02/2018
ms.topic: conceptual
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1e84ff96381fb29a1728ad43df4ff558abd17243
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689838"
---
# <a name="troubleshooting-template-installation"></a>Risoluzione dei problemi di installazione del modello

Se si verificano problemi relativi alla distribuzione dei modelli di progetto o un elemento, è possibile abilitare la registrazione diagnostica.

1. Creare un file pkgdef nella cartella Common7\IDE\CommonExtensions per l'installazione (ad esempio, C:\Program Files (x86) \Microsoft Visual Studio\2017\Enterprise\Common7\IDE\CommonExtensions\EnablePkgDefLogging.pkgdef) con il contenuto seguente:

    ```
    [$RootKey$\VsTemplate]
    "EnableTemplateDiscoveryLog"=dword:00000001
    ```

1. Aprire un "prompt dei comandi sviluppatori" per l'installazione di una ricerca in ricerca di Windows ed eseguire `devenv /updateConfiguration`.

1. Avviare Visual Studio e avviare le finestre di dialogo Nuovo progetto e nuovo elemento per inizializzare entrambi gli alberi di modello. Il log di modello viene visualizzato nel **%LOCALAPPDATA%\Microsoft\VisualStudio\15.0_[instanceid]\VsTemplateDiagnosticsList.csv** (instanceid corrisponde all'ID di installazione dell'istanza di Visual Studio). Ogni inizializzazione di struttura ad albero del modello aggiunge voci al log.

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