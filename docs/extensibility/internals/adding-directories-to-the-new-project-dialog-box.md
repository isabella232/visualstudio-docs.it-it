---
title: Aggiunta di directory alla finestra di dialogo Nuovo progetto Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710237"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Aggiungere directory alla finestra di dialogo Nuovo progetto
Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory nella finestra di dialogo **Nuovo progetto** per visualizzarli per l'utilizzo come modelli. Nell'esempio di codice riportato di seguito viene illustrato come registrare una nuova directory, nota anche come nodo. Nell'esempio vengono registrati i modelli esposti da VSPackage, *CLSID_Package*, . Di conseguenza, il lato sinistro della finestra di dialogo **Nuovo progetto** offre il nodo aggiunto, con un nome determinato dalla risorsa *Folder_Label_ResID.* Questa risorsa viene caricata dalla DLL satellite VSPackage.

 Il valore **Folder** rappresenta un GUID di una cartella in cui viene visualizzato il *nodo Folder_Label_ResID.* Nell'esempio, il GUID rappresenta la cartella **Altri progetti** nel riquadro **Tipi** progetto della finestra di dialogo **Nuovo progetto.** Se il valore **Altri progetti** è assente, l'etichetta viene posizionata al livello superiore.

 Il `TemplatesDir` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi file possono essere file *vsz* o file modello tipici da clonare.

 Se si `TemplatesLocalizedSubDir`specifica , deve essere l'ID di risorsa `TemplatesDir` di una stringa che denomina la sottodirectory di tale contiene i modelli localizzati. Poiché [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] carica la risorsa stringa da una DLL satellite, se ne è ota', ogni DLL satellite può contenere un nome di sottodirectory diverso. Il `SortPriority` valore specifica una priorità di ordinamento.

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
- [Registrare modelli di progetto e di elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
