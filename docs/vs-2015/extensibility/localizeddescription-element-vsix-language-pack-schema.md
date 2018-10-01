---
title: Elemento LocalizedDescription (Schema del progetto VSIX Language Pack) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e509573518ebf779cb15bc2859bacc61c336f7f7
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530476"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>Elemento LocalizedDescription (Schema del progetto VSIX Language Pack)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [elemento LocalizedDescription (Schema del progetto VSIX Language Pack)](https://docs.microsoft.com/visualstudio/extensibility/localizeddescription-element-vsix-language-pack-schema).  
  
Obbligatorio. Fornisce una descrizione localizzata dell'estensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|nessuno||  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obbligatorio. Fornisce l'elemento radice per un language pack VSIX.|  
  
## <a name="text-value"></a>Valore di testo  
 Obbligatorio. Una descrizione dell'estensione nella lingua di destinazione.  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|||  
|-|-|  
|Spazio dei nomi|http://schemas.microsoft.com/developer/vsx-schema-lp/2010|  
|Nome di schema|Schema del Language Pack VSIX|  
|File di convalida|VSIXLanguagePackSchema.xsd|  
|Può essere vuoto|Non applicabile|  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

