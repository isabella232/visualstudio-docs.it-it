---
title: Automazione per gli oggetti Configuration e SelectedItem | Microsoft Docs
description: Informazioni su come automatizzare i processi Visual Studio compilazione e degli elementi selezionati usando gli oggetti Configuration e SelectedItem nell'interoperabilità della shell.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: eac3740444d1c48a196d717e073da035f5920aec468ff216ad22ebdc6cb65918
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121359754"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per gli oggetti Configuration e SelectedItem

È possibile automatizzare i processi di compilazione e di elemento selezionati in Visual Studio.

## <a name="automation-for-builds"></a>Automazione per le compilazioni

La compilazione o la configurazione ha un modello di automazione fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).

Se si crea un VSPackage e si vogliono controllare le opzioni di configurazione, è necessario usare il modello di automazione.

## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem

Non è necessario fornire un'implementazione per l'oggetto perché Visual Studio `SelectedItem` contiene un'implementazione standard. Tuttavia, se si preferisce, è `SelectedItem` possibile implementare l'oggetto . È necessario implementare un oggetto che contiene l'interfaccia e restituire una risposta a una chiamata al metodo con `SelectedItem` <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> impostato su `VSITEMID` [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuire al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)
