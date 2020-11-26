---
title: Aggiunta di directory alla finestra di dialogo Aggiungi nuovo elemento | Microsoft Docs
description: Per informazioni su come aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento in Visual Studio, usare uno script del registro di sistema per registrare le directory.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d6a8090a47c275e66272ed3ee3e5d5a1eef1926d
ms.sourcegitcommit: b1b747063ce0bba63ad2558fa521b823f952ab51
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/26/2020
ms.locfileid: "96189732"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento
Nell'esempio di codice riportato di seguito viene illustrato come registrare un nuovo set di directory per la finestra di dialogo **Aggiungi nuovo elemento** . Le directory per la finestra di dialogo **Aggiungi nuovo elemento** sono diverse per ogni progetto. Pertanto, le directory vengono registrate nella sottochiave **Projects** , disponibile in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Script del registro di sistema

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

 Il `%Template_Path%` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere clonati con i file con *estensione vsz* o i file modello di prototipo.

 Il `SortPriority` valore specifica una priorità di ordinamento.

## <a name="add-items-to-an-existing-project"></a>Aggiungi elementi a un progetto esistente
 È anche possibile aggiungere elementi a un progetto esistente. Per un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetto, ad esempio, è possibile aggiungere elementi alla cartella *\<root> \Programmi\Microsoft Visual Studio\VC # \CSharpProjectItems\LocalProjectItems* In questo caso, `%GUID_Project%` è il GUID di un progetto C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 È anche possibile estendere un progetto esistente tramite la programmazione di un sottotipo di progetto. Con un sottotipo di progetto, è possibile estendere un progetto senza scrivere un nuovo tipo di progetto. Per ulteriori informazioni sui sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vedere anche
- [Registrare modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aggiungi elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Aggiungi directory alla finestra di dialogo nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
