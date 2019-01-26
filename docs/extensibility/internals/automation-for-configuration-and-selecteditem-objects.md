---
title: Automazione per la configurazione e gli oggetti SelectedItem | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60efbb25b0b5b52e1392ce84c16710a78dde7b16
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54919278"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per gli oggetti di configurazione e SelectedItem
È possibile automatizzare la compilazione e i processi di elemento selezionato in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="automation-for-builds"></a>Automazione per le compilazioni  
 Compilazione o la configurazione dispone di un modello di automazione che viene fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).  
  
 Se si crea un pacchetto VSPackage e si desidera controllare le opzioni di configurazione, è necessario usare il modello di automazione.  
  
## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem  
 Non è necessario fornire un'implementazione per il `SelectedItem` perché Visual Studio contiene un'implementazione standard dell'oggetto. Tuttavia, è possibile implementare il `SelectedItem` dell'oggetto se si preferisce. È necessario implementare un oggetto che contiene il `SelectedItem` dell'interfaccia e restituire una risposta a una chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo con `VSITEMID` impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Contribuire al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)