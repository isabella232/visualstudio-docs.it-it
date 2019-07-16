---
title: Aggiunta come contributo di dialogo Aggiungi nuovo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68197019"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sottotipo di progetto può fornire una nuova directory completa degli elementi per il **Aggiungi nuovo elemento** finestra di dialogo registrando **Aggiungi elemento** modelli sotto il `Projects` sottochiave del Registro di sistema.  
  
## <a name="registering-add-new-item-templates"></a>La registrazione di modelli Aggiungi nuovo elemento  
 In questa sezione si trova sotto **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** nel Registro di sistema. Le voci del Registro di sistema riportata di seguito presuppongono un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto aggregato da un sottotipo di progetto ipotetico. Le voci per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto sono elencati di seguito.  
  
```  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]  
@="#2143"  
"DefaultProjectExtension"="vbproj"  
"PossibleProjectExtensions"="vbproj;vbp"  
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"  
  
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]  
@="#100"  
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"  
```  
  
 Il `AddItemTemplates\TemplateDirs` sottochiave contiene le voci del Registro di sistema con il percorso della directory in cui gli elementi reso disponibili nel **Aggiungi nuovo elemento** vengono inseriti nella finestra di dialogo.  
  
 L'ambiente carica automaticamente tutti i `AddItemTemplates` dati sotto il `Projects` sottochiave del Registro di sistema. Può trattarsi di dati per le implementazioni di progetto di base, nonché i dati per i tipi sottotipo di progetto specifico. Ogni sottotipo di progetto è identificato da un tipo di progetto `GUID`. Il sottotipo di progetto è possibile specificare che un'alternativa set di `Add Item` modelli devono essere utilizzati per un'istanza particolare progetto caratterizzato supportando il `VSHPROPID_ AddItemTemplatesGuid` enumerazione da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementazione per restituire il GUID valore del sottotipo di progetto. Se `VSHPROPID_AddItemTemplatesGuid` proprietà non viene specificata, il progetto di base GUID viene utilizzato.  
  
 È possibile filtrare gli elementi nel **Aggiungi nuovo elemento** finestra di dialogo implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaccia sull'oggetto di Sil aggregator sottotipo del progetto. Ad esempio, un sottotipo di progetto che implementa un progetto di database mediante l'aggregazione di un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] del progetto, consente di filtrare le [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementi specifici dal **Aggiungi nuovo elemento** implementando il filtraggio e nella finestra di dialogo attiva, è possibile aggiungere elementi specifici del progetto del database supportando `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Per altre informazioni sul filtro e aggiunta di elementi il **Aggiungi nuovo elemento** finestra di dialogo, vedere [Aggiunta elementi finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
