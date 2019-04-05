---
title: Element (Schema VSIX Language Pack) di licenza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: a3a46e772849646a82d70ce9a68491d0b388b6c1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964243"
---
# <a name="license-element-vsix-language-pack-schema"></a>Elemento License (Schema del progetto VSIX Language Pack)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Facoltativo. Il percorso di una versione localizzata del file di licenza per l'estensione.  
  
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
|[Elemento LanguagePack VSIX](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|Obbligatorio. Fornisce l'elemento radice per un language pack VSIX.|  
  
## <a name="text-value"></a>Valore di testo  
 Il percorso relativo del file di licenza localizzato da visualizzare.  
  
## <a name="remarks"></a>Note  
 Se il `License` elemento è definito, quindi il testo del file di licenza designato viene visualizzato durante l'installazione e l'utente deve accettare la licenza per continuare.  
  
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
 [Riferimenti su VSIX Extension Schema 1.0](http://msdn.microsoft.com/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
