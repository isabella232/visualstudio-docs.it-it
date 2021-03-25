---
title: '&apos;Novità di Visual Studio 2017 SDK | Microsoft Docs'
description: Visual Studio SDK include funzionalità nuove e aggiornate per Visual Studio 2017, incluso il formato VSIX versione 3 aggiornato.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5a1e34ac23a0e6c298dae14c1613e7af0fc7b25d
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105061927"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novità di Visual Studio 2017 SDK&#39;

Visual Studio SDK include le seguenti funzionalità nuove e aggiornate per Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX V3

Per supportare la nuova installazione ridotta di Visual Studio 2017, il formato manifesto dell'estensione VSIX è stato aggiornato alla versione 3 (VSIX V3).

Il nuovo formato è supportato per:

* Dichiarazione esplicita dei prerequisiti che devono essere rilevati e installati da VSIX Installer.
* Assembly NGEN durante l'installazione dell'estensione.
* Installazione di asset al di fuori della normale radice dell'estensione.

Per ulteriori informazioni su queste modifiche, vedere gli argomenti seguenti:

* [Modifiche all'estendibilità per Visual Studio 2017](breaking-changes-2017.md)
* [Supporto di Ngen in VSIX v3](ngen-support.md)
* [Eseguire l'installazione all'esterno della cartella delle estensioni](set-install-root.md)
* [Domande frequenti sull'estendibilità di Visual Studio 2017](faq-2017.md)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Eseguire la migrazione del progetto di estendibilità a Visual Studio 2017

Per informazioni su come aggiornare i progetti di estendibilità e i relativi manifesti VSIX a Visual Studio 2017, vedere [procedura: eseguire la migrazione di progetti di estendibilità a Visual studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

## <a name="custom-project-and-item-templates"></a>Modelli di progetto e di elemento personalizzati

A partire da Visual Studio 2017, l'analisi dei modelli di progetto e di elemento personalizzati non verrà più eseguita. L'estensione deve invece fornire file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione utilizzando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [aggiornare i modelli di progetto e di elemento personalizzati per Visual Studio 2017](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md). Lo schema del manifesto del modello è documentato in [riferimenti allo schema del manifesto del modello di Visual Studio](../extensibility/visual-studio-template-manifest-schema-reference.md).

## <a name="updated-extension-performance-guidelines"></a>Linee guida sulle prestazioni di estensione aggiornate

Per illustrare come rilevare e analizzare l'impatto dell'estensione sui tempi di caricamento della soluzione e dell'avvio di Visual Studio, è disponibile un nuovo articolo [procedura: diagnosticare le prestazioni dell'estensione](how-to-diagnose-extension-performance.md) in [Gestisci pacchetti VSPackage](managing-vspackages.md) .
