---
title: Automazione per la configurazione e gli oggetti SelectedItem | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42faf8127c1ab70d3470aa497a0cdab6058060f8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68157255"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per la configurazione e per gli oggetti SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È possibile automatizzare la compilazione e i processi di elemento selezionato in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
## <a name="automation-for-builds"></a>Automazione per le compilazioni  
 Compilazione o la configurazione dispone di un modello di automazione che viene fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider>. Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).  
  
 Se si crea un pacchetto VSPackage e si desidera controllare le opzioni di configurazione, è necessario usare il modello di automazione.  
  
## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem  
 Non è necessario fornire un'implementazione per il `SelectedItem` perché Visual Studio contiene un'implementazione standard dell'oggetto. Tuttavia, è possibile implementare il `SelectedItem` dell'oggetto se si preferisce. È necessario implementare un oggetto che contiene il `SelectedItem` dell'interfaccia e restituire una risposta a una chiamata ai <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo con VSITEMID impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Aggiunta come contributo al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md)
