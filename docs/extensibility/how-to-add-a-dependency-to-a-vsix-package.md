---
title: 'Procedura: Aggiungere una dipendenza a un pacchetto VSIX | Microsoft Docs'
description: Informazioni su come configurare una distribuzione di pacchetti VSIX che installa tutte le dipendenze che non sono già presenti nel computer di destinazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0335e243fe0779060282cecdc58ad9deb608c948
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050416"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: Aggiungere una dipendenza a un pacchetto VSIX

È possibile configurare una distribuzione di pacchetti VSIX che installa tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX nel file *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza

1. Aprire il file *source.extension.vsixmanifest* nella **visualizzazione** Progettazione. Passare alla scheda **Dipendenze** e fare clic su **Nuovo.**

2. Per aggiungere un'estensione  installata: nella finestra di  dialogo Aggiungi nuova dipendenza selezionare Estensione installata e quindi, per **Nome**, selezionare un'estensione nell'elenco.

3. Per aggiungere un altro vsix non  installato: nella finestra di dialogo Aggiungi nuova dipendenza  selezionare **File in file system** e quindi usare il pulsante Sfoglia per selezionare vsix.

## <a name="require-a-specific-visual-studio-release"></a>Richiedere una versione Visual Studio specifica

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio, dipende da una funzionalità rilasciata nella versione 15.3, è possibile specificare il numero di build in VSIX **InstallationTarget.** Ad esempio, la versione 15.3 ha un numero di build "15.0.26730.3". È possibile visualizzare il mapping delle versioni ai numeri di build [qui.](../install/visual-studio-build-numbers-and-release-dates.md) Si noti che l'uso del numero di versione '15.3' non funzionerà correttamente.

Se l'estensione richiede la versione 15.3 o successiva, è necessario dichiarare **InstallationTarget Version** come [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIXInstaller rileverà le versioni precedenti Visual Studio e informerà l'utente che è necessario un aggiornamento successivo.

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sullo schema dell'estensione VSIX 1.0](/previous-versions/dd393700(v=vs.110))
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparare le estensioni per la Windows del programma di installazione](../extensibility/preparing-extensions-for-windows-installer-deployment.md)