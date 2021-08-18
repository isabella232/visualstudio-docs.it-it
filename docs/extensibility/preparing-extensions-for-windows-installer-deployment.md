---
title: Preparazione delle estensioni per la distribuzione Windows programma di installazione | Microsoft Docs
description: Informazioni su come preparare un progetto il cui output predefinito è un pacchetto VSIX per l'inclusione in un progetto di installazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ce2dce5735fa665ff127736db2df6d7dfb53b9f2
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041607"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparare le estensioni per la Windows del programma di installazione
Non è possibile usare un pacchetto Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione MSI. Questo documento illustra come preparare un progetto il cui output predefinito è un pacchetto VSIX da includere in un progetto di installazione.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparare un progetto di estensione per la Windows del programma di installazione
 Eseguire questi passaggi sui nuovi progetti di estensione prima di aggiungerli a un progetto di installazione.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione Windows Installer

1. Creare un pacchetto VSPackage, un componente MEF, un'area di controllo dell'editor o un altro tipo di progetto di estendibilità che include un manifesto VSIX.

2. Aprire il manifesto VSIX nell'editor di codice.

3. Impostare `InstalledByMsi` l'elemento del manifesto VSIX su `true` . Per altre informazioni sul manifesto VSIX, vedere Informazioni di riferimento sullo schema dell'estensione [VSIX 2.0.](../extensibility/vsix-extension-schema-2-0-reference.md)

     In questo modo si impedisce al programma di installazione VSIX di provare a installare il componente.

4. Fare clic con il pulsante destro del mouse **sul Esplora soluzioni** e scegliere **Proprietà**.

5. Selezionare la **scheda VSIX.**

6. Selezionare la casella Copy **VSIX content to the following location** (Copia contenuto VSIX nel percorso seguente) e digitare il percorso in cui il progetto di installazione preleverà i file.

## <a name="extract-files-from-an-existing-vsix-package"></a>Estrarre file da un pacchetto VSIX esistente
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non si dispone dei file di origine.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Per estrarre file da un pacchetto VSIX esistente

1. Rinominare *. File VSIX* contenente l'estensione *da filename.vsix* *afilename.zip*.

2. Copiare il contenuto del *file.zip* in una directory.

3. Eliminare il *file [Content_types].xml* dalla directory .

4. Modificare il manifesto VSIX, come illustrato nella procedura precedente.

5. Aggiungere i file rimanenti al progetto di installazione.

## <a name="see-also"></a>Vedi anche
- [Visual Studio del programma di installazione](/previous-versions/2kt85ked(v=vs.120))
- [Procedura dettagliata: Creare un'azione personalizzata](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))