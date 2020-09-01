---
title: Elemento License (schema del Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f1299d97cbda78049732d3367a9231272397e2ec
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284382"
---
# <a name="license-element-vsix-language-pack-schema"></a>Elemento License (schema del Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

facoltativo. Percorso di una versione localizzata del file di licenza per l'estensione.  
  
## <a name="syntax"></a>Sintassi  
  
```  
<License>FilePath\license.txt</License>  
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
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obbligatorio. Fornisce l'elemento radice per un Language Pack VSIX.|  
  
## <a name="text-value"></a>Valore di testo  
 Percorso relativo del file di licenza localizzato da visualizzare.  
  
## <a name="remarks"></a>Osservazioni  
 Se l' `License` elemento è definito, il testo del file di licenza designato viene visualizzato durante l'installazione e l'utente deve accettare la licenza per continuare.  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Spazio dei nomi    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Schema Name   |                 Schema del Language Pack VSIX                 |
| File di convalida |                VSIXLanguagePackSchema. xsd                 |
|  Può essere vuoto   |                      Non applicabile                       |
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento sullo schema del Language Pack VSX](../extensibility/vsx-language-pack-schema-reference.md)   
 [Localizzazione di pacchetti VSIX](../extensibility/localizing-vsix-packages.md)   
 [Riferimento allo schema di estensione VSIX 1,0](/previous-versions/dd393700(v=vs.110))
