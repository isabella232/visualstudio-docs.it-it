---
title: Automazione per gli oggetti Configuration e SelectedItem | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157255"
---
# <a name="automation-for-configuration-and-selecteditem-objects"></a>Automazione per la configurazione e per gli oggetti SelectedItem
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

È possibile automatizzare i processi di compilazione e di elementi selezionati in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="automation-for-builds"></a>Automazione per le compilazioni  
 La compilazione o la configurazione ha un modello di automazione fornito quando si implementa <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider> . Per altre informazioni, vedere [Informazioni sulle configurazioni della build](../../ide/understanding-build-configurations.md).  
  
 Se si crea un pacchetto VSPackage e si desidera controllare le opzioni di configurazione, è necessario utilizzare il modello di automazione.  
  
## <a name="automation-for-selecteditem"></a>Automazione per SelectedItem  
 Non è necessario fornire un'implementazione per l' `SelectedItem` oggetto perché Visual Studio contiene un'implementazione standard. Tuttavia, è possibile implementare l' `SelectedItem` oggetto se lo si preferisce. È necessario implementare un oggetto che contiene l' `SelectedItem` interfaccia e restituire una risposta a una chiamata al <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A> metodo con VSITEMID impostato su <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> .  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetPropertyPage%2A>   
 [Aggiunta come contributo al modello di automazione](../../extensibility/internals/contributing-to-the-automation-model.md)   
 [Informazioni sulle configurazioni di compilazione](../../ide/understanding-build-configurations.md)
