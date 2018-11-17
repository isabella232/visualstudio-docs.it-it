---
title: Elemento LocalizedName (Schema del progetto VSIX Language Pack) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b183a0cbbf79442e8e5b79df14dd3a9dc091571
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51759880"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Elemento LocalizedName (Schema del progetto VSIX Language Pack)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obbligatorio. Il nome localizzato dell'estensione da installare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Name>Localized name of the extension</Name>  
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
 Obbligatorio. Il nome del language pack nella lingua di destinazione.  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Spazio dei nomi    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nome di schema   |                 Schema del Language Pack VSIX                 |
| File di convalida |                VSIXLanguagePackSchema.xsd                 |
|  Può essere vuoto   |                      Non applicabile                       |
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

