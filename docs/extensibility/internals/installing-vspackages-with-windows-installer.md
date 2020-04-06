---
title: Installazione di pacchetti VSPackage con Windows Installer Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2eb90dbffa9f04cd17afa70d2bdfc59205bc99cb
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707458"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installazione di pacchetti VSPackage con Windows Installer
L'integrazione del [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto VSPackage in richiede più di una semplice copia di file nel computer di un utente. Il programma di installazione del pacchetto VSPackage deve installare il pacchetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage e i relativi file dipendenti e registrarli e integrarli in . VsPackage può sfruttare le funzionalità di integrazione, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ad esempio la visualizzazione di un'icona nella schermata iniziale e la finestra di dialogo Informazioni su.

 File di Microsoft Windows Installer sono il modo consigliato per distribuire i pacchetti VSPackage. I pacchetti di Windows Installer facili da usare possono [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]essere eseguiti su qualsiasi sistema operativo Windows supportato da . Per ulteriori informazioni, vedere [Windows Installer](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0).

## <a name="in-this-section"></a>Contenuto della sezione
- [Nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md)

 Viene fornita una panoramica di Windows Installer.

- [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)

 Vengono illustrati diversi modi in cui è possibile supportare [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]le installazioni side-by-side di VSPackage e .

- [Creazione e modifica di un pacchetto di Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)

 Viene fornita una panoramica dei passaggi tipici che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]i programmi di installazione seguono per installare e integrare correttamente i package VS in .

- [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)

 Viene descritto come un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] programma di installazione può rilevare e i relativi componenti e annullare l'installazione se i requisiti DI VSPackage non vengono soddisfatti.

- [Gestione dei componenti](../../extensibility/internals/component-management.md)

 Viene illustrato come sviluppare un programma di installazione che manterrà l'integrità delle versioni precedenti del prodotto.

- [Scelta della directory di installazione per un pacchetto VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)

 Riepiloga le opzioni per l'individuazione di VSPackage.

- [Registrazione di pacchetti VSPackage](../../extensibility/internals/vspackage-registration.md)

 Viene illustrato come VSPackage vengono registrati al momento dell'installazione e perché l'autoregistrazione è una cattiva idea.

- [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)

 Viene illustrato come utilizzare il nuovo aggregatore di tipi di progetto per i tipi di progetto di codice gestito.

- [Procedura: Generare le informazioni del Registro di sistema per un programma di installazione](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)

 Viene illustrato come utilizzare RegPkg.exe per generare un manifesto di registrazione per un VSPackage gestito.

- [Comandi da eseguire dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md)

 Viene illustrato come eseguire i comandi di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]post-installazione per integrare VSPackage in .

- [Disinstallazione di un pacchetto VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)

 Descrive i passaggi che il programma di installazione deve eseguire quando gli utenti disinstallano il pacchetto VSPackage.Describes the steps your installer must perform when users uninstall your VSPackage.
