---
title: Aggiunta di contributi alla finestra di dialogo Aggiungi nuovo elemento | Microsoft Docs
description: Informazioni su come contribuire alla finestra di dialogo Aggiungi nuovo elemento Visual Studio registrando i modelli Aggiungi elemento nella sottochiave del Registro di sistema Projects.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: a99ccd5375f91baf0f91fceaadd803ee30d5b985
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086846"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuire alla finestra di dialogo Aggiungi nuovo elemento
Un sottotipo di progetto può fornire  una nuova directory completa  di elementi per la finestra di dialogo Aggiungi nuovo elemento registrando i modelli Aggiungi elemento nella sottochiave **del** Registro di sistema Projects.

## <a name="register-add-new-item-templates"></a>Registrare i modelli Aggiungi nuovo elemento
 Questa sezione si trova in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** nel Registro di sistema. Le voci del Registro di sistema seguenti [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] presuppongono un progetto aggregato da un sottotipo di progetto ipotetico. Le voci per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto sono elencate di seguito.

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

 La **sottochiave AddItemTemplates\TemplateDirs** contiene le voci del Registro di sistema  con il percorso della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo Aggiungi nuovo elemento.

 L'ambiente carica automaticamente tutti i **dati AddItemTemplates** nella sottochiave del Registro di sistema **Projects.** Questi dati possono includere i dati per le implementazioni del progetto di base, nonché i dati per tipi di sottotipi di progetto specifici. Ogni sottotipo di progetto è identificato da un GUID del tipo **di progetto**. Il sottotipo di progetto può  specificare che un set alternativo di modelli Aggiungi elemento deve essere usato per una particolare istanza del progetto di versione supportando l'enumerazione da nell'implementazione per restituire il valore GUID del sottotipo `VSHPROPID_ AddItemTemplatesGuid` di <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> progetto. Se la `VSHPROPID_AddItemTemplatesGuid` proprietà non viene specificata, viene usato il GUID del progetto di base.

 È possibile filtrare gli elementi nella **finestra di** dialogo Aggiungi nuovo elemento implementando l'interfaccia <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> nell'oggetto aggregatore del sottotipo di progetto. Ad esempio, un sottotipo di progetto che implementa un progetto di database aggregando un progetto può filtrare gli elementi specifici della finestra di dialogo Aggiungi nuovo elemento implementando il filtro e, a sua volta, può aggiungere elementi specifici del progetto di database supportando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] in  `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Per altre informazioni su come filtrare e aggiungere elementi **alla** finestra di dialogo Aggiungi nuovo elemento, vedere Aggiungere elementi alla finestra di dialogo Aggiungi [nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID per oggetti usati in genere per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
