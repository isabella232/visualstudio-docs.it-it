---
title: Automazione per gli oggetti Configuration e SelectedItem | Microsoft Docs
description: Informazioni su come automatizzare la compilazione Visual Studio e i processi di elementi selezionati usando gli oggetti Configuration e SelectedItem in Shell Interop.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 1a95fc06c5d84a936cdb1ada3369f584381dfe7f
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901630"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per gli oggetti Configuration e SelectedItem

È possibile automatizzare i processi di compilazione e di elemento selezionati in Visual Studio.

## <a name="automation-for-builds"></a>Automazione per le compilazioni

La compilazione o la configurazione include un modello di automazione che viene fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).

Se si crea un VSPackage e si vogliono controllare le opzioni di configurazione, è necessario usare il modello di automazione.

## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem

Non è necessario fornire un'implementazione per l'oggetto perché `SelectedItem` Visual Studio un'implementazione standard. Tuttavia, è possibile implementare `SelectedItem` l'oggetto se si preferisce. È necessario implementare un oggetto che contiene l'interfaccia e restituire una risposta a una chiamata al metodo con `SelectedItem` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> impostato su `VSITEMID` [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuire al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)
