---
title: Creazione di un Windows di installazione | Microsoft Docs
description: Informazioni su come creare un pacchetto di Windows Installer per Visual Studio costituito da tabelle di database contenenti dati di file e del Registro di sistema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- .msi files, VSPackages
- msi files, VSPackages
ms.assetid: 0ce7c21d-0d3f-47fe-a0bb-eed506e32609
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 9b2a279b178a7158db8bde117c3aa1e97ad2925f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126711762"
---
# <a name="author-a-windows-installer-package"></a>Creare un pacchetto Windows Installer
I dati determinano il Windows del programma di installazione. Invece di scrivere uno script procedurale per copiare file e scrivere voci del Registro di sistema, ad esempio, è possibile creare righe e colonne in tabelle di database contenenti dati di file e del Registro di sistema.

## <a name="database-entries"></a>Voci di database
Per installare un pacchetto VSPackage, un pacchetto Windows Installer deve contenere voci di database per eseguire le attività seguenti:

- Cercare nel sistema per individuare le versioni supportate dal pacchetto VSPackage (usando le tabelle del programma di installazione di Windows che includono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] AppSearch, CompLocator, RegLocator, DrLocator e Signature).

- Annullare l'installazione se non è installata alcuna versione supportata di o se non viene soddisfatto un altro requisito di sistema del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage (usando la tabella LaunchCondition).

- Installare il pacchetto VSPackage e i file dipendenti (usando le tabelle di directory, componente e file).

- Aggiungere le informazioni appropriate per il pacchetto VSPackage al Registro di sistema (usando la tabella Registry).

- Integrare il pacchetto VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **chiamandodevenv.exe /setup** (usando la tabella CustomAction).

Per altre informazioni, vedere Windows [Installer.](/windows/desktop/Msi/windows-installer-portal)

## <a name="setup-tools"></a>Strumenti di installazione
Un'ampia gamma di strumenti di installazione di terze parti offre un ambiente di sviluppo per Windows di installazione. Sono disponibili gli strumenti gratuiti seguenti:

- InstallShield Limited Edition

   È possibile ottenere una versione limitata di InstallShield tramite la finestra Visual Studio **nuova Project** installazione. Espandere **Altri Project e** quindi selezionare Installazione e **distribuzione.** Selezionare il modello InstallShield.

- Windows Set di strumenti XML del programma di installazione

   Il set Windows di strumenti WiX (Installer XML) compila i Windows installer dai file di origine XML. Il set di strumenti WiX è un progetto open source Microsoft. È possibile scaricare il codice sorgente e gli eseguibili dal set [di strumenti Wix](https://sourceforge.net/projects/wix/).

   Per i prodotti commerciali che si [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrano in tramite [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , vedere [Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

## <a name="see-also"></a>Vedi anche
- [Installare pacchetti VSPackage con il Windows di installazione](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
