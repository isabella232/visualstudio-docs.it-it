---
title: Elemento LOCALIZZATOR (schema del Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57b7f502-3b04-42d9-90d5-f57772a7c757
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 58e491290122a9d525ff8129333ac0f52ac5f778
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477029"
---
# <a name="localizedname-element-vsix-language-pack-schema"></a>Elemento LOCALIZZATOR (schema del Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obbligatoria. Nome localizzato dell'estensione da installare.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<Name>Localized name of the extension</Name>  
```  
  
## <a name="attributes-and-elements"></a>Attributi ed elementi  
 Le sezioni seguenti descrivono gli attributi, gli elementi figlio e gli elementi padre.  
  
### <a name="attributes"></a>Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|None||  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|None||  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obbligatoria. Fornisce l'elemento radice per un Language Pack VSIX.|  
  
## <a name="text-value"></a>Valore di testo  
 Obbligatoria. Nome del Language Pack nella lingua di destinazione.  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Spazio dei nomi    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Nome schema   |                 Schema del Language Pack VSIX                 |
| File di convalida |                VSIXLanguagePackSchema.xsd                 |
|  Può essere vuoto   |                      Non applicabile                       |
  
## <a name="see-also"></a>Vedere anche  
 Informazioni di [riferimento sullo schema del Language Pack VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110))
