---
title: Creazione di un pacchetto di Windows Installer | Microsoft Docs
description: Informazioni su come creare un pacchetto di Windows Installer per Visual Studio costituito da tabelle di database contenenti dati di file e del registro di sistema.
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
ms.workload:
- vssdk
ms.openlocfilehash: afc21237b72d76b73e619740cab0b196e29e928d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078955"
---
# <a name="author-a-windows-installer-package"></a>Creazione di un pacchetto di Windows Installer
I dati guidano il modello di Windows Installer. Anziché scrivere uno script procedurale per copiare file e scrivere voci del registro di sistema, ad esempio, è possibile creare righe e colonne in tabelle di database che contengono dati di file e registro di sistema.

## <a name="database-entries"></a>Voci di database
Per installare un pacchetto VSPackage, un pacchetto di Windows Installer deve contenere voci di database per eseguire le attività seguenti:

- Eseguire una ricerca nel sistema per individuare le versioni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] supportate da VSPackage (usando Windows Installer tabelle che includono AppSearch, CompLocator, RegLocator, DrLocator e Signature).

- Annullare l'installazione se non è installata alcuna versione supportata di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] o se non è stato soddisfatto un altro requisito di sistema del VSPackage (usando la tabella LaunchCondition).

- Installare il pacchetto VSPackage e i file dipendenti (usando la directory, il componente e le tabelle di file).

- Aggiungere le informazioni appropriate per il pacchetto VSPackage al registro di sistema (usando la tabella del registro di sistema).

- Integrare il pacchetto VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] chiamando **devenv.exe/Setup** (usando la tabella CustomAction).

Per ulteriori informazioni, vedere [Windows Installer](/windows/desktop/Msi/windows-installer-portal).

## <a name="setup-tools"></a>Strumenti di installazione
Un'ampia gamma di strumenti di installazione di terze parti fornisce un ambiente di sviluppo per i pacchetti Windows Installer. Sono disponibili gli strumenti gratuiti seguenti:

- InstallShield Limited Edition

   È possibile ottenere una versione limitata di InstallShield tramite la finestra di dialogo **nuovo progetto** di Visual Studio. Espandere **altri tipi di progetto** , quindi selezionare **installazione e distribuzione**. Selezionare il modello InstallShield.

- Set di strumenti XML Windows Installer

   Il set di strumenti Windows Installer XML (WiX) compila Windows Installer pacchetti dai file di origine XML. Il set di strumenti WiX è un progetto open source Microsoft. È possibile scaricare il codice sorgente e i file eseguibili dal [set di strumenti di WiX](https://sourceforge.net/projects/wix/).

   Per i prodotti commerciali che si integrano in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] utilizzando [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] , vedere [Visual Studio Marketplace](https://marketplace.visualstudio.com/).

## <a name="see-also"></a>Vedi anche
- [Installare VSPackage con Windows Installer](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
