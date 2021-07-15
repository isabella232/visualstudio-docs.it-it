---
title: Novità &apos; di Visual Studio 2017 SDK | Microsoft Docs
description: In Visual Studio SDK sono disponibili funzionalità nuove e aggiornate per Visual Studio 2017, incluso il formato VSIX versione 3 aggiornato.
ms.custom: SEO-VS-2020
ms.date: 10/31/2017
ms.topic: conceptual
ms.assetid: 9efcf0a3-dbde-4cab-8ed3-425826a48b2e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 0b0b7852fa7e20f4ee6951e57c5c19f4b5454028
ms.sourcegitcommit: 3c6c263a1c0b20f084290ce45295a46027da33b6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/14/2021
ms.locfileid: "113756894"
---
# <a name="what39s-new-in-the-visual-studio-2017-sdk"></a>Novità&#39;sdk Visual Studio 2017

L Visual Studio SDK include le funzionalità nuove e aggiornate seguenti per Visual Studio 2017.

## <a name="vsix-v3-format"></a>Formato VSIX v3

Per supportare la nuova installazione leggera di Visual Studio 2017, il formato del manifesto dell'estensione VSIX è stato aggiornato alla versione 3 (VSIX v3).

Il nuovo formato include il supporto per:

* Dichiarazione esplicita dei prerequisiti che devono essere rilevati e installati da VSIXInstaller.
* Assembly Ngen durante l'installazione dell'estensione.
* Installazione di asset al di fuori della normale radice dell'estensione.

Per informazioni su queste modifiche, vedere gli argomenti seguenti:

* [Modifiche all'estendibilità per Visual Studio 2017](breaking-changes-2017.md)
* [Supporto di Ngen in VSIX v3](ngen-support.md)
* [Eseguire l'installazione all'esterno della cartella delle estensioni](set-install-root.md)
* [Domande frequenti sull'estendibilità Visual Studio 2017](faq-2017.yml)

## <a name="migrate-extensibility-project-to-visual-studio-2017"></a>Eseguire la migrazione di un progetto di estendibilità Visual Studio 2017

Per informazioni su come aggiornare i progetti di estendibilità e i relativi manifesti VSIX a Visual Studio 2017, vedere Procedura: Eseguire la migrazione di progetti di estendibilità [a Visual Studio 2017.](how-to-migrate-extensibility-projects-to-visual-studio-2017.md)

## <a name="custom-project-and-item-templates"></a>Modelli di progetto ed elemento personalizzati

A partire Visual Studio 2017, l'analisi dei modelli di progetto ed elemento personalizzati non verrà più eseguita. Al contrario, l'estensione deve fornire file manifesto del modello che descrivono il percorso di installazione di questi modelli. È possibile usare Visual Studio 2017 per aggiornare le estensioni VSIX. Se si distribuisce l'estensione usando un file MSI, è necessario generare manualmente i file manifesto del modello. Per altre informazioni, vedere [Aggiornare modelli di progetto ed elemento personalizzati per Visual Studio 2017.](../extensibility/upgrading-custom-project-and-item-templates-for-visual-studio-2017.md) Lo schema del manifesto del modello è documentato nell'Visual Studio [dello schema del manifesto del modello.](../extensibility/visual-studio-template-manifest-schema-reference.md)

## <a name="updated-extension-performance-guidelines"></a>Linee guida aggiornate sulle prestazioni delle estensioni

È disponibile un nuovo articolo [Procedura:](how-to-diagnose-extension-performance.md) Diagnosticare le prestazioni dell'estensione in Gestire i pacchetti [VSPackage](managing-vspackages.md) per illustrare come rilevare e analizzare l'impatto dell'estensione sui tempi di Visual Studio avvio e caricamento della soluzione.
