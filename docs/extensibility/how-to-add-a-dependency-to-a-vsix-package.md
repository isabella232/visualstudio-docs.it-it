---
title: 'Procedura: aggiungere una dipendenza a un pacchetto VSIX | Microsoft Docs'
description: Informazioni su come configurare una distribuzione di pacchetti VSIX che consente di installare tutte le dipendenze che non sono già presenti nel computer di destinazione.
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
ms.workload:
- vssdk
ms.openlocfilehash: 48c6ac0abd5ffb6c36dc894829e29c9304563a5e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105057403"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Procedura: aggiungere una dipendenza a un pacchetto VSIX

È possibile configurare una distribuzione di pacchetti VSIX che consente di installare tutte le dipendenze che non sono già presenti nel computer di destinazione. A tale scopo, includere le dipendenze VSIX nel file *source. Extension. vsixmanifest* .

## <a name="to-add-a-dependency"></a>Per aggiungere una dipendenza

1. Aprire il file *source. Extension. vsixmanifest* nella visualizzazione **progettazione** . Passare alla scheda **dipendenze** e fare clic su **nuovo**.

2. Per aggiungere un'estensione installata: nella finestra di dialogo **Aggiungi nuova dipendenza** selezionare **estensione installata** , quindi selezionare un'estensione nell'elenco come **nome**.

3. Per aggiungere un altro progetto VSIX non installato: nella finestra di dialogo **Aggiungi nuova dipendenza** selezionare **file in file System** e quindi usare il pulsante **Sfoglia** per selezionare il progetto VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Richiedi una versione specifica di Visual Studio

Se l'estensione richiede una versione specifica di Visual Studio 2017, ad esempio dipende da una funzionalità rilasciata in 15,3, è possibile specificare il numero di build nel **installazione** VSIX. Ad esempio, la versione 15,3 include un numero di build pari a' 15.0.26730.3'. È possibile visualizzare il mapping delle versioni per compilare i numeri [qui](../install/visual-studio-build-numbers-and-release-dates.md). Si noti che l'uso del numero di versione ' 15,3' non funzionerà correttamente.

Se l'estensione richiede 15,3 o versione successiva, dichiarare la **versione di installazione** come [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

VSIX Installer rileverà le versioni precedenti di Visual Studio e indicherà all'utente che è necessario un aggiornamento successivo.

## <a name="see-also"></a>Vedi anche

- [Riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [Anatomia di un pacchetto VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparare le estensioni per la distribuzione di Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)