---
title: '&#39;Novità di Visual Studio 2017 in Visual Studio 2017 SDK Documenti Microsoft'
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 88330aa68f2a3752431fd2fbe6c5c1c649acbb8b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697203"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>&#39;Novità di Visual Studio 2017 SDK

Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Per supportare la nuova installazione leggera di Visual Studio 2017, il formato del manifesto dell'estensione VSIX è stato aggiornato alla versione 3 (VSIX v3).

Il nuovo formato supporta:

* Dichiarando in modo esplicito i prerequisiti per essere rilevati e installati dal VSIXInstaller.
* Assembly Ngen durante l'installazione dell'estensione.
* Installazione di risorse al di fuori della radice di estensione usuale.

Per informazioni su queste modifiche, vedere gli argomenti seguenti:To learn about these changes, see the following topics:

* [Modifiche all'estensibilità per Visual Studio 2017Changes to extensibility for Visual Studio 2017](breaking-changes-2017.md)
* [Supporto di Ngen in VSIX v3](ngen-support.md)
* [Eseguire l'installazione all'esterno della cartella delle estensioni](set-install-root.md)
* [Domande frequenti sull'estendibilità di Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Eseguire la migrazione del progetto di estendibilità a Visual Studio 2017Migrate extensibility project to Visual Studio 2017

Per informazioni su come aggiornare i progetti di estensibilità e i relativi manifesti VSIX in Visual Studio 2017, vedere procedura: eseguire la migrazione di progetti di [estensibilità a Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modelli di progetto ed elemento personalizzati

A partire da Visual Studio 2017, l'analisi dei modelli di progetto ed elemento personalizzati non verrà più eseguita. Al contrario, l'estensione deve fornire i file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione utilizzando un file MSI, è necessario generare manualmente i file manifesto del modello. Per ulteriori informazioni, vedere Aggiornare modelli di [progetto ed elemento personalizzati per Visual Studio 2017.](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) Lo schema del manifesto del modello è documentato in [Riferimento allo schema del manifesto del modello](../extensibility/visual-studio-template-manifest-schema-reference.md)di Visual Studio .

## <a name="updated-extension-performance-guidelines"></a>Linee guida aggiornate sulle prestazioni delle estensioni

È disponibile un nuovo [articolo Procedura: Diagnosticare le prestazioni dell'estensione](how-to-diagnose-extension-performance.md) in Gestire i pacchetti VSPackage per illustrare come rilevare e analizzare l'impatto dell'estensione sui tempi di avvio e caricamento della soluzione di Visual Studio.There is a new How to: Diagnostic extension performance article under [Manage VSPackages](managing-vspackages.md) to show how to detect and analyze extension impact on Visual Studio startup and solution load times.
