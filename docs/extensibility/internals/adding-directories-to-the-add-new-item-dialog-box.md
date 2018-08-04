---
title: Aggiunta di directory di dialogo Aggiungi nuovo elemento | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ba535908b1c5ccb06f0f29490c0b87c377d6b2be
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2018
ms.locfileid: "39498334"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento
Esempio di codice seguente viene illustrato come registrare un nuovo set di directory per il **Aggiungi nuovo elemento** nella finestra di dialogo. Directory per il **Aggiungi nuovo elemento** nella finestra di dialogo sono diverse per ogni progetto. Di conseguenza, le directory vengono registrate sotto il **progetti** sottochiave, trovato nella **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.
  
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
  
 Il `%Template_Path%` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere *vsz* file o i file di modello prototipo da clonare.  
  
 Il `SortPriority` valore specifica una priorità di ordinamento.  
  
## <a name="add-items-to-an-existing-project"></a>Aggiungere elementi a un progetto esistente  
 È anche possibile aggiungere elementi a un progetto esistente. Ad esempio, per un [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] progetto, è possibile aggiungere elementi per il  *\<radice > \Programmi\Microsoft Visual Studio\VC & \CSharpProjectItems\LocalProjectItems* cartella. In questo caso, `%GUID_Project%` GUID di un progetto c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 È anche possibile estendere un progetto esistente da un sottotipo di progetto di programmazione. Con un sottotipo di progetto, è possibile estendere un progetto senza dover scrivere un nuovo tipo di progetto. Per altre informazioni sulle sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiungere directory alla finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)