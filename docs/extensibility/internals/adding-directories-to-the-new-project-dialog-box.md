---
title: Aggiunta di directory per la finestra di dialogo Nuovo progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26fe254a168ae1834fba804ca34d4e48bd240ca6
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54941093"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Aggiungere directory alla finestra di dialogo Nuovo progetto
Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory nel **nuovo progetto** finestra di dialogo per la visualizzazione per l'uso come modelli. Esempio di codice seguente illustra come registrare una nuova directory, noto anche come un nodo. Nell'esempio esposti dal pacchetto VSPackage, i modelli *CLSID_Package*, vengono registrati. Di conseguenza, il lato sinistro del **nuovo progetto** finestra di dialogo offre il nodo aggiunto, con un nome di base di *Folder_Label_ResID* risorse. Questa risorsa verrà caricata della DLL satellite di VSPackage.  
  
 Il **cartella** valore rappresenta un GUID di una cartella in cui le *Folder_Label_ResID* nodo viene visualizzato. Nell'esempio, rappresenta il GUID il **altri progetti** cartella il **tipi di progetto** riquadro del **nuovo progetto** nella finestra di dialogo. Se il **altri progetti** valore è assente, l'etichetta viene posizionata nella parte superiore.  
  
 Il `TemplatesDir` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi file possono essere *vsz* file o i file di modello tipico per la clonazione.  
  
 Se si specifica `TemplatesLocalizedSubDir`, deve essere l'ID risorsa della stringa che denomina la sottodirectory della `TemplatesDir` che contiene i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa stringa da una DLL satellite se presente, ogni DLL satellite può contenere un nome di sottodirectory diverse. Il `SortPriority` valore specifica una priorità di ordinamento.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Registrare i modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)