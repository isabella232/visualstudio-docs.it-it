---
title: Aggiunta di directory alla finestra di dialogo Project nuovo | Microsoft Docs
description: Informazioni su come aggiungere directory alla finestra di dialogo Nuovo Project in Visual Studio, in modo da poter creare nuovi tipi di progetto e visualizzarli per l'uso come modelli.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 62d3cfaeca91595e13456b454400e79b50dc6017
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122086917"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Aggiungere directory alla finestra di dialogo Project nuovo
Quando si creano nuovi tipi di progetto, è anche possibile registrare una nuova directory nella finestra di **dialogo Nuovo Project** per visualizzarli da usare come modelli. Nell'esempio di codice seguente viene illustrato come registrare una nuova directory, nota anche come nodo. Nell'esempio i modelli esposti dal pacchetto VSPackage, *CLSID_Package*, vengono registrati. Di conseguenza, il lato sinistro della finestra di **dialogo Project** nuovo nodo offre il nodo aggiunto, con un nome determinato dalla Folder_Label_ResID *risorsa.* Questa risorsa viene caricata dalla DLL satellite VSPackage.

 Il **valore** Cartella rappresenta un GUID di una cartella in cui *viene visualizzato Folder_Label_ResID* nodo. Nell'esempio, il GUID rappresenta **la** cartella Altri progetti nel **riquadro Project** della finestra di **dialogo Project** nuovo progetto . Se il **valore Altri progetti** è assente, l'etichetta viene posizionata al livello superiore.

 Il `TemplatesDir` valore specifica il percorso completo della directory che contiene i modelli di progetto. Questi file possono essere file *con estensione vsz* o file modello tipici da clonare.

 Se si specifica , deve essere l'ID risorsa di una stringa che specifica la `TemplatesLocalizedSubDir` sottodirectory di `TemplatesDir` che contiene i modelli localizzati. Poiché carica la risorsa stringa da una DLL satellite, se presente, ogni [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] DLL satellite può contenere un nome di sottodirectory diverso. Il `SortPriority` valore specifica una priorità di ordinamento.

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

## <a name="see-also"></a>Vedi anche
- [Registrare modelli di progetto ed elemento](../../extensibility/internals/registering-project-and-item-templates.md)
- [Aggiungere elementi alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Aggiungere directory alla finestra di dialogo Aggiungi nuovo elemento](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
