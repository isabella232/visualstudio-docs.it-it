---
title: Supporto di più versioni di Visual Studio | Microsoft Docs
description: Informazioni su come supportare diverse versioni di Visual Studio, con i pacchetti VSPackage in grado di caricare in versioni diverse.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 7aa8659754091106cc3f87f13c2e58a14d6b525d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137483"
---
# <a name="supporting-multiple-versions-of-visual-studio"></a>Supporto di più versioni di Visual Studio
Il termine *side-by-side* indica che è possibile installare e gestire più versioni di un prodotto nello stesso computer. Per i pacchetti VSPackage, questo significa che un utente può avere diverse Visual Studio installate nello stesso computer. Tuttavia, non è possibile avere versioni side-by-side dei pacchetti VSPackage caricati in una singola versione di Visual Studio.

 Prima di rendere il vspackage in grado di essere caricato in versioni side-by-side di Visual Studio, tenere presente quanto segue:

- È necessario determinare quale strategia di implementazione side-by-side si vuole seguire.

   Per altre informazioni, vedere [Scelta tra vspackage condivisi e con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md).

- I formati di file di soluzione e di progetto devono essere adatti alla strategia di implementazione.

   Per altre informazioni, vedere [Aggiornamento di progetti personalizzati](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects) e Registrazione di estensioni di file per [distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Il programma di installazione deve gestire la strategia di implementazione in modo che i componenti con controllo delle versioni, oltre ai componenti condivisi tra tutte le versioni, vengano installati e registrati correttamente.

   Per altre informazioni, vedere [Installing VSPackages With Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md) and also [Component Management](../extensibility/internals/component-management.md).

  > [!NOTE]
  > L'installazione di una Visual Studio installa anche una versione corrispondente del .NET Framework. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4.0 e 4.5 del .NET Framework, rispettivamente.

## <a name="in-this-section"></a>Contenuto della sezione
- [Scelta tra vspackage condivisi e con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md) Viene illustrato come risolvere i problemi side-by-side nel pacchetto VSPackage.

- [Registrazione di estensioni di file per distribuzioni side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) Viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario side-by-side.

## <a name="related-sections"></a>Sezioni correlate
- [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
