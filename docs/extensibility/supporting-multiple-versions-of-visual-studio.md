---
title: Supporto di più versioni di Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3837116a33dc5608f75e48e3397273f65e5ea260
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49817990"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
Il termine *side-by-side* significa che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per i pacchetti VSPackage, che significa che un utente può avere diverse versioni di Visual Studio installate nello stesso computer. Tuttavia, non è possibile avere versioni side-by-side del VSPackage caricati in una singola versione di Visual Studio.  
  
 Prima di eseguire il pacchetto VSPackage in grado di essere caricati in versioni side-by-side di Visual Studio, considerare quanto segue:  
  
- È necessario determinare la strategia di implementazione side-by-side che si desidera seguire.  
  
   Per altre informazioni, vedere [scelta tra condivise e i pacchetti VSPackage con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md).  
  
- I formati di file di soluzione e progetto devono rientrare la strategia di implementazione.  
  
   Per altre informazioni, vedere [l'aggiornamento dei progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e [registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).  
  
- Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con controllo delle versioni, nonché i componenti condivisi tra tutte le versioni, in modo corretto vengono installati e registrati.  
  
   Per altre informazioni, vedere [installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) nonché [gestione dei componenti](../extensibility/internals/component-management.md).  
  
  > [!NOTE]
  >  Installazione di una versione di Visual Studio installa anche una versione corrispondente del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4.0 e 4.5 del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], rispettivamente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Scelta tra pacchetti VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md)  
 Viene illustrato come risolvere i problemi side-by-side nel pacchetto VSPackage.  
  
 [Registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md)  
 Viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario side-by-side.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)  
