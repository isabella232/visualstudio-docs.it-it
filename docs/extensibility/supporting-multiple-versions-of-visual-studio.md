---
title: Supporto di più versioni di Visual Studio | Microsoft Docs
description: Informazioni su come supportare diverse versioni di Visual Studio, con i pacchetti VSPackage che possono essere caricati in versioni diverse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 52b8bf1be57e10790d91d4712e56d707621cc7df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889941"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
Il termine *side-by-side* significa che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per i pacchetti VSPackage, significa che un utente può avere diverse versioni di Visual Studio installate nello stesso computer. Tuttavia, non è possibile avere versioni affiancate dei pacchetti VSPackage caricati in una singola versione di Visual Studio.

 Prima di consentire il caricamento del pacchetto VSPackage in versioni affiancate di Visual Studio, tenere presente quanto segue:

- È necessario determinare quale strategia di implementazione side-by-Side si desidera seguire.

   Per altre informazioni, vedere [scelta tra VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- I formati di file di soluzione e di progetto devono adattarsi alla strategia di implementazione.

   Per ulteriori informazioni, vedere [aggiornamento di progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e [registrazione di estensioni di file per distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con versione e anche i componenti condivisi tra tutte le versioni siano installati e registrati correttamente.

   Per altre informazioni, vedere [installazione di VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) e [gestione dei componenti](../extensibility/internals/component-management.md).

  > [!NOTE]
  > L'installazione di una versione di Visual Studio installa anche una versione corrispondente del .NET Framework. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4,0 e 4,5 del .NET Framework, rispettivamente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Scelta tra VSPackage condivisi e con versione](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Viene illustrato come risolvere i problemi side-by-side nel pacchetto VSPackage.

- [Registrazione delle estensioni di file per le distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario affiancato.

## <a name="related-sections"></a>Sezioni correlate
- [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
