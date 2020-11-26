---
title: Automazione per gli oggetti Configuration e SelectedItem | Microsoft Docs
description: Informazioni su come automatizzare la compilazione di Visual Studio e i processi degli elementi selezionati usando gli oggetti di configurazione e SelectedItem nell'interoperabilità della shell.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5bc4b23662efe688146a7266d1b061d2d9611a45
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2020
ms.locfileid: "96190070"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per oggetti Configuration e SelectedItem

È possibile automatizzare i processi di compilazione e di elementi selezionati in Visual Studio.

## <a name="automation-for-builds"></a>Automazione per le compilazioni

La compilazione o la configurazione ha un modello di automazione fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).

Se si crea un pacchetto VSPackage e si desidera controllare le opzioni di configurazione, è necessario utilizzare il modello di automazione.

## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem

Non è necessario fornire un'implementazione per l' `SelectedItem` oggetto perché Visual Studio contiene un'implementazione standard. Tuttavia, è possibile implementare l' `SelectedItem` oggetto se lo si preferisce. È necessario implementare un oggetto che contiene l' `SelectedItem` interfaccia e restituire una risposta a una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo con `VSITEMID` impostato su [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuire al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)
