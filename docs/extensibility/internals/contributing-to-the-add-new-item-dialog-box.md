---
title: Contribuire alla finestra di dialogo Aggiungi nuovo elemento Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709286"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuire alla finestra di dialogo Aggiungi nuovo elemento
Un sottotipo di progetto può fornire una nuova directory completa di elementi per la finestra di dialogo **Aggiungi nuovo elemento** registrando i modelli Aggiungi **elemento** nella sottochiave del Registro di sistema **Progetti.**

## <a name="register-add-new-item-templates"></a>Registrare i modelli Aggiungi nuovo elemento
 Questa sezione si trova in HKEY_LOCAL_MACHINE SOFTWARE Microsoft **VisualStudio 8.0 Projects** nel Registro di sistema. Le voci del Registro di sistema seguenti presuppongono un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aggregato da un sottotipo di progetto ipotetico. Le voci per [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il progetto sono elencate di seguito.

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

 La sottochiave **AddItemTemplates-TemplateDirs** contiene le voci del Registro di sistema con il percorso della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo **Aggiungi nuovo elemento.**

 L'ambiente carica automaticamente tutti i dati **AddItemTemplates** nella sottochiave del Registro di sistema **Projects.** Questi dati possono includere i dati per le implementazioni del progetto di base, nonché i dati per tipi di sottotipi di progetto specifici. Ogni sottotipo di progetto è identificato da un tipo di progetto **GUID**. Il sottotipo di progetto può specificare che un set alternativo di **modelli Aggiungi elemento** deve essere utilizzato per una particolare istanza di progetto aromatizzata supportando l'enumerazione `VSHPROPID_ AddItemTemplatesGuid` da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> nell'implementazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> per restituire il valore GUID del sottotipo di progetto. Se `VSHPROPID_AddItemTemplatesGuid` la proprietà non è specificata, viene utilizzato il GUID del progetto di base.

 È possibile filtrare gli elementi nella finestra <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> di dialogo Aggiungi nuovo **elemento** implementando l'interfaccia nell'oggetto aggregatore di sottotipi di progetto. Ad esempio, un sottotipo di progetto che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementa un progetto [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di database aggregando un progetto, è possibile filtrare gli elementi `VSHPROPID_ AddItemTemplatesGuid` specifici <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>dalla finestra di dialogo Aggiungi **nuovo elemento** implementando il filtro e, a sua volta, aggiungere elementi specifici del progetto di database supportando in . Per ulteriori informazioni sul filtro e sull'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento,** vedere Aggiungere elementi alla finestra di [dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID per gli oggetti che vengono in genere utilizzati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
