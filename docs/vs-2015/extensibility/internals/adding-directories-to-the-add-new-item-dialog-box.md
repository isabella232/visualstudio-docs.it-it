---
title: Aggiunta di directory di dialogo Aggiungi nuovo elemento | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9a4623df5794ae29b97bbbdc077c465d822d6f4d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519591"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Aggiunta di directory nella finestra di dialogo Aggiungi nuovo elemento
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiunta di directory per la finestra di dialogo Aggiungi nuovo elemento](https://docs.microsoft.com/visualstudio/extensibility/internals/adding-directories-to-the-add-new-item-dialog-box).  
  
Esempio di codice seguente viene illustrato come registrare un nuovo set di directory per il **Aggiungi nuovo elemento** nella finestra di dialogo. Directory per il **Aggiungi nuovo elemento** nella finestra di dialogo sono diverse per ogni progetto. Di conseguenza, le directory vengono registrate nella sottochiave progetti, disponibili in \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Lo Script del Registro di sistema  
  
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
  
 Il valore Template_Path specifica il percorso completo della directory che contiene i modelli di progetto. Questi modelli possono essere VSZ (file) o file di modello prototipo da clonare.  
  
 Il valore SortPriority specifica una priorità di ordinamento.  
  
## <a name="adding-items-to-an-existing-project"></a>Aggiunta di elementi a un progetto esistente  
 È anche possibile aggiungere elementi a un progetto esistente. Ad esempio, per un [!INCLUDE[csprcs](../../includes/csprcs-md.md)] progetto, è possibile aggiungere elementi per il \<radice > cartella \VC#\CSharpProjectItems\LocalProjectItems \Programmi\Microsoft Visual Studio. In questo caso il `%GUID_Project%` GUID di un progetto c# ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 È anche possibile estendere un progetto esistente da un sottotipo di progetto di programmazione. Con un sottotipo di progetto, è possibile estendere un progetto senza dover scrivere un nuovo tipo di progetto. Per altre informazioni sulle sottotipi di progetto, vedere [sottotipi di progetto](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Vedere anche  
 [La registrazione di progetto e modelli di elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiunta di elementi di Aggiungi nuovo elemento di finestre di dialogo](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiunta di directory nella finestra di dialogo Nuovo progetto](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
