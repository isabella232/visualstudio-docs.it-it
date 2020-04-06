---
title: Aggiunta di directory alla finestra di dialogo Aggiungi nuovo elemento . Documenti Microsoft
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
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710257"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento
Esempio di codice seguente viene illustrato come registrare un nuovo set di directory per il **Aggiungi nuovo elemento** la finestra di dialogo. Le directory per la finestra di dialogo **Aggiungi nuovo elemento** sono diverse per ogni progetto. Di conseguenza, le directory vengono registrate nella sottochiave **Projects** , disponibile nella **HKEY_LOCAL_MACHINE SOFTWARE**.

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

 Il `%Template_Path%` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere file *con estensione vsz* o file di modello prototipo da clonare.

 Il `SortPriority` valore specifica una priorità di ordinamento.

## <a name="add-items-to-an-existing-project"></a>Aggiungere elementi a un progetto esistente
 È inoltre possibile aggiungere elementi a un progetto esistente. Ad esempio, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] per un progetto, è possibile aggiungere elementi alla cartella * \<>* directory radice> . In questo `%GUID_Project%` caso, è il GUID per un progetto in C, ovvero FAE04EC0-301F-11D3-BF4B-00C04F79EFBC.

 È inoltre possibile estendere un progetto esistente programmando un sottotipo di progetto. Con un sottotipo di progetto, è possibile estendere un progetto senza scrivere un nuovo tipo di progetto. Per ulteriori informazioni sui sottotipi di progetto, vedere [Sottotipi di progetto](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Vedere anche
- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Aggiungere directory alla finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
