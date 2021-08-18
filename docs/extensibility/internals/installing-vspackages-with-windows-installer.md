---
title: Installazione di VSPackage con Windows installer | Microsoft Docs
description: Informazioni su come usare il programma di installazione di Microsoft Windows per installare un pacchetto VSPackage e i relativi file dipendenti e registrarli e integrarli in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 57d8ea2b8ab15ebb90a0d0160a5316f1b08d1d04
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122042309"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installazione di pacchetti VSPackage con Windows Installer
L'integrazione del pacchetto VSPackage in richiede molto di più della semplice copia di file nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] computer di un utente. Il programma di installazione di VSPackage deve installare il pacchetto VSPackage e i relativi file dipendenti e registrarli e integrarli in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Il pacchetto VSPackage può sfruttare le funzionalità di integrazione, ad esempio la visualizzazione di un'icona nella schermata iniziale e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la finestra di dialogo Informazioni su.

 Microsoft Windows installer sono il modo consigliato per distribuire i pacchetti VSPackage. I pacchetti del programma di Windows di installazione possono essere eseguiti in qualsiasi Windows operativo supportato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . Per altre informazioni, vedere Windows [Installer](/previous-versions/2kt85ked(v=vs.120)).

## <a name="in-this-section"></a>Contenuto della sezione
- [Nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Fornisce una panoramica del programma di Windows installer.

- [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Vengono illustrati i diversi modi in cui è possibile supportare le installazioni side-by-side di vspackage e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Creazione e modifica di un pacchetto di Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Fornisce una panoramica dei passaggi tipici che i programmi di installazione seguono per installare e integrare correttamente i pacchetti VSPackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)

 Descrive come un programma di installazione può rilevare e i relativi componenti e annullare l'installazione se non vengono soddisfatti i requisiti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di VSPackage.

- [Gestione dei componenti](../../extensibility/internals/component-management.md)

 Viene illustrato come sviluppare un programma di installazione che manterrà l'integrità delle versioni precedenti del prodotto.

- [Scelta della directory di installazione per un pacchetto VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Riepiloga le opzioni per l'individuazione dei pacchetti VSPackage.

- [Registrazione di pacchetti VSPackage](../../extensibility/internals/vspackage-registration.md)

 Viene illustrato come registrare i pacchetti VSPackage in fase di installazione e perché la registrazione automatica non è una buona idea.

- [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)

 Viene illustrato come usare il nuovo aggregatore di tipo progetto per i tipi di progetto di codice gestito.

- [Procedura: Generare le informazioni del Registro di sistema per un programma di installazione](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Viene illustrato come usare RegPkg.exe per generare un manifesto di registrazione per un VSPackage gestito.

- [Comandi da eseguire dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Viene illustrato come eseguire comandi di post-installazione per integrare vspackage in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- [Disinstallazione di un pacchetto VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Descrive i passaggi che il programma di installazione deve eseguire quando gli utenti disinstallano il pacchetto VSPackage.