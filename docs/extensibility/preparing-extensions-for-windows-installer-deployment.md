---
title: Preparazione delle estensioni per la distribuzione di Windows Installer | Microsoft Docs
description: Informazioni su come preparare un progetto il cui output predefinito è un pacchetto VSIX da includere in un progetto di installazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 6436d05d3b15be1c1fe8d7c7bb9c8592dee091dc
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090278"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparare le estensioni per la distribuzione di Windows Installer
Non è possibile usare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione di MSI. Questo documento illustra come preparare un progetto il cui output predefinito è un pacchetto VSIX da includere in un progetto di installazione.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparare un progetto di estensione per la distribuzione di Windows Installer
 Eseguire questi passaggi nei nuovi progetti di estensione prima di aggiungere a un progetto di installazione.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows Installer

1. Creare un pacchetto VSPackage, un componente MEF, un'area di lavoro dell'editor o un altro tipo di progetto di estendibilità che include un manifesto VSIX.

2. Aprire il manifesto VSIX nell'editor di codice.

3. Impostare l' `InstalledByMsi` elemento del manifesto VSIX su `true` . Per altre informazioni sul manifesto VSIX, vedere [riferimento allo schema di estensione vsix 2,0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Ciò impedisce al programma di installazione VSIX di tentare di installare il componente.

4. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e scegliere **Proprietà**.

5. Selezionare la scheda **VSIX** .

6. Selezionare la casella **copia contenuto VSIX nel percorso seguente** e digitare il percorso in cui il progetto di installazione selezionerà i file.

## <a name="extract-files-from-an-existing-vsix-package"></a>Estrai i file da un pacchetto VSIX esistente
 Eseguire questi passaggi per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non si dispone dei file di origine.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Per estrarre i file da un pacchetto VSIX esistente

1. Rinominare il *. File VSIX* contenente l'estensione da *nomefile. vsix* a *filename.zip*.

2. Copiare il contenuto del file con *estensione zip* in una directory.

3. Eliminare il file *[Content_Types]. XML* dalla directory.

4. Modificare il manifesto VSIX, come illustrato nella procedura precedente.

5. Aggiungere i file rimanenti al progetto di installazione.

## <a name="see-also"></a>Vedi anche
- [Distribuzione del programma di installazione di Visual Studio](/previous-versions/2kt85ked(v=vs.120))
- [Procedura dettagliata: creare un'azione personalizzata](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))