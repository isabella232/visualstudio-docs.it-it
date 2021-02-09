---
title: Estensione di altre parti di Visual Studio | Microsoft Docs
description: Informazioni sulle parti dell'interfaccia utente di Visual Studio che è possibile estendere. È possibile creare un pacchetto VSPackage, scrivere nel log attività ed estendere la casella degli strumenti e la barra di stato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- user interfaces
ms.assetid: 27d2f1e1-2503-4aca-9cfc-707abd07ccf0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e21c5b8a3570b4da0cb0286d3c0d6d7c84c2f704
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895843"
---
# <a name="extend-other-parts-of-visual-studio"></a>Estendi altre parti di Visual Studio

Sono disponibili molte altre parti dell'interfaccia utente di Visual Studio che è possibile estendere. Qui ne mostreremo alcuni.

## <a name="create-a-vspackage"></a>Creare un pacchetto VSPackage

I blocchi predefiniti di base dell'estensibilità di Visual Studio sono VSPackage.  Informazioni su come aggiungere un pacchetto VSPackage: [creare un'estensione con un pacchetto VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)

## <a name="extend-the-toolbox"></a>Estensione della casella degli strumenti

Informazioni su come aggiungere nuovi controlli e altri elementi alla casella degli strumenti e come usare la funzionalità della casella degli strumenti:

- [Creare un controllo della casella degli strumenti WPF](../extensibility/creating-a-wpf-toolbox-control.md)

- [Creare un controllo della casella degli strumenti Windows Form](../extensibility/creating-a-windows-forms-toolbox-control.md)

## <a name="extend-the-status-bar"></a>Estendere la barra di stato

Informazioni su come leggere e scrivere sulla barra di stato e sull'indicatore di stato e su come fornire animazioni e altre interfacce utente: [estendere la barra di stato](../extensibility/extending-the-status-bar.md).

::: moniker range="vs-2017"

## <a name="create-custom-start-pages"></a>Crea pagine iniziali personalizzate

Informazioni su come creare una pagina iniziale, da zero o da un esempio scaricabile di pagina iniziale: [creare una pagina iniziale personalizzata](../extensibility/creating-a-custom-start-page.md).

::: moniker-end

## <a name="write-to-the-activity-log"></a>Scrivi nel log attività

Informazioni su come scrivere nel log attività: [procedura: usare il log attività](../extensibility/how-to-use-the-activity-log.md).
