---
title: Elemento TemplateGroupID (modelli di Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID
helpviewer_keywords:
- TemplateGroupID element [Visual Studio Templates]
- <TemplateGroupID> element [Visual Studio Templates]
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7a6c2852938e77f87143b3ddd15fce0a4a6e5bcd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49203918"
---
# <a name="templategroupid-element-visual-studio-templates"></a>Elemento TemplateGroupID (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Specifica il tipo di progetto in cui verranno visualizzati i modelli di elemento. Questo elemento è significativo quando [ShowByDefault (modelli di Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) è impostata su `false`. Quando [ShowByDefault (modelli di Visual Studio)](../extensibility/showbydefault-visual-studio-templates.md) è impostata su `true`, un modello di elemento è disponibile in tutti i tipi di progetto.  
  
 \<VSTemplate >  
 \<TemplateData >  
 \<TemplateGroupID >  
  
## <a name="syntax"></a>Sintassi  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** .|  
  
## <a name="text-value"></a>Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo specifica un identificatore per una categoria di modelli di elemento.  
  
## <a name="remarks"></a>Note  
 `TemplateGroupID` è un elemento.  
  
 Il valore della `TemplateGroupID` elemento viene usato con la registrazione nel sistema di progetto (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<numero di versione >* \Projects\\) per i modelli di filtro che vengono visualizzati nei **Aggiungi nuovo elemento** nella finestra di dialogo.  
  
|Valore di Visual C++|Significato|  
|------------------------|-------------|  
|VC-Native|Usato nei progetti nativi. È anche il valore predefinito se non è possibile determinare un tipo di progetto.|  
|VC-Managed|Usato per i progetti (/clr) gestiti|  
|VC-Windows|Usato per tutti i progetti per la piattaforma Windows (nativi/gestiti/Store)|  
|WinRT-Native-UAP|Usato per i progetti Store di Windows 10|  
|CodeSharing-Native|Usato per i progetti di elementi condivisi|  
|WinRT-Native-6.3|Usato per i progetti Store di Windows 8.1|  
|WinRT-Native-Phone-6.3|Usato per i progetti Windows Phone 8.1|  
|WinRT-Nativo|Usato per i progetti Store di Windows 8.0|  
|VC-Android|Usato per i progetti Android|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)

