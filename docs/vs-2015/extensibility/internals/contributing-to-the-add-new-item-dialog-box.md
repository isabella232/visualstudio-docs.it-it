---
title: Aggiunta di un contributo alla finestra di dialogo Aggiungi nuovo elemento | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197019"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Aggiunta di elementi nella finestra di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un sottotipo di progetto può fornire una nuova directory completa di elementi per la finestra di dialogo **Aggiungi nuovo elemento** registrando Aggiungi modelli di **elemento** nella `Projects` sottochiave del registro di sistema.  
  
## <a name="registering-add-new-item-templates"></a>Registrazione di modelli di aggiunta di nuovi elementi  
 Questa sezione si trova in **HKEY_LOCAL_MACHINE \Software\Microsoft\VisualStudio\8.0\Projects** nel registro di sistema. Le voci del registro di sistema seguenti presuppongono un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto aggregato da un sottotipo di progetto ipotetico. Di seguito sono elencate le voci per il [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto.  
  
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
  
 La `AddItemTemplates\TemplateDirs` sottochiave contiene le voci del registro di sistema con il percorso della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo **Aggiungi nuovo elemento** .  
  
 L'ambiente carica automaticamente tutti i `AddItemTemplates` dati nella `Projects` sottochiave del registro di sistema. Questo può includere i dati per le implementazioni di progetto di base e i dati per tipi di sottotipi di progetto specifici. Ogni sottotipo di progetto viene identificato da un tipo di progetto `GUID` . Il sottotipo di progetto può specificare che un set alternativo di `Add Item` modelli deve essere usato per un'istanza del progetto con versioni particolari, supportando l' `VSHPROPID_ AddItemTemplatesGuid` enumerazione da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementazione per restituire il valore GUID del sottotipo di progetto. Se `VSHPROPID_AddItemTemplatesGuid` la proprietà non è specificata, viene usato il GUID del progetto di base.  
  
 È possibile filtrare gli elementi nella finestra di dialogo **Aggiungi nuovo elemento** implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaccia nell'oggetto Aggregator del sottotipo di progetto. Ad esempio, un sottotipo di progetto che implementa un progetto di database aggregando un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] progetto può filtrare gli [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] elementi specifici dalla finestra di dialogo **Aggiungi nuovo elemento** implementando filtri e, a sua volta, può aggiungere elementi specifici del progetto di database supportando `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Per ulteriori informazioni sul filtro e l'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento** , vedere [aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATID per gli oggetti che vengono in genere usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
