---
title: Aggiunta di directory alla finestra di dialogo nuovo progetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710237"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Aggiungi directory alla finestra di dialogo nuovo progetto
Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory nella finestra di dialogo **nuovo progetto** per visualizzarli per l'uso come modelli. Nell'esempio di codice seguente viene illustrato come registrare una nuova directory, nota anche come nodo. Nell'esempio, i modelli esposti dal pacchetto VSPackage, *CLSID_Package*, sono registrati. Di conseguenza, il lato sinistro della finestra di dialogo **nuovo progetto** offre il nodo aggiunto, con un nome determinato dalla risorsa *Folder_Label_ResID* . Questa risorsa viene caricata dalla DLL satellite del pacchetto VSPackage.

 Il valore della **cartella** rappresenta il GUID di una cartella in cui viene visualizzato il nodo *Folder_Label_ResID* . Nell'esempio, il GUID rappresenta la cartella **altri progetti** nel riquadro **Tipi progetto** della finestra di dialogo **nuovo progetto** . Se il valore di **altri progetti** è assente, l'etichetta viene posizionata al livello superiore.

 Il `TemplatesDir` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi file possono essere file con *estensione vsz* o file modello tipici da clonare.

 Se si specifica `TemplatesLocalizedSubDir` , deve essere l'ID risorsa di una stringa che denomina la sottodirectory di `TemplatesDir` che include i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa di stringa da una DLL satellite se ne è presente una, ogni DLL satellite può contenere un nome di sottodirectory diverso. Il `SortPriority` valore specifica una priorità di ordinamento.

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
- [Registrare modelli di progetti e di elementi](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aggiungi elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
