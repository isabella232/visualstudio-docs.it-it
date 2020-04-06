---
title: Automazione per gli oggetti Configuration e SelectedItem . Documenti Microsoft
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
ms.openlocfilehash: 0341cdf56b32b8b1ac77104b3f3e813ae0610767
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709963"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per gli oggetti Configuration e SelectedItem

È possibile automatizzare i processi di compilazione e di elemento selezionati in Visual Studio.You can automate the build and selected item processes in Visual Studio.

## <a name="automation-for-builds"></a>Automazione per le compilazioni

La compilazione o la configurazione dispone <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>di un modello di automazione fornito quando si implementa . Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).

Se si crea un pacchetto VSPackage e si desidera controllare le opzioni di configurazione, è necessario utilizzare il modello di automazione.

## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem

Non è necessario fornire un'implementazione per l'oggetto `SelectedItem` perché Visual Studio contiene un'implementazione standard. Tuttavia, è `SelectedItem` possibile implementare l'oggetto, se si preferisce. È necessario implementare un `SelectedItem` oggetto che contiene l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> e `VSITEMID` restituire una risposta a una chiamata al metodo con impostato su [__VSHPROPID. VSHPROPID_ExtSelectedItem](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_ExtSelectedItem>).

## <a name="see-also"></a>Vedere anche

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>
- [Contribuire al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)
- [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)
