---
title: Supporto di più versioni di Visual Studio | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, supporting multiple versions
- VSPackages, side-by-side compatibility
ms.assetid: 0047aa90-1ed4-40d3-8772-622b2719a4b1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8469f89e2dd013be9760dc80c6f96ea655b80699
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66316868"
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
  > Installazione di una versione di Visual Studio installa anche una versione corrispondente del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)]. Ad esempio, l'installazione di Visual Studio 2010 e Visual Studio 2012 nello stesso computer installa anche le versioni 4.0 e 4.5 del [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], rispettivamente.

## <a name="in-this-section"></a>In questa sezione
- [Scelta tra condivise e i pacchetti VSPackage con controllo delle versioni](../extensibility/choosing-between-shared-and-versioned-vspackages.md) spiega come risolvere i problemi side-by-side nel pacchetto VSPackage.

- [La registrazione di estensioni di File per le distribuzioni Side-By-Side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md) viene descritto come il pacchetto VSPackage può registrare le associazioni di file in uno scenario side-by-side.

## <a name="related-sections"></a>Sezioni correlate
- [Installazione di pacchetti VSPackage con Windows Installer](../extensibility/internals/installing-vspackages-with-windows-installer.md)
