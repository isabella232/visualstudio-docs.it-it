---
title: Elemento VSIXLanguagePack (schema del Language Pack VSIX) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284341"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>Elemento VSIXLanguagePack (schema del Language Pack VSIX)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obbligatorio. Fornisce l'elemento radice per un Language Pack VSIX. Il Language Pack VSIX fornisce le informazioni di installazione localizzate per un pacchetto VSIX.  
  
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
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|Obbligatorio. Percorso del file che definisce lo schema per i Language Pack.|  
  
### <a name="child-elements"></a>Elementi figlio  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|[Elemento LocalizedName](../extensibility/localizedname-element-vsix-language-pack-schema.md)|Obbligatorio. Nome localizzato dell'estensione da installare.|  
|[Elemento LocalizedDescription](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|Obbligatorio. Descrizione localizzata dell'estensione da installare.|  
|[Elemento MoreInfoURL](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|facoltativo. Collegamento alle informazioni localizzate sull'estensione.|  
|[Elemento License](../extensibility/license-element-vsix-language-pack-schema.md)|facoltativo. Percorso di una versione localizzata del file di licenza per l'estensione.|  
  
### <a name="parent-elements"></a>Elementi padre  
  
|Elemento|Descrizione|  
|-------------|-----------------|  
|nessuno||  
  
## <a name="element-information"></a>Informazioni sull'elemento  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    Spazio dei nomi    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Schema Name   |                 Schema del Language Pack VSIX                 |
| File di convalida |                VSIXLanguagePackSchema. xsd                 |
|  Può essere vuoto   |                            No                             |
  
## <a name="see-also"></a>Vedere anche  
 Informazioni di [riferimento sullo schema del Language Pack di VSX](../extensibility/vsx-language-pack-schema-reference.md) [localizzazione dei pacchetti VSIX](../extensibility/localizing-vsix-packages.md) [estensione VSIX schema 1,0](/previous-versions/dd393700(v=vs.110))
