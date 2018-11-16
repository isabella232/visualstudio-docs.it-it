---
title: Elemento VSIXLanguagePack (Schema del progetto VSIX Language Pack) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 556b701f0a1dbc348fef53273379586f7a0dba2c
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51744175"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento VSIXLanguagePack (Schema del progetto VSIX Language Pack)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obbligatorio. Fornisce l'elemento radice per un language pack VSIX. Il language pack VSIX vengono fornite informazioni di installazione localizzata per un pacchetto VSIX.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`xmlns`|Lo spazio dei nomi XML in cui è definito lo schema del Language Pack VSIX.|  
  
## <a name="xmlns-attribute"></a>Attributo xmlns  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obbligatorio. Il percorso del file che definisce lo schema per i language pack.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obbligatorio. Il nome localizzato dell'estensione da installare.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obbligatorio. La descrizione localizzata dell'estensione da installare.|  
|[Elemento MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|Facoltativo. Collegamento a informazioni localizzate sull'estensione.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|Facoltativo. Il percorso di una versione localizzata del file di licenza per l'estensione.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Spazio dei nomi    | http://schemas.microsoft.com/developer/vsx-schema-lp/2010 |
|   Nome di schema   |                 Schema del Language Pack VSIX                 |
| File di convalida |                VSIXLanguagePackSchema.xsd                 |
|  Può essere vuoto   |                            No                             |
  
## <a name="see-also"></a>Vedere anche  
 [Riferimento allo Schema VSX Language Pack](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/en-us/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)

