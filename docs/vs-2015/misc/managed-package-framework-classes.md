---
title: Classi di Framework di pacchetto gestito | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 38f159df52c99554ed931269f29ad57e72745b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531576"
---
# <a name="managed-package-framework-classes"></a>Classi del framework di pacchetto gestito
Le classi del framework di pacchetto gestito (MPF) possono essere usate per creare pacchetti VSPackage con il codice gestito e forniscono le implementazioni predefinite per molte delle interfacce di VSPackage. Nascondere la complessità e i dettagli di implementazione, MPF consente di creare [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] i prodotti di integrazione con una quantità minima di codice.  
  
> [!WARNING]
>  La maggior parte degli assembly che contengono le classi del framework di pacchetto gestito viene fornita con Visual Studio SDK. È possibile scaricare il codice sorgente per il framework di pacchetto gestito per i progetti in [framework di pacchetto gestito per progetti](http://mpfproj11.codeplex.com/).  
  
## <a name="mpf-namespaces"></a>Spazi dei nomi MPF  
 La tabella seguente elenca gli spazi dei nomi MPF forniti dal [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Spazio dei nomi|Contenuto|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contiene classi utili per la gestione degli errori COM, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] costanti e le finestre Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Include i wrapper del codice gestito per [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetti, editor e MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Include le classi base di MPF da cui è possibile derivare un'implementazione di molti oggetti comuni di Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni della finestra di progettazione.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni della finestra di progettazione di serializzazione.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] estensioni della finestra di progettazione CodeDom.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Supporta sottotipi di progetto (noti anche come "versioni").|  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage e Framework di pacchetto gestito](../misc/vspackages-and-the-managed-package-framework.md)   
 [Uso degli assembly di interoperabilità di Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Pacchetti VSPackage e framework del pacchetto gestito](../misc/vspackages-and-the-managed-package-framework.md)