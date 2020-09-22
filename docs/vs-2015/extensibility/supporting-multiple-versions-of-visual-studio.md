---
title: Supporto di più versioni di Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8f4393a88a689e2a923291ada37a9b6d85718db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839283"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il termine *side-by-side* significa che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per i pacchetti VSPackage, significa che un utente può avere diverse versioni di Visual Studio installate nello stesso computer. Tuttavia, non è possibile avere versioni affiancate dei pacchetti VSPackage caricati in una singola versione di Visual Studio.

 Prima di consentire il caricamento del pacchetto VSPackage in versioni affiancate di Visual Studio, tenere presente quanto segue:

- È necessario determinare quale strategia di implementazione side-by-Side si desidera seguire.

     Per altre informazioni, vedere [scelta tra VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- I formati di file di soluzione e di progetto devono adattarsi alla strategia di implementazione.

     Per ulteriori informazioni, vedere [aggiornamento di progetti personalizzati](../misc/upgrading-custom-projects.md) e [registrazione di estensioni di file per distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con versione e anche i componenti condivisi tra tutte le versioni siano installati e registrati correttamente.

     Per altre informazioni, vedere [installazione di VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).

    > [!NOTE]
    > Se si installa una versione di Visual Studio, viene installata anche una versione corrispondente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4,0 e 4,5 del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] , rispettivamente.

## <a name="in-this-section"></a>Contenuto della sezione
 [Scelta tra VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Viene illustrato come risolvere i problemi side-by-side nel pacchetto VSPackage.

 [Registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario affiancato.

## <a name="related-sections"></a>Sezioni correlate
 [Installazione di VSPackage](../misc/installing-vspackages.md) Viene illustrato come compilare e installare VSPackage e come supportare gli utenti che eseguono più versioni di Visual Studio nello stesso momento.
