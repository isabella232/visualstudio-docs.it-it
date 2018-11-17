---
title: Automazione per la configurazione e gli oggetti SelectedItem | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- automation [Visual Studio SDK], SelectedItem object
- automation [Visual Studio SDK], builds
ms.assetid: 120377f1-51aa-4445-b2f7-06ab7fc2b47f
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 612916da7922900a1054d785dad86ed448aa1f12
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51733465"
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

