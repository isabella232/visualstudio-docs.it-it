---
title: Elemento LocalizedName (Schema del progetto VSIX Language Pack) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fcbda9f8c7a98d0830c898c81471854efc3a6403
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686145"
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
 [Riferimenti su VSIX Extension Schema 1.0](https://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
