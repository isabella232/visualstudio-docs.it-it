---
title: Destinazione Visual Studio 2019 durante la creazione di un'estensione in Visual Studio 2022 Preview
description: Informazioni su come fare in modo che l'estensione Visual Studio funzioni con Visual Studio 2019 se si crea il progetto con Visual Studio 2022 Preview.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
feedback_system: GitHub
ms.openlocfilehash: b6d8c21b2bb67664ceba348ef1ea9746305e3e8d
ms.sourcegitcommit: 3c5b1a1d51b521356f42a6879c1f1745573dda65
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2021
ms.locfileid: "114592229"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Destinazione di una versione precedente durante la creazione di un'estensione in Visual Studio 2022 Preview

[!INCLUDE [preview-note](../includes/preview-note.md)]

Quando si crea un nuovo progetto VSIX usando Visual Studio 2022 Preview, il progetto viene creato da un modello destinato a Visual Studio 2022. Se si vuole impostare come destinazione Visual Studio 2019 o una versione precedente, è necessario modificare il progetto creato.

È [consigliabile usare](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) i progetti condivisi Visual Studio 2019 e Visual Studio 2022 condividendo al tempo stesso la maggior parte o tutto il codice nell'estensione.

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
