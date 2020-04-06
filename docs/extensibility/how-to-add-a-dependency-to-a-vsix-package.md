---
title: 'Procedura: aggiungere una dipendenza a un pacchetto VSIX Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711075"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: aggiungere una dipendenza a un pacchetto VSIXHow to: Add a dependency to a VSIX package

È possibile configurare una distribuzione del pacchetto VSIX che installa tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX per il file *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza

1. Aprire il file *source.extension.vsixmanifest* nella visualizzazione **Progettazione.** Passare alla scheda **Dipendenze** e fare clic su **Nuovo**.

2. Per aggiungere un'estensione installata: nella finestra di dialogo **Aggiungi nuova dipendenza** selezionare Estensione **installata** e quindi, per **Nome**, selezionare un'estensione nell'elenco.

3. Per aggiungere un altro progetto VSIX che non è installato: nella finestra di dialogo **Aggiungi nuova dipendenza** , selezionare File nel file **system** e quindi utilizzare il **pulsante Sfoglia** per selezionare il progetto VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Richiedere una versione specifica di Visual StudioRequire a specific Visual Studio release

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, dipende da una funzionalità rilasciata in 15.3, è possibile specificare il numero di build in VSIX **InstallationTarget**. Ad esempio, la versione 15.3 ha un numero di build di '15.0.26730.3'. È possibile visualizzare il mapping dei rilasci ai numeri di build [qui](../install/visual-studio-build-numbers-and-release-dates.md). Si noti che l'utilizzo del numero di versione '15.3' non funzionerà correttamente.

Se l'estensione richiede 15.3 o superiore, è necessario dichiarare la **versione InstallationTarget** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

Il VSIXInstaller rileverà le versioni precedenti di Visual Studio e informerà l'utente che è necessario un aggiornamento successivo.

## <a name="see-also"></a>Vedere anche

- [Riferimento allo schema di estensione VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparare le estensioni per la distribuzione di Windows InstallerPrepare extensions for Windows Installer deployment](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
