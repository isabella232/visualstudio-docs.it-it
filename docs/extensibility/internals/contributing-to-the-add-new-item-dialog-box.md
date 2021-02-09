---
title: Aggiunta di un contributo alla finestra di dialogo Aggiungi nuovo elemento | Microsoft Docs
description: Per informazioni su come contribuire alla finestra di dialogo Aggiungi nuovo elemento in Visual Studio, registrare Aggiungi modelli di elemento nella sottochiave del registro di sistema progetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3fdc5705cad0ec696a520350042d7f18aaec146
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99884637"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Contribuire alla finestra di dialogo Aggiungi nuovo elemento
Un sottotipo di progetto può fornire una nuova directory completa di elementi per la finestra di dialogo **Aggiungi nuovo elemento** registrando Aggiungi modelli di **elemento** nella sottochiave del registro di sistema **progetti** .

## <a name="register-add-new-item-templates"></a>Registrare i modelli di aggiunta di nuovi elementi
 Questa sezione si trova in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** nel registro di sistema. Le voci del registro di sistema seguenti presuppongono un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto aggregato da un sottotipo di progetto ipotetico. Di seguito sono elencate le voci per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto.

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

 La sottochiave **AddItemTemplates\TemplateDirs** contiene le voci del registro di sistema con il percorso della directory in cui vengono inseriti gli elementi resi disponibili nella finestra di dialogo **Aggiungi nuovo elemento** .

 L'ambiente carica automaticamente tutti i dati **AddItemTemplates** nella sottochiave del registro di sistema dei **progetti** . Questi dati possono includere i dati per le implementazioni di progetto di base e i dati per tipi di sottotipi di progetto specifici. Ogni sottotipo di progetto viene identificato da un **GUID** del tipo di progetto. Il sottotipo di progetto può specificare che un set alternativo di modelli di **aggiunta di elementi** deve essere usato per una particolare istanza di progetto con il supporto dell' `VSHPROPID_ AddItemTemplatesGuid` enumerazione da <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> nell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> implementazione per restituire il valore GUID del sottotipo di progetto. Se la `VSHPROPID_AddItemTemplatesGuid` proprietà non è specificata, viene usato il GUID del progetto di base.

 È possibile filtrare gli elementi nella finestra di dialogo **Aggiungi nuovo elemento** implementando l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> interfaccia nell'oggetto Aggregator del sottotipo di progetto. Ad esempio, un sottotipo di progetto che implementa un progetto di database aggregando un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] progetto può filtrare gli [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] elementi specifici dalla finestra di dialogo **Aggiungi nuovo elemento** implementando filtri e, a sua volta, può aggiungere elementi specifici del progetto di database supportando `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Per ulteriori informazioni sul filtro e l'aggiunta di elementi alla finestra di dialogo **Aggiungi nuovo elemento** , vedere [aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATID per gli oggetti che in genere vengono usati per estendere i progetti](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
