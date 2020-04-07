---
title: Creazione di un pacchetto di Windows Installer Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d30c0e2b3b375e6e0efedddd3a017fbfb8646a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710031"
---
# <a name="author-a-windows-installer-package"></a>Creare un pacchetto di Windows Installer
I dati determinano il modello di Windows Installer.Data drives the Windows Installer model. Anziché scrivere uno script procedurale per copiare file e scrivere voci del Registro di sistema, ad esempio, si creano righe e colonne in tabelle di database contenenti dati di file e del Registro di sistema.

## <a name="database-entries"></a>Voci di database
Per installare un pacchetto VSPackage, un pacchetto di Windows Installer deve contenere voci di database per eseguire le attività seguenti:To install a VSPackage, a Windows Installer package must contain database entries to perform the following tasks:

- Cercare nel sistema per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] individuare le versioni dei supporti VSPackage (utilizzando le tabelle di Windows Installer che includono AppSearch, CompLocator, RegLocator, DrLocator e firma).

- Annullare l'installazione se [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non è installata alcuna versione supportata di o se non viene soddisfatto un altro requisito di sistema del pacchetto VSPackage (utilizzando la tabella LaunchCondition).

- Installare il pacchetto VSPackage e i file dipendenti (utilizzando le tabelle di directory, componenti e file).

- Aggiungere le informazioni appropriate per il pacchetto VSPackage al Registro di sistema (utilizzando la tabella del Registro di sistema).

- Integrare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage in chiamando **devenv.exe /setup** (utilizzando la tabella CustomAction).

Per ulteriori informazioni, vedere [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Strumenti di configurazione
Un'ampia gamma di strumenti di installazione di terze parti fornisce un ambiente di sviluppo per i pacchetti di Windows Installer. Sono disponibili i seguenti strumenti gratuiti:

- Edizione limitata InstallShield

   È possibile ottenere una versione limitata di InstallShield tramite la finestra di dialogo Nuovo progetto di Visual Studio.You can get a limited version of InstallShield through the Visual Studio **New Project** dialog. Espandere **Altri tipi di progetto,** quindi selezionare Installazione e **distribuzione**. Selezionare il modello InstallShield.Select the InstallShield template.

- Set di strumenti XML di Windows Installer

   Il set di strumenti XML di Windows Installer (WiX) crea pacchetti di Windows Installer dai file di origine XML. Il set di strumenti WiX è un progetto open source Microsoft.The WiX toolset is a Microsoft open-source project. È possibile scaricare il codice sorgente e gli eseguibili dal set di [strumenti Wix](https://sourceforge.net/projects/wix/).

   Per i prodotti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] commerciali che [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]si integrano utilizzando il , vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Vedere anche
- [Installare i pacchetti VSPackage con Windows InstallerInstall VSPackages With Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
