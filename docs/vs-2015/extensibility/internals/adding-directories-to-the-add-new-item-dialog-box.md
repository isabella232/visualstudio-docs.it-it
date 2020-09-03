---
title: Aggiunta di directory alla finestra di dialogo Aggiungi nuovo elemento | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203920"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Nell'esempio di codice riportato di seguito viene illustrato come registrare un nuovo set di directory per la finestra di dialogo **Aggiungi nuovo elemento** . Le directory per la finestra di dialogo **Aggiungi nuovo elemento** sono diverse per ogni progetto. Pertanto, le directory vengono registrate nella sottochiave Projects, disponibile in \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Script del registro di sistema  
  
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
  
 Il valore Template_Path specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere clonati con i file con estensione vsz o i file modello di prototipo.  
  
 Il valore SortPriority specifica una priorità di ordinamento.  
  
## <a name="adding-items-to-an-existing-project"></a>Aggiunta di elementi a un progetto esistente  
 È anche possibile aggiungere elementi a un progetto esistente. Per un [!INCLUDE[csprcs](../../includes/csprcs-md.md)] progetto, ad esempio, è possibile aggiungere elementi alla \<root> cartella \Programmi\microsoft Visual Studio \VC # \CSharpProjectItems\LocalProjectItems In questo caso `%GUID_Project%` è il GUID di un progetto C# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 È anche possibile estendere un progetto esistente tramite la programmazione di un sottotipo di progetto. Con un sottotipo di progetto, è possibile estendere un progetto senza scrivere un nuovo tipo di progetto. Per ulteriori informazioni sui sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione di modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiunta di elementi alle finestre di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiunta di directory nella finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
