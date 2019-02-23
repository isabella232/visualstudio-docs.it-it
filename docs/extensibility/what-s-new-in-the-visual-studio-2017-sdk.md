---
title: Cosa&#39;novità di Visual Studio 2017 SDK s | Microsoft Docs
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e3d149a7cec711e59909ff21944ed52e3c074113
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710175"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Cosa&#39;s novità di Visual Studio 2017 SDK

Visual Studio SDK ha le seguenti funzionalità nuove e aggiornate per Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Per supportare la nuova installazione leggera di Visual Studio 2017, il formato del manifesto di estensione VSIX è stato aggiornato alla versione 3 (VSIX v3).

Il nuovo formato offre supporto per:

* Dichiarare in modo esplicito i prerequisiti per essere rilevati e installati per il VSIX Installer.
* Assembly Ngen in installazione dell'estensione.
* Installazione di risorse all'esterno di radice dell'estensione normali.

Per altre informazioni su queste modifiche, vedere gli argomenti seguenti:

* [Modifiche apportate all'estendibilità per 2017](breaking-changes-2017.md)
* [Supporto di Ngen in VSIX v3](ngen-support.md)
* [Installare all'esterno della cartella delle estensioni](set-install-root.md)
* [Domande frequenti sulle estendibilità di Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017

Per informazioni su come aggiornare i progetti di estendibilità e i manifesti VSIX a Visual Studio 2017, vedere [come: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modelli di progetto ed elemento personalizzati

A partire da Visual Studio 2017, l'analisi per progetto personalizzato e i modelli di elemento verrà non sarà più eseguita. Al contrario, l'estensione deve fornire i file manifesto che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [aggiornare i modelli di progetto ed elemento personalizzati per Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Schema del modello di manifesto è documentato in [riferimenti dello schema del manifesto dei modelli di Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Linee guida sulle prestazioni di estensione aggiornato

C'è un nuovo [come: Diagnosticare le prestazioni delle estensioni](how-to-diagnose-extension-performance.md) sotto l'articolo [gestire i pacchetti VSPackage](managing-vspackages.md) per mostrare come rilevare e analizzare l'impatto di estensione in Visual Studio avvio e soluzione tempi di caricamento.
