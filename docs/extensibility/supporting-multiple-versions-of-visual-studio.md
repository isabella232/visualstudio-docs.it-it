---
title: Supporto di più versioni di Visual Studio Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d571f1be4da45ff5ed6b2538cfb515930bde1de
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699480"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
Il termine *side-by-side* significa che è possibile installare e gestire più versioni di un prodotto sullo stesso computer. Per i package VS, ciò significa che un utente può avere diverse versioni di Visual Studio installate nello stesso computer. Tuttavia, non è possibile avere versioni side-by-side dei pacchetti VSPackage caricati in una singola versione di Visual Studio.

 Prima di rendere il pacchetto VSPackage in grado di essere caricato in versioni side-by-side di Visual Studio, considerare quanto segue:

- È necessario determinare quale strategia di implementazione side-by-side si desidera seguire.

   Per ulteriori informazioni, vedere [Scelta tra package VS condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- I formati di file di soluzione e di progetto devono essere adatti alla strategia di implementazione.

   Per ulteriori informazioni, vedere [Aggiornamento di progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e Registrazione delle estensioni di file per [distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con controllo delle versioni e anche i componenti condivisi tra tutte le versioni vengano installati e registrati correttamente.

   Per ulteriori informazioni, vedere [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e anche Gestione [componenti](../extensibility/internals/component-management.md).

  > [!NOTE]
  > L'installazione di una versione di Visual Studio consente inoltre di installare una versione corrispondente di .NET Framework. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4.0 e 4.5 di .NET Framework, rispettivamente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Scelta tra package VS condivisi e con versioneChoosing Between Shared and Concono](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Viene illustrato come risolvere i problemi side-by-side nel pacchetto VSPackage.

- [Registrazione delle estensioni di file per le distribuzioni side-by-sideRegistering File Name Extensions for Side-By-Side Deployments](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Descrive come il pacchetto VSPackage può registrare le associazioni di file in uno scenario side-by-side.

## <a name="related-sections"></a>Sezioni correlate
- [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
