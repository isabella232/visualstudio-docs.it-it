---
title: Elemento PreviewImage (modelli di Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 313f97324d3b4eed5a9d0866bef94ee9265701eb
ms.sourcegitcommit: 35bebf794f528d73d82602e096fd97d7b8f82c25
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/18/2018
ms.locfileid: "53562048"
---
# <a name="previewimage-element-visual-studio-templates"></a>Elemento PreviewImage (modelli di Visual Studio)
Specifica l'immagine di anteprima, come un nome di file, per l'immagine di anteprima che verrà visualizzato in entrambi i **nuovo progetto** o **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<PreviewImage >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<PreviewImage>"filename"</PreviewImage>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
 Nessuno.  
  
### <a name="child-elements"></a>Elementi figlio  
 Nessuno.  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce come viene visualizzato in entrambi i **nuovo progetto** o il **Aggiungi nuovo elemento** nella finestra di dialogo.|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo deve essere una stringa che rappresenta un nome di file.  
  
## <a name="remarks"></a>Note  
 `PreviewImage` è un elemento facoltativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti dello schema di modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)