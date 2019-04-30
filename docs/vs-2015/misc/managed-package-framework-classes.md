---
title: Classi di Framework di pacchetto gestito | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 75f7cb153a976614ff790095141a820af80b5834
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63422760"
---
# <a name="managed-package-framework-classes"></a>Classi del framework di pacchetto gestito
Le classi del framework di pacchetto gestito (MPF) possono essere usate per creare pacchetti VSPackage con il codice gestito e forniscono le implementazioni predefinite per molte delle interfacce di VSPackage. Nascondendo i dettagli e le complessità di implementazione, MPF consente di creare prodotti per l'integrazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con una quantità minima di codice.  
  
> [!WARNING]
> La maggior parte degli assembly che contengono le classi del framework di pacchetto gestito viene fornita con Visual Studio SDK. È possibile scaricare il codice sorgente per il framework di pacchetto gestito per i progetti in [framework di pacchetto gestito per progetti](http://mpfproj11.codeplex.com/).  
  
## <a name="mpf-namespaces"></a>Spazi dei nomi MPF  
 La tabella seguente contiene l'elenco degli spazi dei nomi MPF forniti da [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Spazio dei nomi|Contenuto|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contiene le classi utili per la gestione degli errori COM, le costanti di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] e le finestre Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Include i wrapper di codice gestito per i progetti, gli editor e MSBuild di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell>|Include le classi base di MPF da cui è possibile derivare un'implementazione di molti oggetti comuni di Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contiene le estensioni della finestra di progettazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contiene le estensioni della finestra di serializzazione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contiene le estensioni della finestra di progettazione CodeDom di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Supporta sottotipi di progetto (noti anche come "versioni").|  
  
## <a name="see-also"></a>Vedere anche  
 [Pacchetti VSPackage e Framework di pacchetto gestito](../misc/vspackages-and-the-managed-package-framework.md)   
 [Uso degli assembly di interoperabilità di Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [Pacchetti VSPackage e framework del pacchetto gestito](../misc/vspackages-and-the-managed-package-framework.md)