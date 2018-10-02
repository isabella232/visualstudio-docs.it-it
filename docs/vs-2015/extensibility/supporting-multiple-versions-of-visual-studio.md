---
title: Supporto di più versioni di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a15eb606e2415d3a6cd5cf115580c6a0d71e801
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525277"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [supporto di più versioni di Visual Studio](https://docs.microsoft.com/visualstudio/extensibility/supporting-multiple-versions-of-visual-studio).  
  
Il termine *side-by-side* significa che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per i pacchetti VSPackage, che significa che un utente può avere diverse versioni di Visual Studio installate nello stesso computer. Tuttavia, non è possibile avere versioni side-by-side del VSPackage caricati in una singola versione di Visual Studio.  
  
 Prima di eseguire il pacchetto VSPackage in grado di essere caricati in versioni side-by-side di Visual Studio, considerare quanto segue:  
  
-   È necessario determinare la strategia di implementazione side-by-side che si desidera seguire.  
  
     Per altre informazioni, vedere [scelta tra condivise e i pacchetti VSPackage con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
-   I formati di file di soluzione e progetto devono rientrare la strategia di implementazione.  
  
     Per altre informazioni, vedere [l'aggiornamento dei progetti personalizzati](../misc/upgrading-custom-projects.md) e [registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
-   Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con controllo delle versioni, nonché i componenti condivisi tra tutte le versioni, in modo corretto vengono installati e registrati.  
  
     Per altre informazioni, vedere [installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) nonché [gestione dei componenti](../extensibility/internals/component-management.md).  
  
    > [!NOTE]
    >  Installazione di una versione di Visual Studio installa anche una versione corrispondente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4.0 e 4.5 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], rispettivamente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Scelta tra pacchetti VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Viene illustrato come risolvere i problemi side-by-side nel pacchetto VSPackage.  
  
 [Registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario side-by-side.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Installazione di VSPackage](../misc/installing-vspackages.md)  
 Illustra come compilare e installare VSPackage e come supportare gli utenti che eseguono più versioni di Visual Studio contemporaneamente.

