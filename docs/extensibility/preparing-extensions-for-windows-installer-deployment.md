---
title: Preparazione delle estensioni per la distribuzione di Windows Installer Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702021"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparare le estensioni per la distribuzione di Windows InstallerPrepare extensions for Windows Installer deployment
Non è possibile utilizzare un pacchetto di Windows Installer (MSI) per distribuire un pacchetto VSIX. Tuttavia, è possibile estrarre il contenuto di un pacchetto VSIX per la distribuzione MSI. In questo documento viene illustrato come preparare un progetto il cui output predefinito è un pacchetto VSIX da includere in un progetto di installazione.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Preparare un progetto di estensione per la distribuzione di Windows InstallerPrepare an extension project for Windows Installer deployment
 Eseguire questi passaggi sui nuovi progetti di estensione prima di aggiungerli a un progetto di installazione.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Per preparare un progetto di estensione per la distribuzione di Windows InstallerTo prepare an extension project for Windows Installer deployment

1. Creare un VSPackage, un componente MEF, Editor Adornment o un altro tipo di progetto di estensibilità che include un manifesto VSIX.

2. Aprire il manifesto VSIX nell'editor di codice.

3. Impostare `InstalledByMsi` l'elemento del `true`manifesto VSIX su . Per ulteriori informazioni sul manifesto VSIX, vedere riferimento allo schema di [estensione VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Ciò impedisce al programma di installazione VSIX di tentare di installare il componente.

4. Fare clic con il pulsante destro del mouse sul progetto in **Esplora soluzioni** e **scegliere Proprietà**.

5. Selezionare la scheda **VSIX.**

6. Selezionare la casella **Copia contenuto VSIX nel percorso seguente** e digitare il percorso in cui il progetto di installazione preleva i file.

## <a name="extract-files-from-an-existing-vsix-package"></a>Estrarre file da un pacchetto VSIX esistenteExtract files from an existing VSIX package
 Eseguire questa procedura per aggiungere il contenuto di un pacchetto VSIX esistente a un progetto di installazione quando non si dispone dei file di origine.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Per estrarre file da un pacchetto VSIX esistenteTo extract files from an existing VSIX package

1. Rinominare il *file . VSIX* contenente l'estensione *filename.vsix* a *filename.zip*.

2. Copiare il contenuto del file *.zip* in una directory.

3. Eliminare il file *[Content_types].xml* dalla directory.

4. Modificare il manifesto VSIX, come illustrato nella procedura precedente.

5. Aggiungere i file rimanenti al progetto di installazione.

## <a name="see-also"></a>Vedere anche
- [Distribuzione del programma di installazione di Visual StudioVisual Studio installer deployment](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Procedura dettagliata: Creare un'azione personalizzataWalkthrough: Create a custom action](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
