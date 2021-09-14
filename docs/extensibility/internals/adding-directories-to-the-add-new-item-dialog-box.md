---
title: Aggiunta di directory alla finestra di dialogo Aggiungi nuovo elemento | Microsoft Docs
description: Informazioni su come aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento Visual Studio usando uno script del Registro di sistema per registrare le directory.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 258ff221893fc9ec10c9e37920c87fb242f4dc36
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709585"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento
Nell'esempio di codice seguente viene illustrato come registrare un nuovo set di directory per la **finestra di** dialogo Aggiungi nuovo elemento . Le directory per **la finestra di dialogo Aggiungi** nuovo elemento sono diverse per ogni progetto. Di conseguenza, le directory vengono registrate nella **sottochiave Projects,** disponibile in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Script del Registro di sistema

```
NoRemove Projects
{
  NoRemove %GUID_Project%
  {
    NoRemove AddItemTemplates
    {
      NoRemove TemplateDirs
      {
        ForceRemove %CLSID_Package%
        {
      ForceRemove /1 = s '#%Folder_Label_ResID%'
          {
            val TemplatesDir = s '%Template_Path%'
            val SortPriority = d 2000
          }
        }
      }
    }
  }
}
```

 Il `%Template_Path%` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere *file vsz* o file modello prototipo da clonare.

 Il `SortPriority` valore specifica una priorità di ordinamento.

## <a name="add-items-to-an-existing-project"></a>Aggiungere elementi a un progetto esistente
 È anche possibile aggiungere elementi a un progetto esistente. Ad esempio, per un progetto, è possibile aggiungere elementi alla cartella [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] *\<root> \Programmi\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems.* In questo caso, è il GUID per un progetto `%GUID_Project%` C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 È anche possibile estendere un progetto esistente programmando un sottotipo di progetto. Con un sottotipo di progetto è possibile estendere un progetto senza scrivere un nuovo tipo di progetto. Per altre informazioni sui sottotipi di progetto, [vedere Project sottotipi](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vedi anche
- [Registrare i modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Aggiungere directory alla finestra di dialogo Project nuova cartella](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
