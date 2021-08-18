---
title: Destinazione Visual Studio 2019 durante la creazione di un'estensione in Visual Studio 2022 Preview
description: Informazioni su come fare in modo che l'estensione Visual Studio funzioni con Visual Studio 2019 se si crea il progetto con Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: b7509e53108d9b33570c92f6d6bedb8f200a1fe6
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086404"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Destinazione di una versione precedente durante la creazione di un'estensione in Visual Studio 2022 Preview

[!INCLUDE [preview-note](../includes/preview-note.md)]

Quando si crea un nuovo progetto VSIX usando Visual Studio 2022 Preview, il progetto viene creato da un modello destinato a Visual Studio 2022. Se si vuole impostare come destinazione Visual Studio 2019 o una versione precedente, è necessario modificare il progetto creato.

È [consigliabile usare](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) progetti condivisi per Visual Studio 2019 e Visual Studio 2022 condividendo al tempo stesso la maggior parte o tutto il codice nell'estensione.

Seguire questa procedura nel progetto VSIX che deve essere Visual Studio 2019:

1. Modificare il `source.extension.vsixmanifest` file per rimuovere `ProductArchitecture` l'elemento e l'intervallo di versioni:

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   Aggiornare anche il prerequisito:

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    Esaminare il file per eventuali altri aggiornamenti che potrebbero essere necessari.

1. Modificare le versioni dei pacchetti VS SDK a cui si fa riferimento nel file di progetto:

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
