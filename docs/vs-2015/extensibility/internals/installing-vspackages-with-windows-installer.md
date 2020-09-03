---
title: Installazione di VSPackage con Windows Installer | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], with Windows Installer
- VSPackages, deploying
ms.assetid: 41d2c72c-0a97-4fcd-b3aa-33a8d3aa962a
caps.latest.revision: 31
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 35942f6babf18967e11f268ef0412acb4cc8edf7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687472"
---
# <a name="installing-vspackages-with-windows-installer"></a>Installazione di pacchetti VSPackage con Windows Installer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

L'integrazione [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] di un VSPackage in richiede molto più della semplice copia dei file nel computer di un utente. Il programma di installazione del pacchetto VSPackage deve installare il pacchetto VSPackage e i relativi file dipendenti e registrarli e integrarli in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Il pacchetto VSPackage può sfruttare le funzionalità di integrazione, ad esempio la visualizzazione di un'icona nella [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] schermata iniziale e la finestra di dialogo informazioni su.  
  
 Microsoft Windows Installer file sono la soluzione consigliata per distribuire i pacchetti VSPackage. I pacchetti Windows Installer di facile utilizzo possono essere eseguiti in qualsiasi sistema operativo Windows supportato da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . Per ulteriori informazioni, vedere [Windows Installer](https://msdn.microsoft.com/121be21b-b916-43e2-8f10-8b080516d2a0).  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Nozioni di base su Windows Installer](../../extensibility/internals/windows-installer-basics.md)  
 Viene fornita una panoramica del Windows Installer.  
  
 [Scenari di installazione di pacchetti VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)  
 Vengono illustrati i diversi modi in cui è possibile supportare installazioni side-by-side di entrambi i pacchetti VSPackage e [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Creazione e modifica di un pacchetto di Windows Installer](../../extensibility/internals/authoring-a-windows-installer-package.md)  
 Viene fornita una panoramica dei passaggi tipici che i programmi di installazione seguono per installare e integrare correttamente i pacchetti VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Rilevamento dei requisiti di sistema](../../extensibility/internals/detecting-system-requirements.md)  
 Descrive in che modo un programma di installazione può rilevare [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] e i relativi componenti e annullare la configurazione se non vengono soddisfatti i requisiti del pacchetto VSPackage.  
  
 [Gestione dei componenti](../../extensibility/internals/component-management.md)  
 Viene illustrato come sviluppare un programma di installazione che manterrà l'integrità delle versioni precedenti del prodotto.  
  
 [Scelta della directory di installazione per un pacchetto VSPackage](../../extensibility/internals/choosing-the-installation-directory-for-a-vspackage.md)  
 Riepiloga le opzioni per l'individuazione dei pacchetti VSPackage.  
  
 [Registrazione di pacchetti VSPackage](../../extensibility/internals/vspackage-registration.md)  
 Viene illustrato come vengono registrate le VSPackage al momento dell'installazione e perché la registrazione automatica non è una buona idea.  
  
 [Distribuzione dei tipi di progetto](../../extensibility/internals/deploying-project-types.md)  
 Viene illustrato come utilizzare il nuovo tipo di progetto aggregator per i tipi di progetto di codice gestito.  
  
 [Procedura: Generare le informazioni del Registro di sistema per un programma di installazione](../../extensibility/internals/how-to-generate-registry-information-for-an-installer.md)  
 Viene illustrato come usare RegPkg.exe per generare un manifesto di registrazione per un pacchetto VSPackage gestito.  
  
 [Comandi da eseguire dopo l'installazione](../../extensibility/internals/commands-that-must-be-run-after-installation.md)  
 Viene illustrato come eseguire i comandi di post-installazione per integrare i pacchetti VSPackage in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [Disinstallazione di un pacchetto VSPackage con Windows Installer](../../extensibility/internals/uninstalling-a-vspackage-with-windows-installer.md)  
 Vengono descritti i passaggi che il programma di installazione deve eseguire quando gli utenti disinstallano il pacchetto VSPackage.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Installazione di VSPackage](../../misc/installing-vspackages.md)  
 Viene illustrato come compilare e installare VSPackage e come supportare gli utenti che eseguono più versioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] nello stesso momento.
